# Seedance 2.0 Module: Video Extension & Continuation

<module_meta>
when_to_use: Extending videos forward, adding prequels (backward extension), inserting scenes between clips, merging videos, continuing existing footage
related_modules: commercial-ads.md (for brand ending extensions), one-take-storytelling.md (for maintaining continuity)
</module_meta>

<capabilities>
- **Forward extension** — continue a video smoothly from its end
- **Backward extension** — add a prequel before the video starts
- **Scene insertion** — add a new scene between two existing clips
- **Smooth continuity** — maintains shot-to-shot consistency, characters, style
</capabilities>

<critical_rule>
## CRITICAL: Duration Setting

Set generation duration = length of NEW content only.
- Extending by 5s → set generation to 5s
- Extending by 15s → set generation to 15s
- This is the EXTENSION length, NOT total video length
</critical_rule>

<extension_patterns>
## Extension Patterns

| Pattern | Usage |
|---------|-------|
| `Extend @Video1 by [X] seconds.` | Forward continuation |
| `Extend backward by [X] seconds.` | Add prequel |
| `Add a scene between @Video1 and @Video2. The content is [description].` | Scene insertion |
</extension_patterns>

<examples>
## Prompt Examples

**Forward extension — coffee commercial (15s):**
"Extend @Video1 by 15 seconds. 1–5s: Light and shadow slowly slide across a wooden table and cup through venetian blinds, with branches gently swaying. 6–10s: A single coffee bean gently drifts down from above. Camera pushes into the bean until the screen goes black. 11–15s: Text fades in — first line: 'Lucky Coffee', second line: 'Breakfast', third line: 'AM 7:00–10:00'."

**Wild commercial extension (15s):**
"Extend the video by 15 seconds. Reference @Image1 and @Image2's donkey-on-motorcycle character. Add a wild advertisement sequence: Scene 1: Side fixed shot — donkey bursts out of a fence on a motorcycle, nearby chickens are startled. Scene 2: Donkey does donuts on sand. Close-up of motorcycle tire, then aerial overhead shot of the donkey performing spinning stunts, kicking up dust. Scene 3: Snowy mountain backdrop — donkey flies over a hillside on the motorcycle. Ad text 'Inspire Creativity, Enrich Life' appears behind the subject through a masking effect as the motorcycle flies past, ending with a dust trail."

**Fitness ad extension (6s):**
"Extend the video by 6 seconds. An intense electric guitar riff kicks in. 'JUST DO IT' text appears center-screen then gradually fades. Camera tilts up to the ceiling — a muscular man pulls himself up on gymnastic rings, wearing @Image1's tight-fitting workout gear with @Image2's 'Fitness' logo on the back. He powers through the pull-up, then 'DO SOME SPORT' text appears as the closing ad frame."

**Backward extension — adding a prequel (10s):**
"Extend backward by 10 seconds. In warm afternoon light, the camera starts from awnings fluttering in the breeze at a street corner, slowly tilting down to small daisies poking out at the base of a wall. The protagonist's red sneakers appear — he's crouching at a flower stand, smiling as he gathers a big bunch of sunflowers into his arms, petals brushing his white T-shirt. As he turns to step onto his skateboard, the flower stand owner laughs and calls out 'Watch out for flying petals!' He waves back, then starts skating — a few golden petals have already escaped the bouquet, landing on the skateboard deck."
</examples>

<common_mistakes>
## Common Mistakes — AVOID

- Setting generation duration to TOTAL length instead of EXTENSION length — this is the #1 error
- Not maintaining visual continuity — describe the transition from the existing video's end
- Forgetting to specify camera movement in the extension — it defaults unpredictably
- For backward extensions, not matching the tone/lighting of the video's opening frame
- Overloading the extension — too many scene changes in a short extension
</common_mistakes>
