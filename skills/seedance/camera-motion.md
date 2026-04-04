# Seedance 2.0 Module: Camera & Motion Replication

<module_meta>
when_to_use: Camera angles, dolly/tracking/crane shots, motion replication from reference videos, choreography transfer, cinematic camera techniques
related_modules: character-consistency.md (for multi-character fight scenes), commercial-ads.md (for product showcases with camera), editing-effects.md (for rhythm replication)
</module_meta>

<capabilities>
Seedance 2.0 extracts and replicates from reference videos:
- **Choreography** — fight scenes, dance moves, action sequences
- **Camera techniques** — dolly, tracking, crane, handheld, Hitchcock zoom, orbit shots, mechanical arm tracking
- **Editing rhythm** — cut timing, transitions, pacing
- **Specific moves** — whip pans, orbit shots, fish-eye lens, POV shifts
</capabilities>

<how_to_reference>
MUST be explicit about WHAT to extract from each reference:
- `reference @Video1's camera movements` — camera work only
- `reference @Video1's fighting choreography` — motion/action only
- `reference @Video1's rhythm and transitions` — editing pace only
- `fully replicate @Video1's camera work and the protagonist's facial expressions` — camera + performance
- `reference @Video1's mechanical-arm multi-angle tracking` — specific technique
- `reference @Video1's rapid left-right orbital camera work` — specific movement pattern
</how_to_reference>

<camera_language_keywords>
## Camera Language Reference

**Shot types:** close-up, medium shot, wide shot, extreme close-up, full body shot, over-the-shoulder, overhead/aerial, POV/subjective, fish-eye

**Camera movements:** slow push-in, gentle pull-out, steady pan, half-orbit, full orbit, tracking shot (front/side/behind), dolly shot, crane shot, tilt up/down, whip pan, Hitchcock zoom, mechanical arm tracking

**Stabilization:** fixed shot, handheld-stable, no shake, silky smooth, no jitter

**Compositing example:** "medium shot, slow push-in, steady follow-cam, silky smooth with no jitter"
</camera_language_keywords>

<examples>
## Prompt Examples

**Hitchcock zoom + mechanical arm tracking:**
"Reference @Image1 for the man's appearance. He's in @Image2's elevator. Fully replicate @Video1's camera movements and the protagonist's facial expressions. Hitchcock zoom when startled, then several orbit shots showcasing the elevator interior. Elevator doors open — tracking shot follows him out. The exterior scene references @Image3. The man looks around. Reference @Video1's mechanical-arm multi-angle tracking following the character's line of sight."

**Complex chase with multiple camera techniques:**
"Reference @Image1 for the man's appearance. He's in @Image2's corridor. Fully replicate @Video1's camera work and the protagonist's facial expressions. Camera follows the protagonist sprinting around a corner in @Image2, then in @Image3's long hallway — camera tracks from behind, low angle, orbiting around to the front. Camera pans right 90° to capture @Image4's forked intersection, hard stop, then pans 180° for a close-up of the protagonist's face: gasping for breath. Camera follows the protagonist's POV looking around — reference @Video1's rapid left-right orbital camera work to showcase the scene. Pull back to @Image5's setting, continue side-angle tracking of the protagonist running."

**Product showcase with cinematic camera:**
"The tablet from @Image1 as the main subject. Camera work references @Video1 — push in to a screen close-up, camera rotates as the tablet flips to reveal its full form. Data streams on screen constantly change. The surrounding environment gradually transforms into a sci-fi data space."

**Dance with synchronized camera rhythm:**
"The female star from @Image1 as the main subject. Reference @Video1's camera techniques for rhythmic push-pull-pan movements. The star's movements also reference the dance choreography from @Video1's dancer — performing energetically on stage."

**Multi-character fight choreography:**
"Reference @Image1 and @Image2 for the spear-wielding character. @Image3 and @Image4 for the dual-blade character. Replicate @Video1's choreography. They fight in @Image5's maple leaf forest."
→ cross-ref: see character-consistency.md for multi-character management

**Fight scene with environment and camera fusion:**
"Reference @Video1 for character actions. Reference @Video2 for orbiting camera language. Generate a fight scene between Character 1 and Character 2. The fight takes place under a starry sky. White dust rises during combat. The fighting is spectacular, the atmosphere intensely tense."

**Commercial car showcase:**
"Reference @Video1's camera work, frame transitions, and rhythm. Replicate using the red supercar from @Image1."
→ cross-ref: see commercial-ads.md for full ad workflow
</examples>

<common_mistakes>
## Common Mistakes — AVOID

- Saying "cinematic camera" without specifying actual movements — be precise about push-in, orbit, tracking, etc.
- Forgetting to specify low/high angle — it changes the entire feel
- Mixing motion reference and camera reference from the same video without clarifying which is which
- Not specifying camera transitions between scenes in multi-shot prompts
- Using only one angle for a character in fight scenes — provide front + side images for each character
</common_mistakes>

<community_examples>
## Community Examples — See community-examples.md

- **Wuxia "Duel on the Lake"** — 2-segment fight with per-shot camera design (medium, close-up, long shot, extreme long shot)
- **White Suit vs Cat** — orbit shots, bullet time 0.25x-0.3x, multi-shot rhythm with time segments
- **Tiger Chase** — 15s continuous POV shot (camera gripping tiger's tail), motion parallax, biomechanics
- **Speeder Chase** — single continuous shot, dynamic lock-on tracking, slingshot camera, environment reveal
- **1970s Robot Combat** — handheld cam, low angle, extreme slow-mo 0.25x, side wide shot
- **Surreal Megacity** — aerial tracking shot, rotating camera, dreamlike gravity-defying environment
- **Emotional Chinese Dance** — multiple angles (below, above, pull-in, pull-back), environmental particles
- **Multi-Shot Emotional Sequence** — static → close-up → wide → medium two-shot progression
- **Cinematic Dance Video** — fixed camera (Lock-off), 50mm f/2.8, side lighting technique
</community_examples>
