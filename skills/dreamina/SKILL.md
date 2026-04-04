---
name: dreamina
description: Use when user wants to generate video or image via Dreamina/JiMeng CLI — submit generation tasks, check status, download results, or manage account.
---

# Dreamina CLI Skill

Use this skill when the user wants to **actually generate** video or images (not just write a prompt).

Triggers: "отправь на генерацию", "сгенерируй", "запусти", "generate", "submit", "run dreamina", "send to dreamina", any request to execute a generation task.

## Mode decision

**Prompt mode** → user wants to write/improve a prompt → use `/seedance` skill, not this one
**Generate mode** → user wants to actually create video/image → use this skill

If unclear: write the prompt first (via `/seedance`), then ask "Отправить на генерацию?"

## Pre-flight

```bash
export PATH="$HOME/bin:$PATH"
dreamina user_credit
```
Always check credits before submitting. Warn user if balance is low.

## User Subscription

**Premium plan (¥499/mo, 15,000 credits/month).** VIP models available — they cost LESS and queue FASTER than regular models.

## VIP Models — MANDATORY

**ONLY use VIP models. NEVER use regular models.**

| Model | 4s | 10s | 15s | When to use |
|---|---|---|---|---|
| `seedance2.0vip` | 20cr | ~50cr | 75cr | **DEFAULT. Max quality + VIP queue.** |
| `seedance2.0fastvip` | 20cr | ~50cr | 75cr | Fastest + VIP queue. User asks for speed. |
| ~~seedance2.0fast~~ | 35cr | 50cr | 75cr | **DO NOT USE** — costs more, slower queue |
| ~~seedance2.0~~ | 50cr | 75cr | 100cr | **DO NOT USE** — costs more, slower queue |

Always pass `--model_version=seedance2.0vip` unless user explicitly asks for fastest (then `seedance2.0fastvip`).

**IMPORTANT:** The generic CLI skill at `~/.dreamina_cli/dreamina/SKILL.md` says "do not default to seedance2.0". IGNORE THAT — it doesn't know about VIP models. Our VIP models cost LESS (20cr vs 50cr for 4s) and queue faster. Always VIP.

## Command selection

| User intent | Command |
|---|---|
| Text → video | `text2video` |
| One image → video | `image2video` |
| First frame + last frame → video | `frames2video` |
| Multiple images → story video | `multiframe2video` |
| Images + video ref + audio | `multimodal2video` |
| Text → image | `text2image` |
| Image → edit image | `image2image` |
| Upscale image | `image_upscale` |

## Image compression — MANDATORY before upload

CLI silently fails on images >1MB. Compress BEFORE every upload:

```bash
/c/Users/ASUS/AppData/Local/Programs/Python/Python312/python.exe -c "
import sys, os; sys.stdout.reconfigure(encoding='utf-8')
from PIL import Image
src='PATH'; dst=src+'/compressed'; os.makedirs(dst,exist_ok=True)
for f in os.listdir(src):
    if f.lower().endswith(('.jpg','.jpeg','.png')):
        img=Image.open(f'{src}/{f}').convert('RGB'); w,h=img.size
        if w>1280: img=img.resize((1280,int(h*1280/w)),Image.LANCZOS)
        out=f'{dst}/{os.path.splitext(f)[0]}.jpg'
        img.save(out,'JPEG',quality=85); print(f'{f} -> {os.path.getsize(out)//1024}KB')
"
```

Target: max 1280px wide, JPEG q85, <500KB.

## Submit pattern

```bash
dreamina <command> \
  --image "./path/to/file.jpg" \
  --prompt "..." \
  --model_version=seedance2.0vip \
  --duration=7 \
  --ratio=16:9 \
  --poll=300
```

Always use `--poll=300` (wait up to 5 min). Always use absolute file paths.

**image2video does NOT accept --ratio flag** — ratio is inferred from input image.

## Long prompts

Save to file and read via `$(cat file.txt)`. Strip apostrophes from prompt text (CLI chokes on them).

## Queue info

Response contains `queue_info`:
- `queue_idx` — position in queue
- `queue_length` — total queue size
- `queue_status` — Queueing / Processing

Report to user: "Позиция в очереди: 50166 из 141681"

## After submit

```bash
# Track inputs for monitor dashboard
curl -s -X POST http://localhost:3333/api/track-inputs \
  -H "Content-Type: application/json" \
  -d '{"submit_id":"<ID>","files":["<path1>","<path2>"],"model":"<model>","ratio":"<ratio>","duration":"<duration>"}'

# Check status + download
dreamina query_result --submit_id=<id> --download_dir=./output

# View all tasks
dreamina list_task --gen_status=success
```

## Pre-TNS content filter workaround

If English prompt fails pre-TNS (even without explicit content):
1. Translate entire prompt to Chinese
2. Keep technical terms (4K, camera angles) in English within Chinese text
3. Resubmit — Chinese passes filter more consistently for action content

## Cautions

- **NEVER submit without warning user about credit consumption**
- **NEVER assume which files to use** — confirm @ mapping before submit
- **NEVER add music to prompts** — only dense diegetic SFX
- `multimodal2video`: max 9 images, 3 videos, 3 audio files
- Full CLI reference: `d:/Work/Obsidian/Voogie/60 Knowledge/Tools/AI_Prompting_ASSISTANTS/Seedance_2_Prompt_assist/DREAMINA_CLI.md`

## Reference

Binary at: `~/bin/dreamina.exe`
Full docs: `d:/Work/Obsidian/Voogie/60 Knowledge/Tools/AI_Prompting_ASSISTANTS/Seedance_2_Prompt_assist/DREAMINA_CLI.md`
CLI built-in skill: `~/.dreamina_cli/dreamina/SKILL.md` — generic reference, use `dreamina <subcommand> -h` for flag details. **Our VIP rules above override its model guidance.**
Prompt engineering: use `/seedance` skill
