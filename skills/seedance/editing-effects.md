# Seedance 2.0 Module: Editing, Effects, Templates & Beat-Sync

<module_meta>
when_to_use: Editing existing videos, character swaps, element addition/removal, narrative reversal, effects transfer (particles, fish-eye, ink-wash, puzzle-shatter), template replication, beat-synced montages, visual rhythm matching
related_modules: camera-motion.md (for camera replication within effects), audio-lipsync.md (for beat-sync with audio), commercial-ads.md (for ad template recreation)
</module_meta>

<video_editing_capabilities>
## Video Editing

Targeted edits on existing videos without starting over:
- **Character swap** — replace a person while preserving all motion
- **Element addition/removal** — add or remove objects, change hairstyles, add creatures
- **Narrative reversal** — flip the entire storyline (dramatic → comedy, etc.)
- **Brand insertion** — add logos, packaging, brand elements into existing footage
- **Style override** — convert to ink-wash, anime, pixel art, etc.

<enforcement>
CRITICAL: Always clarify whether you're EDITING a video or using it as REFERENCE for something new.
- EDIT: `Replace the lead singer in @Video1 with @Image1` — modifies existing video
- REFERENCE: `Reference @Video1's style. Create a new scene with @Image1` — creates new content
These are DIFFERENT operations. Specify which.
</enforcement>
</video_editing_capabilities>

<effects_template_replication>
## Creative Template & Effects Replication

Seedance identifies action rhythm, camera language, and visual structure from references and replicates precisely.
Pattern: `Reference @Video1's [specific effect/style/rhythm]. Replace [subject] with @Image1.`

You don't need professional terminology. Write clearly: "Reference @Video1's rhythm and camera work, @Image1's character design" — and the model delivers.
</effects_template_replication>

<beat_sync>
## Beat-Synced Editing

Music video content that hits the beats. Upload a reference video with music — model matches rhythm.
Pattern: `@Image1 through @Image6 synced to @Video1's rhythm and beats. Each image transitions on the beat.`
</beat_sync>

<examples>
## Prompt Examples — Video Editing

**Character swap preserving all motion:**
"Replace the female lead singer in @Video1 with the male vocalist from @Image1. All actions should exactly replicate the original video. No cuts. Band performance music throughout."

**Simple element addition:**
"Change the woman's hairstyle in @Video1 to long red hair. The great white shark from @Image1 slowly surfaces behind her, half its head visible."

**Complete narrative reversal (dramatic → comedy):**
"Subvert @Video1's entire storyline. 0–3s: A man in a suit sits at a bar, calm, swirling his glass. Camera slowly pushes in — elegant lighting, serious atmosphere. He whispers: 'This deal... it's big.' 3–6s: The woman behind him looks tense and asks 'How big?' He looks up, lowers his voice: 'Very big.' Camera cuts to a hand close-up as he sets the glass down — full gravitas. 6–9s: Suddenly he pulls out from under the table — an absurdly oversized snack gift pack, slamming it on the table with a thud. 9–12s: The woman's hand, tensed at her waist, visibly relaxes. Her expression softens. The entire mood shifts to playful. 13–15s: The man offers her a snack. Camera pulls wide to the full bar. The image goes transparent and blurry — subtitle appears: 'No matter how busy, remember to have a snack~'"

**Commercial edit with brand insertion:**
"@Video1: Camera pans right. The fried chicken shop owner busily hands fried chicken to queuing customers, saying in Mandarin: 'After his order, yours — everyone please line up.' He then grabs a paper bag printed with @Image1's design. Close-up of the branded bag. Close-up of the hand-off to the customer."

## Prompt Examples — Effects & Template Replication

**VR/Sci-fi scene transitions with template video:**
"Replace @Video1's subject with @Image1. @Image1 as the first frame. The character puts on a virtual sci-fi headset. Reference @Video1's camera work. From third-person view to the character's subjective POV. Through the AI headset, arrive at @Image2's deep blue universe. Several spaceships appear, flying into the distance. Camera follows the ships, transitioning to @Image3's pixel world. Camera flies low over pixel mountains with trees growing in stylized formations. Then the view tilts up, accelerating through to @Image4's green-textured planet, camera gliding over the planet's surface."

**Fashion montage with fish-eye effect:**
"Reference the first image for the model's facial features. The model wears outfits from images 2–6, approaching the camera with playful, cool, cute, surprised, and suave poses respectively. Each outfit change triggers a cut. Reference the video's fish-eye lens effect and ghosting/flickering visual effects."

**Advertisement recreation:**
"Reference the video's ad concept. Using the provided down jacket image, reference the goose feather image and swan image. Pair with this ad copy: 'This is goose down. This is a warm swan. This is a wearable arctic swan-down jacket. Dress warm for the new year, live warm every day.' Generate a new down jacket advertisement."
→ cross-ref: see commercial-ads.md for full ad workflow

**Ink-wash style with effects transfer:**
"Black-and-white ink-wash style. The character from @Image1 references @Video1's effects and movements — performing an ink-wash tai chi martial arts sequence."

**Particle and texture effects transfer:**
"Starting from black. Reference @Video1's particle effects and materials. Gold-gilded sand drifts in from the left side of the frame, covering rightward. Reference @Video1's particle dispersion effect. The text from @Image1 gradually appears at the center of the frame."

**Character effects mashup:**
"The character from @Image1 references @Video1's actions and expression changes — demonstrating the absurd act of eating instant noodles."

**Puzzle-shatter transition recreation:**
"Starting from @Image1's ceiling. Reference @Video1's puzzle-shattering effect for the transition. Replace the 'BELIEVE' text with 'Seedance.' Reference @Image2's font style."

## Prompt Examples — Beat-Sync

**Fashion beat-sync:**
"The girl in the poster keeps changing outfits. Clothing styles reference @Image1 and @Image2. She holds the bag from @Image3. Video rhythm and beat references @Video1."

**Multi-image rhythm montage:**
"@Image1 through @Image7: the characters sync to @Video1's keyframe positions and overall rhythm. Characters should be more dynamic. The overall visual style is more dreamlike with strong visual tension. Adjust framing of reference images as needed for the music and scene requirements. Add lighting variations to complement the visuals."

**Landscape rhythm montage:**
"@Image1 through @Image6 scenic landscape images. Reference @Video1's visual rhythm. Transitions between scenes should match the style and musical beat for perfect sync."

**Anime combat with precise timing:**
"8-second intense strategic battle anime clip with a revenge theme. 0–3s: The female lead from storyboard 1 turns and sits. Cut — she places a chess piece, saying 'You lose.' Reference storyboard 2. 3–4s: Quick pan to the opposing man's face close-up (storyboard 3). He grits his teeth, furious at the result. 4–6s: Cut to overhead shot. She plays a piece — onlookers gasp in amazement (storyboard 4). 6–8s: Camera whips down. Screen goes black, then fades in — dim interior — she gazes out the window at the moonlight and quietly says 'We'll see about that' (storyboard 5)."
</examples>

<video_remix_workflows>
## Tested Video Remix Workflows

1. **Fashion runway swap** — runway video + clothing image → "Replace the clothing of the model in @Video1 with the clothing in @Image1"
2. **Element addition/removal** — video → "Add a glowing neon sign in the background" or "Remove the car from the scene"
3. **Character replacement** — video + character image → "Replace the lead in @Video1 with @Image1, replicate all original actions"
4. **Video continuation** — video → "Extend @Video1 by 10 seconds with a dramatic reveal"
5. **Narrative reversal** — video → "Subvert @Video1's storyline — turn the dramatic scene into a comedy"
6. **Style transfer** — video + style reference → "Recreate @Video1 in black-and-white ink-wash style"
7. **Commercial recreation** — trending ad + product images → "Reference @Video1's ad concept and rhythm. Replace the product with @Image1"
8. **Multi-character swap** — fight video + 2 character images → "Replace the 2 characters in @Video1 with @Image1 and @Image2"
9. **Music video from stills** — photos + music video → "Sync @Image1 through @Image6 to @Video1's rhythm and beats"
</video_remix_workflows>

<common_mistakes>
## Common Mistakes — AVOID

- Not specifying "replicate all original actions" when doing character swaps — motion can drift
- Writing beat-sync prompts without a reference video that has the actual music
- Confusing EDIT vs. REFERENCE — these are different operations, specify which
- Not breaking long beat-sync sequences into timed segments
- Forgetting to specify the exact effect to replicate: "fish-eye," "particle dispersion," "puzzle-shatter" — be specific
</common_mistakes>

<community_examples>
## Community Examples — See community-examples.md

- **1970s Robot Combat** — complete style spec (35mm film stock, color grading, film grain +25%), physics rules
- **Scenery Switching (coordinates)** — ultra-high-speed 0.1s montage, 100 locations, "each cut must be video"
- **Character Transformation** — fish-eye, ghosting, flickering effects referenced from video
- **Warrior Transformation** — emotional arc with camera transitions (static → zoom → cut → low-angle)
</community_examples>
