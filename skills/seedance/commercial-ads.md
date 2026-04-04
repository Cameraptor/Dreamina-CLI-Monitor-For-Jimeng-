# Seedance 2.0 Module: Commercial & Advertising

<module_meta>
when_to_use: Product demos, ad creation/recreation, brand content, e-commerce showcases, template-based ad scaling, multi-language ad localization, product consistency
related_modules: camera-motion.md (for cinematic product camera), character-consistency.md (for brand element consistency), audio-lipsync.md (for multilingual ad voiceover), video-extension.md (for brand ending extensions), editing-effects.md (for ad template recreation)
</module_meta>

<use_cases>
## Commercial Use Cases

- Product demos with synced narration
- Replicate winning ad creatives with your own products
- Template-based ad scaling — one format, multiple product variants
- Brand-consistent multi-scene commercials
- Multi-language ads with native lip-sync
- E-commerce product showcases with detail close-ups
- Content localization — reference original motion, generate new dialogue in target language
</use_cases>

<key_workflows>
## Key Workflow Patterns

**Template recreation:**
Find trending ad → upload as @Video1 → upload your product as @Image1 →
`Reference @Video1's ad concept, camera work, and rhythm. Replace the product with @Image1.`

**Product showcase:**
Upload product from multiple angles →
`Perform a commercial-grade showcase of [product] in @Image1. Side view references @Image2. Material/texture references @Image3. Show all details.`

**Multi-language localization:**
Upload original ad → generate new dialogue in target language with native lip-sync
→ cross-ref: see audio-lipsync.md for multilingual dialogue techniques

**Brand ending (extension pattern):**
`Extend @Video1 by 10s. Camera pushes in → clean background → product center-frame → brand text fades in → music crescendos.`
→ cross-ref: see video-extension.md for extension rules

**Text-to-video ad (no references needed):**
Describe the full ad concept, scene by scene, with time segments for 10-15s.
</key_workflows>

<examples>
## Prompt Examples

**Painting-comes-alive concept (cola ad — text-to-video, no refs):**
"The person in the painting looks nervous, eyes darting left and right, then peeks out from the frame. They quickly reach out of the painting to grab a cola, take a sip, and show a satisfied expression. Footsteps approach — the person in the painting hurriedly puts the cola back. A cowboy walks up and takes the cola, then leaves. The camera pushes in as the screen gradually fades to black with only a top light illuminating a can of cola. Artistic subtitles appear at the bottom: 'Yikou Cola — a taste you can't miss!'"

**Multi-language commercial with brand elements (15s):**
"0–2s: Rapid four-frame flash cuts — red, pink, purple, and leopard-print bows displayed in sequence. Close-ups of satin sheen and the 'cheri' brand text. 3–6s: Close-up of silver magnetic clasp clicking shut, then gently pulled apart — showcasing silky texture and convenience. 7–12s: Quick cuts of wearing scenarios — wine-red bow on a coat collar for commuter style; pink bow tying a ponytail for sweet street look; purple bow on a bag strap for understated luxury; leopard-print bow on a suit collar for bold style. 13–15s: All four bows displayed side by side with brand name."

**Product showcase — handbag:**
"Perform a commercial-grade showcase of the handbag in @Image2. The side view references @Image1. The surface material references @Image3. Show all details of the handbag. Background audio should be grand and majestic."

**Ad recreation from template:**
"Reference the video's ad concept. Using the provided down jacket image, reference the goose feather image and swan image. Pair with this ad copy: 'This is goose down. This is a warm swan. This is a wearable arctic swan-down jacket. Dress warm for the new year, live warm every day.' Generate a new down jacket advertisement."

**Range-hood ad with contrasting emotions:**
"This is a range-hood advertisement. @Image1 as the first frame — a woman elegantly cooking, no smoke. Camera quickly pans right to @Image2 — a man sweating profusely, face flushed, cooking in heavy smoke. Camera pans left and pushes in on a range hood on @Image1's table — the hood references @Image4 — frantically sucking up all the smoke."

**Commercial edit with brand insertion:**
"@Video1: Camera pans right. The fried chicken shop owner busily hands fried chicken to queuing customers, saying in Mandarin: 'After his order, yours — everyone please line up.' He then grabs a paper bag printed with @Image1's design. Close-up of the branded bag. Close-up of the hand-off to the customer."

**Commercial car showcase:**
"Reference @Video1's camera work, frame transitions, and rhythm. Replicate using the red supercar from @Image1."
→ cross-ref: see camera-motion.md for cinematic camera techniques
</examples>

<tested_remix_workflows>
## Tested Ad Remix Workflows

1. **Commercial recreation** — trending ad + your product images → reference concept, rhythm, replace product
2. **Fashion runway swap** — runway video + clothing image → replace clothing
3. **Character replacement in ad** — ad video + new talent image → replace lead, replicate all actions
4. **Template scaling** — one winning ad format → multiple product variants using same template
5. **Multi-language localization** — original ad → new language with native lip-sync
6. **Brand ending extension** — existing video + brand assets → extend with closing brand frame
</tested_remix_workflows>

<common_mistakes>
## Common Mistakes — AVOID

- Not including a clear closing frame with brand/text/tagline — always plan the final 2-3s
- Forgetting to specify product detail close-ups — model won't prioritize them without instruction
- Writing ad copy in prompt without specifying it should appear as ON-SCREEN TEXT vs voiceover
- Not using time segments for 10-15s ads — pacing becomes uncontrolled
- Not specifying the exact visual style/mood of the ad (cinematic, playful, luxury, etc.)
</common_mistakes>

<community_examples>
## Community Examples — See community-examples.md

- **UGC Skincare** — complete SETTING/LIGHT/CAMERA/SUBJECT/AUDIO/PROPS/ACTION/DIALOGUE breakdown, "iPhone feel"
- **Qipao Evolution** — 15s commercial with character consistency through 4 eras, drum rhythm sync, time segments
</community_examples>
