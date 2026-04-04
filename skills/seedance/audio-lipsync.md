---
module: audio-lipsync.md
when_to_use: voice, dialogue, lip sync, audio, music, sound, multilingual, narration, timbre, speech
related_modules: commercial-ads.md, one-take-storytelling.md, character-consistency.md
---

<module id="09_audio-lipsync">

<module_meta>
  <name>Audio, Voice & Lip Sync</name>
  <when_to_use>voice, dialogue, lip sync, audio, music, sound, multilingual, narration, timbre, speech</when_to_use>
  <related_modules>commercial-ads.md, one-take-storytelling.md, character-consistency.md</related_modules>
</module_meta>

<capabilities>
Seedance 2.0 sound engine can:
- Generate realistic lip-sync matched to mouth movements
- Work in multiple languages: Mandarin, English, Spanish, Korean, and more
- Create environmental sound: wind, rain, traffic based on what's on screen
- Produce sound effects matched to on-screen actions
- Generate background music following visual rhythm
- Reference voice timbre from uploaded videos (@Video1)
- Extract and reference audio from any uploaded video (no separate audio file needed)
</capabilities>

<audio_patterns>
DIRECT AUDIO:
  use @Audio1 for background music
  → plays the uploaded audio track directly

EXTRACT FROM VIDEO:
  reference @Video1's background music and sound effects
  → extracts audio from a video reference, no separate file needed

VOICE TIMBRE CLONE:
  the narrator's voice timbre references @Video1
  → clones speech character/tone from a video

AMBIENT SOUND:
  background audio: footsteps, crowd chatter, vehicle sounds
  → describes environmental sound in natural language

SOUND EFFECTS:
  sound of a chaotic crowd / engine revving / door creaking
  → describe specific SFX in the prompt

LIP SYNC:
  the character says "..." in [language]
  → model generates lip movement matching the spoken line
</audio_patterns>

<lip_sync_rules>
RULE_1: Always specify the character who is speaking (by @Image ref or description).
RULE_2: Write dialogue in the target language directly in the prompt.
RULE_3: For multi-character dialogue, clearly indicate who says what and in what order.
RULE_4: Combine character consistency keywords with dialogue to prevent face drift during speech.
RULE_5: For voiceover (off-screen narrator), specify "voiceover" or "narration" — do not describe mouth movement.
RULE_6: For timbre clone, @Video1 must contain clear speech by the target voice.
</lip_sync_rules>

<examples>

<example id="animal_dialogue_fisheye">
<task>Animal dialogue with fish-eye camera + voice reference</task>
<prompt>
Fixed camera. Central fish-eye lens view looking down through a circular opening. Reference @Video1's fish-eye lens. Make the horse from @Video2 look into the fish-eye camera. Reference @Video1's talking movements. Background music references @Video3's sound effects.
</prompt>
<settings>ratio: 1:1, duration: 6-8s</settings>
</example>

<example id="real_estate_voiceover">
<task>Documentary voiceover with timbre reference</task>
<prompt>
Based on the provided office building photos, generate a 15-second cinematic documentary in realistic style. 2.35:1 widescreen, 24fps, with delicate visuals. The narrator's voice timbre references @Video1. Capture "the ecosystem of the office building" — showing different companies operating inside, with narration explaining how the building has become a vibrant commercial ecosystem. 4K ultra-high definition, rich details, sharp resolution. Cinematic quality, natural colors, no blur, no ghosting, stable footage.
</prompt>
<settings>ratio: 21:9, duration: 15s, @ mapping: @Video1=voice timbre reference</settings>
</example>

<example id="cat_dog_roast">
<task>Multi-character comedy dialogue — two animals</task>
<prompt>
A comedy roast between a cat and a dog in a "Cat & Dog Roast Show". Fixed camera, medium shot.
Cat host (licking paw, eye-roll): "Folks, who even understands? This guy next to me does nothing all day but wag his tail, destroy the couch, and use those 'I'm so good, please pet me' eyes to scam treats from humans. You still go by 'Lucky'? I'd call you 'Wrecky'! Hahaha."
Dog host (head tilted, tail wagging): "You're one to talk! You sleep 18 hours a day, and the moment you're awake you rub against humans' legs for canned food. You shed so much the humans' black clothes are covered in your fur. And you still pretend to be royalty?"
Natural and fluid motion, smooth and stable footage. 4K ultra-high definition, no blur, no flickering, stable footage.
</prompt>
<settings>ratio: 16:9, duration: 10-12s</settings>
</example>

<example id="chinese_opera_dialogue">
<task>Period drama dialogue — Chinese opera style</task>
<prompt>
The prelude to "The Case of Chen Shimei" begins. The black-robed Judge Bao on the left points at the red-robed Chen Shimei on the right, teeth gritted, singing in traditional opera style: "The blade meets its sheath — with irrefutable evidence, do you dare deny it?" Chen Shimei's eyes dart nervously, seeking an escape, his face deeply embarrassed. Then, from off-screen, a female opera voice calls out: "Hold!" Both Bao and Chen turn to look to the right of the frame. Clear facial features, stable face, no distortion. Natural and fluid motion. 4K ultra-high definition, cinematic quality, stable footage.
</prompt>
<settings>ratio: 16:9, duration: 10s</settings>
</example>

<example id="multilingual_family">
<task>Multi-character multilingual dialogue — family celebration</task>
<prompt>
The girl in the hat center frame warmly sings "I'm so proud of my family!", then turns to hug the girl next to her. The girl responds emotionally: "My sweetie, you're the heart of our family." The boy in yellow on the left says excitedly: "Folks, let's dance together to celebrate!" The girl on the far right responds: "I'll bring the music!" Latin music kicks in. The woman in the orange dress on the left nods and smiles. People in the crowd start stomping their feet, children clap along to the beat. The whole family forms a circle, dancing joyfully on a colorful street, skirts swirling. Clear facial features, stable face, no distortion, no deformation. Normal body proportions, natural structure. Natural and fluid motion, smooth and stable footage. 4K ultra-high definition, cinematic quality, no blur, stable footage.
</prompt>
<settings>ratio: 16:9, duration: 12-15s</settings>
</example>

<example id="action_squad_spanish">
<task>Multi-character tactical dialogue in Spanish</task>
<prompt>
Fixed camera. The standing squad leader clenches his fist and commands in Spanish: "We strike in three minutes!" The knife-wielder sheathes his blade. The blond team member checks his firearm. The green-haired member grips a tactical flashlight. The dark-skinned member puts a hand on his partner's shoulder and asks in Spanish: "Flank them?" The captain nods: "Standard play — leave survivors for interrogation." Everyone goes silent, equipment clinking as they complete tactical hand signals and rise in unison. Clear facial features, stable faces, no distortion. Natural and fluid motion, no stiffness. 4K ultra-high definition, cinematic quality, dramatic lighting, stable footage.
</prompt>
<settings>ratio: 16:9, duration: 10-12s</settings>
</example>

<example id="morning_timbre_clone">
<task>Morning scene with voice timbre clone from video</task>
<prompt>
0–3s: An alarm clock rings. A blurry image of the bedroom fades in.
3–10s: Quick camera pan to the man's face in close-up. He tiredly calls the girl to wake up — his voice and timbre reference @Video1.
10–12s: The girl pouts and dives under the covers.
12–15s: Cut to full body shot of the man. He sighs and says: "I really can't do anything with you!"
Clear facial features, stable face, no distortion. Natural and fluid motion. 4K ultra-high definition, cinematic quality, no blur, no flickering, stable footage.
</prompt>
<settings>ratio: 16:9, duration: 15s, @ mapping: @Video1=voice timbre source</settings>
</example>

<example id="science_narrated_animation">
<task>Educational narration + animated storyboard</task>
<prompt>
In a science-documentary style and tone, animate the content from @Image1. The story covers: Wukong needs the Banana Leaf Fan to cross Flaming Mountain, so he goes to Princess Iron Fan at Emerald Cloud Mountain to borrow it. But she refuses — her son Red Boy was subdued by Wukong and made a disciple of Guanyin, separating mother and child. She won't lend the fan and even tries to take revenge. Wukong's polite request fails, and a confrontation erupts. Documentary narration voiceover throughout. Natural and fluid motion, smooth and stable footage. 4K ultra-high definition, cinematic quality, stable footage.
</prompt>
<settings>ratio: 16:9, duration: 12-15s, @ mapping: @Image1=storyboard/scene reference</settings>
</example>

</examples>

<common_mistakes>
MISTAKE: Writing dialogue without specifying the speaker → model creates random lip movement
FIX: Always name or reference the character before their line: "The man from @Image1 says: '...'"

MISTAKE: Expecting generated audio to match a specific music track without uploading it
FIX: Upload the audio as @Audio1 and use: "use @Audio1 for background music"

MISTAKE: Requesting both timbre clone AND specific dialogue text in complex multi-character scenes
FIX: Use timbre clone only for single narrator/voiceover; write dialogue text directly for multi-character scenes

MISTAKE: Vague audio direction: "add some cool music"
FIX: Describe the musical character: "dramatic orchestral swell", "lo-fi ambient beats", "high-energy Latin percussion"

MISTAKE: Forgetting character consistency keywords when characters speak
FIX: Always append "Clear facial features, stable face, no distortion" even in dialogue scenes
</common_mistakes>

<community_examples>
## Community Examples — See community-examples.md

- **Wuxia "Duel on the Lake"** — per-shot audio design (guqin, bamboo flute, collision SFX, voice)
- **UGC Skincare** — natural ambient audio, dialogue with "DIALOGUE LOCK" technique
- **Mukbang Slice-of-Life** — dialect dialogue, multi-layer SFX (chopsticks, noodles, firecrackers)
- **Conductor Restores Light** — music-visual synchronization, poetic sound narrative
- **Multi-Shot Emotional Sequence** — specific SFX (rustling leaves, footsteps on moss, breathing)
- **Detailed Cinematic Scene** — multi-character dialogue with whispered/confident delivery
</community_examples>

</module>
