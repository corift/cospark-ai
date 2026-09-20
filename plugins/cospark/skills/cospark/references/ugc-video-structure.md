# UGC video planning and structure

Use this for a complete creator-led ad with supporting footage. The reusable approach is a continuous spoken story, brief visual examples that clarify it, and a return to the person for the personal takeaway. Adapt it to the brief rather than imposing it on every video.

## Using a reference video

When a supplied or selected video guides the new ad, read [Using a reference video](using-a-reference-video.md). That separate workflow covers source breakdown, what to preserve or adapt, and turning the original shots into a new plan and starting frames. Then use the structure and timing guidance below to complete the requested video.

## Plan the spoken story and what to show

Start with the user's script, or write a short spoken script within the requested duration. Identify its opening thought, useful explanation or demonstration, and conclusion. A personal observation can lead into a concrete feature and then a takeaway, but preserve another structure when the brief calls for it.

Map phrases to shots before generating footage. Choose B-roll because it helps the viewer understand an action, feature, context, or result. Leave opinions and emotional beats on the speaker when their expression contributes more than an insert would. Avoid illustrating every noun or adding unrelated lifestyle footage merely to increase the number of cuts.

| Spoken idea | Useful visual |
| --- | --- |
| Personal opinion, question, or reaction | The speaker's face and expression |
| Physical activity or use case | One recognizable action |
| Product feature | A close-up showing that feature |
| Outcome | The visible result |
| Personal conclusion | Return to the speaker |

Without a reference video, build the shot list from the script. Use [realistic source-led frames](creating-a-realistic-character.md) to prepare the person, action shots, and product shots. The absence of a reference ad does not require inventing every image from text.

Give each planned insert one clear job: the phrase it supports, the action or detail to show, and the framing that makes it legible. Maintain the same character and product across coverage. Choose wardrobe and location continuity appropriate to the story; different activities can naturally use different outfits.

## Test the first line for a new setup

When video production is authorized and the presenter setup is new, generate one short spoken test from the chosen creator frame using `generate_video_from_frames`. Use an actual line from the script, the requested video model, and a supported duration. Reuse a successful existing test instead of charging for the same check again.

Watch and listen for a believable face, natural gestures and blinks, clear speech, useful pace, and lighting that still matches the frame. Follow the [simple clip prompt guide](gemini-talking-head.md): scene and delivery, quoted dialogue, and short fixed rules. If pacing drags, use that guide to distinguish an empty ending from stretched speech and choose a trim or an authorized disposable-dialogue test. Keep the delivered script exact.

If the test needs work, identify whether the frame, performance direction, dialogue length, or edit is responsible. Follow the existing authorization and retry rules. Once it works, keep the chosen frame and delivery direction for the full script. This test is a production step, not a new mandatory user-approval stage. A research, prompt-only, or image-only request does not authorize it.

## Create coverage that will cut together

For a talking-head-plus-B-roll ad, pass the complete script, chosen creator frame, and tested direction to the full UGC workflow. Let it handle script splitting; do not manually generate every remaining line as a separate job. Generate supporting shots separately from their prepared frames. Independent coverage can run alongside the A-roll; wait for the actual speech before locking edit times.

Give a short B-roll generation one manageable action and enough usable footage to choose its entrance and exit. A three-second generated clip may supply a much shorter insert. Do not ask each insert to tell a complete mini-story, repeat the narration, or change scenes internally unless the brief needs that.

For app demonstrations that depend on readable UI or precise interactions, prefer a real app recording when available. Generated phone footage can provide illustrative coverage, but an official screenshot used as its reference does not guarantee accurate taps or screen behavior. Retiming an interaction to hide a generation error can make the app appear sluggish; choose a usable range that preserves a believable response, and disclose illustrative UI when it could be mistaken for a live demonstration.

## Let the spoken timing determine the cuts

Inspect the finished A-roll and B-roll with `inspect_media`, including the visual results. Use the transcript to locate the phrase each insert supports, then choose the useful part of that clip. Planned timings are estimates until the actual delivery exists.

- Let the opening thought establish the speaker when that suits the hook. An effective product-first opening can also be preserved.
- Place an insert near its spoken cue; entering slightly before the key word can give the viewer time to recognize the shot.
- Keep it long enough to understand one idea. Roughly 1–2.5 seconds is a useful starting range for simple quick-cut coverage, not a quota. Reading an interface or understanding a demonstration may require longer.
- Leave once the visual has done its job. The viewer rarely needs to see an entire exercise repetition or a product returning to its starting position.
- Keep the narration continuous beneath picture changes. Mute competing B-roll speech; do not cut words or stretch the delivery merely to accommodate a visual.
- Vary the holds according to meaning. A longer face shot followed by two short inserts can feel more natural than changing shots at equal intervals.
- Return to the speaker when their reaction or closing takeaway benefits from eye contact.

Simple hard cuts often fit this structure. Add transitions, zooms, music, or captions when they serve the requested style, rather than using them as substitutes for useful shot selection.

## Example: a short fitness-app ad

One effective 19-second edit kept the opening thought on the creator, used these inserts, and returned to her face for the closing line:

| Spoken cue | Insert | Time on screen |
| --- | --- | --- |
| “Apple Watch” | Watch-check still | 1.5 seconds |
| “Workouts” | Leg-extension footage | 1.75 seconds |
| “Calories, protein, carbs” | App dashboard close-up | 2.25 seconds |

The transferable choice is the relationship between the phrase and the picture. Neither these subjects nor these durations are a fixed template for the next ad.

## Assemble and review

Use the user's chosen editor or a suitable available tool. FFmpeg can handle simple picture inserts over continuous audio; this creative structure does not depend on FFmpeg or Resolve.

A full UGC result may already contain separately generated scenes, automatic audio trims, and joins. Check the run's scene and trimming metadata, and review the audible boundaries before locking B-roll timing. A complete transcript or an unchanged audio stream in the final edit does not prove that upstream trims preserved natural speech. When a join sounds clipped, compare it with the untrimmed scene if available and retain enough breathing room around the phrase; distinguish trimming damage from generated delivery rather than guessing the cause. If audible review is unavailable, state that limit instead of claiming the joins sound clean.

Save the selected source ranges, timeline placements, and phrase cues with the output. Inspect the assembled result to confirm that the insert timing makes sense, the full spoken thought survives, and the ending finishes cleanly. Contact sheets help review shot selection and sequence; use playback when judging motion or audible joins. Clearly disclose any still used in place of requested animated footage.
