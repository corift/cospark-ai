# Generate realistic UGC clips

Start with the selected creator image. Get one short clip working before generating the remaining script. Reuse a setup that already works.

## Write a simple prompt

Use three parts:

1. **Scene and delivery:** Describe the camera setup and how the person should speak.
2. **Dialogue:** Put the exact spoken words in quotation marks.
3. **Fixed rules:** Add a few instructions to preserve the shot and prevent unwanted changes.

Let the person gesture naturally. Avoid assigning hand movements, expressions, or head turns to specific seconds unless the user requests a particular action. For a requested action, describe it plainly without adding a full gesture sequence.

### Example

```text
Static locked-off shot, casual UGC iPhone footage. The woman talks to the phone with high energy, like an engaging social-media creator. Her delivery is brisk, confident, and expressive, with playful frustration about the dinner rush.

"It's already SIX, everyone's hungry, and I'm scrolling through saved recipes trying to figure out DINNER."

One continuous shot, no jump cuts. Natural eye contact, normal blinking, and small conversational gestures. Preserve her identity, glasses, clothing, background, and existing lighting. No camera movement, added text, music, or words outside the quoted dialogue.
```

Match the delivery to the script. Use capitalization selectively to suggest emphasis. Adapt the example's person, setting, and camera behavior to the selected image and brief.

## Fit the dialogue to the clip

Choose a supported duration that gives the line enough room at the intended pace. Honor the requested duration and avoid requesting a long silent finish. Set duration in the generation tool; writing it in the prompt is not enough.

If the result drags:

- **Silence after the sentence:** trim the empty ending.
- **The words themselves are stretched:** try appending a short disposable phrase to the quoted dialogue, then trim it off after generation. Choose a neutral phrase that does not suggest a new physical action.

Keep the intended line unchanged and check that the trim preserves its final word. Disposable dialogue is only a production aid for a clip that will be trimmed; do not add it to a prompt-only or exact unedited-dialogue request unless requested. Keep the source and final cut, and follow the authorized generation/retry scope.

## Review the first take

Watch and listen for natural delivery, believable facial movement, useful gestures, consistent lighting, and complete dialogue. Check for unwanted captions or scene changes.

Change the specific thing that failed. Do not keep adding instructions when the take already works. If the frame repeatedly animates poorly, reconsider the starting image before generating the rest of the script.

## Continue with the same setup

Once the user likes a take, reuse its starting image, camera setup, delivery direction, and fixed rules. Change the dialogue for the next requested passage. For a complete ad, pass the successful direction and full script into the [full UGC workflow](cospark-tools.md).

Use the requested model. Keep prompts, settings, and selected outputs together so the successful approach can be repeated. See [Gemini video](gemini-video.md) for frame inputs and model selection, and [Cospark tools](cospark-tools.md) for execution and inspection.

## Previous approach

The former [timed Dialogue + Action guide and examples](archive/gemini-talking-head.md) are preserved for reference. Read them only when the user explicitly asks for that approach; do not use them as an automatic fallback.
