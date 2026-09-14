# Gemini Omni talking-head clips

Use for direct-to-camera dialogue, natural gestures, and spoken product handling. Read [prompt examples](gemini-examples.md) when composing a talking-head prompt.

## Prepare the start frame

When sourcing or remaking A-roll, B-roll, or product-shot references, follow [Creating realistic characters and shots](creating-a-realistic-character.md): use a real photo or exact video frame, change the face, clothing, and colors as requested, and preserve the rest of the shot. For B-roll and product demos, use existing media even when its product differs; adapt the product and necessary action through the prompt.

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
