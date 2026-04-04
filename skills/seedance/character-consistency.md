# Seedance 2.0 Module: Character Consistency & Style Transfer

<module_meta>
when_to_use: Face lock, multi-character scenes, style transfer, clothing consistency, product detail preservation, multi-scene character persistence
related_modules: camera-motion.md (for multi-character fight choreography), commercial-ads.md (for brand/product consistency), one-take-storytelling.md (for character across scene changes)
</module_meta>

<what_stays_consistent>
Seedance 2.0 locks across entire generation:
- **Face identity** — no morphing mid-clip
- **Clothing and accessories** — stable throughout
- **Product details** — logos, text, fine elements preserved
- **Visual style** — no random drift mid-clip
- **Environment** — consistent across shots
</what_stays_consistent>

<mandatory_keywords>
## Constraint Keywords — ALWAYS Include in Character Prompts

- "Clear facial features, stable face, no distortion, no deformation"
- "Normal body proportions, natural structure, no stiffness"
- "Same character, consistent clothing, unchanged hairstyle"

MUST include these. Face WILL morph without explicit constraints.
</mandatory_keywords>

<key_techniques>
## Techniques

**Character from image + action from video (core pattern):**
`@Image1 performs the dance from @Video1`

**Multi-character — assign each explicitly:**
- `@Image1 and @Image2 for Character A` (front + side = much better consistency)
- `@Image3 and @Image4 for Character B`
- Multiple angles of same character improve consistency significantly

**Style transfer while preserving character:**
`Replace the girl in @Video1 with [new character]. Reference @Video1's camera work and transitions.`

**First-frame lock:**
`@Image1 as the first frame` — locks composition and character appearance from start
</key_techniques>

<examples>
## Prompt Examples

**Multi-scene family reunion — character across complex narrative:**
"The man (@Image1) tiredly walks down a hallway after work, his steps slowing. He stops at the front door. Close-up on his face — he takes a deep breath, adjusts his emotions, releases the negativity, and relaxes. Close-up of him finding his keys, inserting into the lock. After entering, his young daughter and a pet dog joyfully run over to greet him with hugs. The interior is warm and cozy. Natural dialogue throughout."

**Style transfer — character through transformation:**
"Replace the girl in @Video1 with a Chinese opera huadan. The scene is an ornate stage. Reference @Video1's camera work and transitions. Use the camera to match the character's movements. Ultimate stage aesthetics with enhanced visual impact."

**One-take with consistent character across scene changes:**
"Reference all transitions and camera work from @Video1. One continuous take. The scene opens on a chess game, camera pans left revealing yellow sand on the floor, camera tilts up to a beach with footprints. A girl in white walks into the distance on the beach. Camera cuts to an aerial overhead view — ocean waves washing the shore (no people visible). Seamless dissolve transition — the washing waves transform into flowing curtains. Camera pulls back to reveal the girl's face in close-up. One continuous take throughout."
→ cross-ref: see one-take-storytelling.md for full oner techniques

**Product commercial — brand consistency:**
"Perform a commercial-grade showcase of the handbag in @Image2. The side view references @Image1. The surface material references @Image3. Show all details of the handbag. Background audio should be grand and majestic."
→ cross-ref: see commercial-ads.md for full product workflow

**First-person POV with multi-scene references:**
"Set @Image1 as the first frame. First-person perspective. Reference @Video1 for camera movement. Upper scene references @Image2, left scene references @Image3, right scene references @Image4."

**Multi-language commercial with brand elements (15s):**
"0–2s: Rapid four-frame flash cuts — red, pink, purple, and leopard-print bows displayed in sequence. Close-ups of satin sheen and the 'cheri' brand text. 3–6s: Close-up of silver magnetic clasp clicking shut, then gently pulled apart — showcasing silky texture and convenience. 7–12s: Quick cuts of wearing scenarios — wine-red bow on a coat collar for commuter style; pink bow tying a ponytail for sweet street look; purple bow on a bag strap for understated luxury; leopard-print bow on a suit collar for bold style. 13–15s: All four bows displayed side by side with brand name."
</examples>

<common_mistakes>
## Common Mistakes — AVOID

- Not providing multiple angles of same character (front + side = much better)
- Forgetting constraint phrases — face WILL morph without "stable face, no distortion"
- Describing character appearance in text when you have a reference image — use the image
- Mixing up which @Image is which character in multi-person scenes
- Not specifying "same character" when cutting between shots of the same person
</common_mistakes>

<community_examples>
## Community Examples — See community-examples.md

- **White Suit vs Cat** — two distinct characters with locked appearances across 15s fight
- **Qipao Evolution** — same character across 4 historical eras, consistent identity through costume changes
- **Cinematic Dance Video** — single character with detailed appearance spec + photography setup
- **Emotional Chinese Dance** — traditional attire consistency with dynamic camera angles
- **Character Transformation (fish-eye)** — single face reference + 5 outfit changes with effects
</community_examples>
