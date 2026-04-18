# Dreamina CLI — Полное руководство

> Официальный CLI от JiMeng (即梦) / ByteDance для генерации видео и изображений через терминал или AI-агент.
> Версия билда: `65dc0e0` / релиз `1.4.1` (2026-04-17)
>
> **Источник истины по флагам и моделям:** [docs/DREAMINA_CLI_HELP.md](docs/DREAMINA_CLI_HELP.md) — сырой дамп `dreamina <cmd> --help`. Если что-то в этом руководстве расходится с help-дампом — верить help-дампу.
>
> **Что нового в 1.4.1 vs 1.3.3 (5a448f5):**
> - Рефакторинг логина для повышенной безопасности (release notes)
> - Новый флаг `--session int` (default 0 "默认对话") на всех задачах: `text2video`, `image2video`, `frames2video`, `multimodal2video`, `multiframe2video`, `text2image`, `image2image`, `image_upscale`
> - `image2video`: добавлены алиасы моделей с подчёркиванием — `3.0_fast`, `3.0_pro`, `3.5_pro`
> - `image_upscale`: `8k` теперь явно в help (`supported values: 2k, 4k, 8k`)
> - `text2image`: модель `lab` (VIP) больше не указана в `--help` — считать её недокументированной
> - `image2image`: только модели `4.0, 4.1, 4.5, 4.6, 5.0` (версии 3.x не поддерживаются)
>
> **Seedance 1080p статус (обновлено 2026-04-18):** 🎉 **1080p для Seedance 2.0 VIP РАБОТАЕТ через CLI**, несмотря на то что `dreamina <cmd> -h` всё ещё показывает только `720p`. Доку CLI не обновили. Подтверждено вживую: `multimodal2video --model_version=seedance2.0_vip --video_resolution=1080p` возвращает реальное видео 1920×1080. Сервер маршрутизирует на отдельный pipeline **Pro Vision** (`DreaminaFusion:Video40_Pro_Vision_unified_edit_1080p`). См. раздел [1080p для Seedance VIP](#1080p-для-seedance-vip-verified-2026-04-18) ниже.

> **Resolution-matching rule (обязательное правило):** когда user просит генерацию в 1080p / Full HD — ресайзим input картинку в **1920×1080**, q92, <1MB. Когда 720p / HD — ресайзим в **1280×720**, q85, <500KB. Пути без пробелов (копия в `.ai/temp/`). Сервер апскейлит сам, но матч input→output даёт чище результат.

---

## Установка и авторизация

```bash
# Установка (одна команда)
curl -s https://jimeng.jianying.com/cli | bash

# Войти в аккаунт (откроет браузер)
dreamina login

# Войти без браузера (для агентов/серверов)
dreamina login --headless

# Проверить баланс кредитов
dreamina user_credit

# Выйти из аккаунта
dreamina logout

# Перелогиниться (сброс + новый вход)
dreamina relogin
```

После установки **перезапусти терминал** — путь `~/bin` добавляется в PATH автоматически.

---

## Как работают задачи

Все генерации **асинхронные**: ты отправляешь задачу → получаешь `submit_id` → потом запрашиваешь результат.

### Статусы задачи
| Статус | Значение |
|---|---|
| `querying` | Задача в очереди / выполняется |
| `success` | Готово, есть ссылка на файл |
| `fail` | Ошибка, смотри `fail_reason` |

> **Недокументированно:** при статусе `querying` ответ содержит `queue_info` с позицией в очереди:
> ```json
> "queue_info": {
>   "queue_idx": 50166,       // твоя позиция
>   "queue_length": 141681,   // всего в очереди
>   "queue_status": "Queueing" // Queueing / Processing
> }
> ```
> Это не указано в `--help` — узнали из живого ответа.

### Флаг `--poll` — ждать результат прямо в терминале

```bash
# Ждать до 120 секунд, опрашивая каждую секунду
dreamina text2video --prompt="..." --poll=120
```

Без `--poll` — сразу возвращает `submit_id`, дальше запрашиваешь сам.

### Запросить статус задачи

```bash
dreamina query_result --submit_id=3f6eb41f425d23a3

# Скачать результат сразу в папку
dreamina query_result --submit_id=3f6eb41f425d23a3 --download_dir=./output
```

### Посмотреть историю задач

```bash
# Последние 20 задач
dreamina list_task

# Только успешные
dreamina list_task --gen_status=success

# Только видео
dreamina list_task --gen_task_type=video

# Пагинация (следующие 20)
dreamina list_task --limit=20 --offset=20

# Найти конкретную задачу
dreamina list_task --submit_id=3f6eb41f425d23a3
```

---

## Генерация видео

### 1. Текст → Видео (`text2video`)

Самый простой способ. Seedance 2.0 / fast.

```bash
# Базовый запрос
dreamina text2video --prompt="a cat walking in rain, cinematic"

# Полный контроль
dreamina text2video \
  --prompt="neon city at night, slow camera pan" \
  --model_version=seedance2.0 \
  --duration=10 \
  --ratio=16:9 \
  --video_resolution=720p \
  --poll=180
```

**Модели:**
- `seedance2.0_vip` — макс. качество + VIP-очередь (VIP only)
- `seedance2.0fast_vip` — быстрейший + VIP-очередь (VIP only)
- `seedance2.0` — максимальное качество
- `seedance2.0fast` — быстрее, дешевле (дефолт)

> VIP-модели явно в `--help` с CLI `5a448f5` (2026-04-07). Правильные имена: `seedance2.0_vip` и `seedance2.0fast_vip` (с подчёркиванием перед `vip`). Старые имена `seedance2.0vip` / `seedance2.0fastvip` (без подчёркивания) — **неправильные**: CLI принимал без ошибки, но API игнорировал и ставил в стандартную очередь. Нужен VIP-аккаунт.

**Параметры:** длительность 4–15с, соотношения: `1:1`, `3:4`, `4:3`, `9:16`, `16:9`, `21:9`, разрешение `720p` (1080p для Seedance **не в CLI 1.4.1**)

**Новое в 1.4.1:** флаг `--session int` (default 0 "默认对话") — привязать задачу к конкретной сессии/диалогу Dreamina.

---

### 2. Картинка → Видео (`image2video`)

Анимирует одно изображение.

```bash
dreamina image2video \
  --image=./photo.png \
  --prompt="camera slowly zooms in, wind moves the hair" \
  --model_version=seedance2.0 \
  --duration=6 \
  --poll=180
```

**Доступные модели:** `3.0`, `3.0fast`, `3.0pro`, `3.0_fast`, `3.0_pro`, `3.5pro`, `3.5_pro`, `seedance2.0`, `seedance2.0fast`, `seedance2.0_vip`, `seedance2.0fast_vip`

**Разрешение по моделям:**
- `3.0` / `3.0fast` / `3.5pro` → `720p` или `1080p`
- `3.0pro` → `1080p` (только)
- `seedance2.0` family → `720p` **или `1080p`** (1080p не в help, но работает через `multimodal2video` — см. раздел «1080p для Seedance VIP»)

**Длительность по моделям:** 3.0/3.0fast/3.0pro → 3–10с, 3.5pro → 4–12с, seedance2.0 family → 4–15с.

> Соотношение сторон берётся автоматически из картинки.

---

### 3. Первый + Последний кадр → Видео (`frames2video`)

Задаёшь начало и конец — модель строит переход сама.

```bash
dreamina frames2video \
  --first=./start.png \
  --last=./end.png \
  --prompt="season changes from summer to winter" \
  --model_version=seedance2.0 \
  --duration=8 \
  --poll=180
```

**Модели:** `3.0`, `3.5pro`, `seedance2.0`, `seedance2.0fast`, `seedance2.0_vip`, `seedance2.0fast_vip`

**Разрешение:** `3.0`/`3.5pro` → `720p` или `1080p`; seedance2.0 family → `720p` (для 1080p на seedance2.0 VIP используй `multimodal2video`, см. раздел «1080p для Seedance VIP»).
**Длительность:** `3.0` → 3–10с, `3.5pro` → 4–12с, seedance2.0 family → 4–15с.

---

### 4. Несколько картинок → Связная история (`multiframe2video`)

От 2 до 20 изображений. Модель сама строит связный нарратив.

```bash
# 2 картинки (простой вариант)
dreamina multiframe2video \
  --images ./frame1.png,./frame2.png \
  --prompt="character turns around slowly" \
  --duration=4

# 3+ картинки (с описанием каждого перехода)
dreamina multiframe2video \
  --images ./a.png,./b.png,./c.png \
  --transition-prompt="walks from forest to city" \
  --transition-prompt="enters the building" \
  --transition-duration="4" \
  --transition-duration="3"
```

> Для N картинок нужно N-1 промптов переходов. Каждый сегмент: 0.5–8 сек, общая длина ≥ 2 сек.

---

### 5. Мультимодальное видео — флагман (`multimodal2video`)

Самый мощный режим. Принимает картинки + видео + аудио одновременно.

```bash
# Картинка + музыка
dreamina multimodal2video \
  --image ./scene.png \
  --audio ./music.mp3 \
  --prompt="cinematic reveal, slow motion" \
  --model_version=seedance2.0 \
  --duration=10 \
  --ratio=16:9 \
  --poll=180

# Картинка + видео-референс + музыка
dreamina multimodal2video \
  --image ./character.png \
  --image ./background.png \
  --video ./style_ref.mp4 \
  --audio ./soundtrack.mp3 \
  --prompt="merge the character into the background scene" \
  --model_version=seedance2.0fast \
  --duration=8
```

**Лимиты:** до 9 картинок, до 3 видео, до 3 аудио (каждое 2–15 сек), длительность 4–15с.

**Разрешение:** `720p` (дефолт по help) **или `1080p`** (не в help, но работает — см. ниже).

---

### 1080p для Seedance VIP (verified 2026-04-18)

CLI help говорит: `--video_resolution` для seedance2.0 family поддерживает только `720p`. **Это устаревшая информация.** Проверено вживую:

| Что | Значение |
|---|---|
| Команда | `multimodal2video --model_version=seedance2.0_vip --video_resolution=1080p` |
| Результат | ✅ `gen_status: success`, реальное видео **1920×1080** mp4 |
| Серверный endpoint | `DreaminaFusion:Video40_Pro_Vision_unified_edit_1080p` |
| Очередь | `dreamina_fusion_video40_pro_vision` (отдельная Pro-очередь) |

**Цены (multimodal, 5 сек):**

| Модель + разрешение | Кредиты |
|---|---|
| `seedance2.0fast_vip` 720p | 55cr |
| `seedance2.0_vip` 720p | ~70cr |
| **`seedance2.0_vip` 1080p** | **165cr** (×2.36 от 720p standard, ×3 от 720p fast) |

**Resolution-matching rule (обязательно):**
- User просит **1080p / Full HD** → ресайз input в **1920×1080**, q92, <1MB
- User просит **720p / HD** (дефолт) → ресайз в **1280×720**, q85, <500KB
- Пути без пробелов (копия в `.ai/temp/`) — иначе upload silently fails server-side с частичным списанием
- Сервер апскейлит input сам, но matching даёт чище результат

**⚠️ Перед submit в 1080p — предупреждать user о цене (×3 от привычной 720p fast).**

---

## Генерация изображений

### Текст → Изображение (`text2image`)

```bash
dreamina text2image \
  --prompt="portrait of a samurai in rain, dramatic lighting, 8k" \
  --model_version=5.0 \
  --ratio=3:4 \
  --resolution_type=4k \
  --poll=60
```

**Модели и разрешения (из `--help` CLI 1.4.1):**
| Модель | Разрешения |
|---|---|
| `3.0`, `3.1` | `1k` или `2k` |
| `4.0`, `4.1`, `4.5`, `4.6`, `5.0` | `2k` или `4k` |

> Модель `lab` (VIP) в старой документации — больше **не указана в `--help`**. Считать недокументированной. Проверять наличие перед использованием.

**Соотношения:** `21:9`, `16:9`, `3:2`, `4:3`, `1:1`, `3:4`, `2:3`, `9:16`

---

### Изображение → Изображение (`image2image`)

Редактирование/трансформация по промпту.

```bash
dreamina image2image \
  --images ./input.png \
  --prompt="turn into oil painting style, warm colors" \
  --model_version=5.0 \
  --resolution_type=4k \
  --poll=60

# Несколько входных картинок (до 10)
dreamina image2image \
  --images ./face.png,./style.png \
  --prompt="apply the art style to the face"
```

**Модели (CLI 1.4.1):** только `4.0`, `4.1`, `4.5`, `4.6`, `5.0` (версии 3.x не поддерживаются).
**Разрешение:** `2k` или `4k` (1k **не работает** для `image2image`).
**Лимит:** до 10 картинок за раз.

---

### Апскейл изображения (`image_upscale`)

```bash
# До 4K (VIP)
dreamina image_upscale --image=./photo.jpg --resolution_type=4k

# До 8K (VIP)
dreamina image_upscale --image=./photo.jpg --resolution_type=8k --poll=120
```

**Варианты и цены (CLI 1.4.1 help + live API 2026-04-07):**
| Резолюция | Кредиты | Доступ |
|---|---|---|
| `2k` | 1 | Все пользователи |
| `4k` | 2 | VIP |
| `8k` | ? | VIP (не тестировали) — теперь явно в `--help` |

> **Известный баг CLI (2026-04-07):** `query_result` для задач `image_upscale` навсегда возвращает `querying`, даже когда результат готов на сайте jimeng.jianying.com. Причина: CLI полит по `submit_id`, а API апскейлинга индексирует результат по `history_record_id`. Загрузить через `--download_dir` невозможно. Скачивать вручную с сайта.

---

## Фишки и рабочий процесс

### Скачать результат сразу после готовности

```bash
dreamina text2video --prompt="..." --poll=300 && \
dreamina query_result --submit_id=<id> --download_dir=./output
```

### Пакетная проверка всех задач в очереди

```bash
dreamina list_task --gen_status=querying
```

### Быстрый тест без траты кредитов

Сначала проверь параметры через `--help`:
```bash
dreamina text2video -h
dreamina multimodal2video -h
```

### Если вернулось `AigcComplianceConfirmationRequired`

Зайди на сайт Dreamina Web, подтверди разрешение на использование модели, затем повтори команду.

### Экономия кредитов

- `seedance2.0fast` дешевле и быстрее — используй для тестов
- `seedance2.0` — только для финального рендера
- Короткие видео (4–5 сек) стоят меньше

---

## Таблица всех команд

| Команда | Вход | Выход | Seedance 2.0 |
|---|---|---|---|
| `text2video` | промпт | видео | ✅ |
| `image2video` | 1 картинка + промпт | видео | ✅ |
| `frames2video` | 2 кадра (старт+финал) | видео | ✅ |
| `multiframe2video` | 2–20 картинок | видео-история | ❌ |
| `multimodal2video` | картинки + видео + аудио | видео | ✅ |
| `text2image` | промпт | изображение | — |
| `image2image` | картинки + промпт | изображение | — |
| `image_upscale` | картинка | картинка HD | — |
| `query_result` | submit_id | статус + файл | — |
| `list_task` | фильтры | история задач | — |
| `user_credit` | — | баланс кредитов | — |

---

## Известные ограничения и подводные камни (из практики)

### Лимит на размер файла при аплоаде

CLI фейлит загрузку файлов >1–2MB с ошибкой:
```
upload image: upload phase, no file upload, please check log for more details
```

**Решение:** сжимать изображения перед отправкой. Целевой размер по **Resolution-matching rule**:
- 720p output → 1280×720, q85, <500KB
- 1080p output → 1920×1080, q92, <1MB

Пути без пробелов — иначе upload фейлится с частичным списанием на сервере.

```python
from PIL import Image
img = Image.open("input.png")
if img.mode == "RGBA": img = img.convert("RGB")
img = img.resize((1280, int(1280 * img.height / img.width)), Image.LANCZOS)
img.save("output.jpg", "JPEG", quality=85)
```

### pre-TNS контент-фильтр

Ошибка `generation failed: pre-TNS check did not pass` — контент-фильтр Dreamina отклонил задачу. Кредиты при этом списываются.

**Что триггерит:**
- Изображения с обнажённым/полуобнажённым торсом (даже CGI/3D модели)
- Описания фокуса на теле: "muscular frame", "body tracking shot", камера по телу снизу вверх
- Нестандартный цвет кожи + минимум одежды на изображении (синяя/зелёная кожа фэнтези-персонажей)
- Некоторые character sheet / model sheet с полным видом тела

**Как обойти:**
- Убрать из промпта акцент на теле — фокус на лицо, действие, окружение
- Добавить одежду/доспехи в описание: "wearing fur armor and leather bracers"
- Камеру направлять на лицо, а не на тело: "camera pushes in to face close-up"
- Если фейлится изображение — использовать кроп (только лицо/плечи) или другой ракурс
- Проверять: если одно изображение персонажа фейлится на TNS, другое может пройти

**Важно:** фильтр проверяет и изображение, и промпт. Даже идеальный промпт не спасёт, если само изображение триггерит.

### Задачи-призраки ("no history found")

Некоторые submit_id возвращают `no history found` при query_result. Причины:
- Задача не прошла сабмит (upload failed, но submit_id уже выдан)
- API потерял задачу при высокой нагрузке
- Таймаут на стороне сервера при загрузке файла

В list_task такие задачи показываются как `querying`, но на сервере их нет. Проверяй через логи: `~/.dreamina_cli/logs/YYYY-MM-DD/*.log`

### Скорость очереди

Средняя скорость обработки (на апрель 2026): ~500–900 позиций/мин.
При очереди ~160k задач:
- Позиция 20k → ~30–40 мин
- Позиция 40k → ~1 час  
- Позиция 60k → ~1.5–2 часа

Multimodal2video задачи обрабатываются медленнее, чем image2video.

### `image2video` не принимает `--ratio`

Соотношение сторон берётся автоматически из входного изображения. Флаг `--ratio` вызовет `unknown flag` ошибку. Если нужен конкретный ratio — ресайзни картинку заранее.

---

## Быстрый старт за 3 команды

```bash
# 1. Проверить баланс
dreamina user_credit

# 2. Отправить задачу и подождать
dreamina text2video --prompt="golden hour landscape, cinematic drone shot" --model_version=seedance2.0fast --duration=5 --ratio=16:9 --poll=180

# 3. Скачать результат (если не скачалось автоматически)
dreamina query_result --submit_id=<твой_id> --download_dir=./output
```
