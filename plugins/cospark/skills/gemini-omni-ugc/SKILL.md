---
name: gemini-omni-ugc
description: Write and execute raw Gemini Omni Flash prompts for short, individual UGC video clips from a prepared start frame. Use for A-roll, B-roll, direct-to-camera dialogue, product handling, clip tests, and replacement shots. Use a full UGC workflow instead when a long-form script needs complete multi-shot A-roll generation and assembly.
---

# Gemini Omni Flash UGC

Create a natural 5–10 second UGC-style clip from an exact opening image. Optimize the start frame and raw video prompt for believable speech, expressions, gestures, product handling, and other requested motion.

Read [references/examples.md](references/examples.md) whenever composing a new Gemini Omni UGC prompt.

For B-roll, inserts and footage of someone showing a meal or object, read [B-roll prompting](references/broll-prompting.md). Use the shared [timed shot structure](../cospark/references/broll-shot-prompts.md) for montages and plain timed descriptions for single shots; do not carry over the talking-head `Dialogue`/`Action` labels.

## Use with Cospark

Prefer Cospark's `generate_video_from_frames` for individual Gemini Omni shots: create or refine a strong starting image, then animate it. Establish the desired style, character, composition, lighting, and props in the image to give the video a concrete visual starting point. The image can be supplied or created for the task, and a single starting frame is enough. Reference-guided generation through `generate_video_with_references` is primarily reserved for Seedance workflows for now; use `generate_video` for text-only shots when the brief calls for that approach and the requested model supports it.

Read the connected tool schema for supported model identifiers, inputs, and durations; display names in this guide are not API identifiers. Use `upload_media` for local inputs and `inspect_media` to review completed clips. A complete multi-shot talking-head script belongs in `generate_ugc_video` with `model: "gemini-omni"`, the full script in `prompt`, and the supplied starting images using the connected tool's schema. Set the model explicitly: omitting it uses the service's MiniMax default.

## Choose the workflow

Use this skill whenever the user needs an individual Gemini Omni Flash clip, including A-roll, B-roll, standalone shots, product shots, tests, and replacement shots. Use the full UGC workflow such as Cospark's `generate_ugc_video` when a long-form script needs complete multi-shot A-roll generation and assembly.

Keep the workflow focused on the requested clip. Add scene planning, review loops, or multi-scene composition when the user asks for them.

When the request is a full UGC ad with B-roll, read [UGC video planning and structure](../cospark/references/ugc-video-structure.md) to decide the story and supporting shots before composing individual clip prompts. That guide also covers placing cuts against the actual narration; it applies across models and editors.

When a compatible video tool is available, select Gemini Omni Flash, preferring Gemini Omni 1.1 Flash when the tool exposes that version. Send the completed creative prompt directly without a second creative rewrite. If the user asks only for a prompt, return the prompt without starting a generation. If Gemini Omni is unavailable, say so rather than silently substituting another video model.

## Prepare the start frame

When sourcing or remaking A-roll, B-roll, or product-shot references, follow [Creating realistic characters and shots](../cospark/references/creating-a-realistic-character.md): use a real photo or exact video frame, change the face, clothing, and colors as requested, and preserve the rest of the shot. For B-roll and product demos, use existing media even when its product differs; adapt the product and necessary action through the prompt.

The source image strongly controls the result. For talking-head shots, prefer a clean 9:16 frame with:

- direct eye contact and a plausible starting expression;
- the face, shoulders, forearms, and hands visible;
- room around the hands for the requested gesture;
- any handled product already present, legible, and held securely;
- only the people and objects that must persist through the clip;
- no browser chrome, social UI, captions, watermarks, or overlays.

If the user asks to clean or remake a screenshot, preserve the subject, products, pose, wardrobe, room, lighting, and composition while removing the UI. Check hand anatomy, object count, label quality, and grip before animating.

Do not replace a usable user-supplied frame merely to polish it. Apply appearance changes the user has already requested; ask only before materially changing the person, product, setting, or composition beyond that scope.

## Compose the talking-head raw prompt

Use this order:

1. Establish a natural one-take smartphone UGC shot and camera behavior.
2. Protect the subject, setting, clothing, object count, and important packaging.
3. Describe the voice and delivery in one concise sentence.
4. Quote the exact dialogue once in a timed range.
5. Choreograph actions in timed ranges and tie the main gesture to a specific word or phrase.
6. End with only the guardrails that prevent likely failures.

Use this adaptable structure:

```text
A natural one-take smartphone UGC talking-head video. The camera stays fixed. Preserve [the person, setting, outfit, and important objects] from the starting frame. Keep [hands/products] coherent and realistic.

[The speaker] speaks directly to the camera in a [voice and delivery], with natural eye contact and [energy level].

Dialogue [0-Xs]: "[Exact spoken line.]"
Action [0-As]: [Starting expression or compact gesture.]
Action [A-Bs]: On "[anchor word or phrase]," [one clear primary action with named hand/object].
Action [B-Cs]: [Return, settle, or secondary beat.]
Action [C-end]: [Hold naturally and finish expression.]

No cuts, no camera movement, no added people or objects, no captions, no background music, and no additional spoken words.
```

Keep action and dialogue separate. Do not bury choreography inside prose about mood or visual style.

Write each timed beat on its own line with a bracketed range, such as `Action [0-2s]: ...` and `Action [2-3s]: ...`. Use non-overlapping ranges for successive actions and cover the requested source duration. These are source-clip seconds; keep final montage cut positions in the edit plan. Timestamps express intent and must be checked against the output; they are not a guarantee of frame-exact execution.

## Direct natural “yapper” gestures

Use compact, purposeful gestures that match the spoken idea:

- eyebrow lift or slight lean-in for a hook;
- pinched fingertips opening outward for emphasis;
- one palm-up question gesture;
- a small hand circle while explaining context;
- hands separating left and right for a contrast;
- a brief self-point on “I” or “my”;
- one finger-counting beat for a short list;
- a small nod or knowing head tilt on the conclusion;
- one deliberate product push toward the lens, followed by a return.

For an 8-second clip, prefer one primary gesture, one micro-expression, and one settling beat. Tie the primary motion to a key word. Continuous generic gesturing often looks frantic, while several simultaneous object motions increase deformation.

### High-gesture direct-response hooks

When the user explicitly wants more hand expression and the start frame shows both forearms with enough room, use a sequence of distinct gesture beats instead of asking for generic continuous movement. For a 10-second hook, three or four sequential beats can work well:

1. Open with a compact two-handed emphasis, such as loose fingertips moving together and then opening into both palms.
2. Map a verbal contrast to opposite sides of the frame with one open-hand gesture per side.
3. Use one palm-up invitation or small forward hand motion for the promise or request.
4. Use one compact explanatory circle, then settle both hands into an open position and finish with a small nod.

Anchor every beat to a quoted phrase from the dialogue and give it a non-overlapping time range. Keep both hands at chest level and inside the portrait frame. Ask for active but believable conversational “yapper” gestures, not constant arbitrary motion. Protect anatomy explicitly, avoid simultaneous competing actions, and end in a stable pose.

For a dense 10-second hook, let the dialogue occupy the full duration when preserving the exact line is more important than reserving a silent finish. Use a quick but clear delivery and keep the final settling action attached to the last phrase.

When products or props are present:

- name the exact object and hand that moves;
- anchor the other objects in place;
- state the movement order and final position;
- move only one object toward the lens at a time;
- keep the object from covering the entire face unless intentional;
- allow roughly two seconds for a forward-and-back product motion.

## Fit the dialogue to the duration

This section applies to spoken clips. Calculate overall WPM as actual spoken words × 60 / actual video duration; script words and requested duration give a planning estimate. Direct delivery in ordinary language instead of treating a numeric WPM instruction as a reliable speed control. Account for omitted or repeated words when reviewing the result.

Default to 8 seconds for tests unless the user requests another supported length. Keep the spoken line short enough to leave a natural finish. Roughly 10–18 words works well for many 8-second clips; an intentionally fast yapper delivery may support slightly more.

Give dialogue a bounded range instead of assigning every word a timestamp. Reserve the final 1–2 seconds for the return motion, eye contact, and a relaxed finish when the action needs it.

Do not paraphrase, add filler, repeat dialogue, or change brand names. If the requested line is too long, shorten it only with approval or use a longer supported duration.

## Generate when requested

Use the user's start frame as the actual first frame, not merely a visual reference. Default to 9:16 and 8 seconds for a portrait UGC test. Pass the raw prompt unchanged to Gemini Omni Flash.

Start only the generation the user authorized. Do not create replacement generations because a job is slow, and do not retry a failed generation if another attempt may incur cost without user approval.

Before claiming that the output followed the dialogue or gestures, inspect the finished media when an inspection capability is available.

## Preflight check

Before returning or sending the prompt, confirm:

- the start frame can physically support the requested motion;
- any requested dialogue fits the duration; silent B-roll has no invented dialogue;
- every moving hand or object is unambiguous;
- stationary products and props are anchored;
- a speaking gesture is tied to a word or phrase; B-roll action is tied to its timed visual beat;
- the gesture intensity matches the user's request, using sequential phrase-anchored beats for an explicitly high-gesture hook;
- timed descriptions use explicit ranges that fit the source duration; B-roll uses plain time blocks or timed shot titles without dialogue/action labels;
- the prompt describes one continuous shot unless the brief explicitly requests model-generated cuts; in that case, name each cut and remove contradictory no-cut restrictions;
- only essential negative constraints remain.
