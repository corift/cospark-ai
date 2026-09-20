# Gemini Video

Direct individual clips and requested montages with Gemini Omni Flash. Choose the prompting guidance for the shot; talking-head dialogue and gestures are one mode, not the template for every video.

## Choose the prompting guidance

- **Talking-head dialogue or spoken product handling:** read [Generate realistic UGC clips](gemini-talking-head.md). Use scene and delivery, quoted dialogue, and short fixed rules. Let gestures happen naturally; describe a specific action only when the brief needs it.
- **B-roll, silent product shots, or inserts:** read [B-roll production](broll-production.md). Use plain timed visual descriptions without invented dialogue or talking-head field labels.
- **A generated montage:** read [timed B-roll shot prompts](broll-shot-prompts.md). Name the cuts explicitly and remove conflicting continuous-shot restrictions.
- **A complete ad with supporting footage:** use [UGC video structure](ugc-video-structure.md) to plan coverage and assembly. Keep clip prompting here.

Read only the guidance needed for the requested shot. B-roll framing, reference selection, and editing principles are shared with Seedance; the talking-head prompt format and Gemini delivery observations live in the Gemini references.

## Use with Cospark

Check the connected tool schema for supported model IDs, durations, resolution, and inputs. This guide covers Gemini Omni Flash; honor an explicit version and otherwise prefer Omni 1.1 Flash when exposed. If unavailable, explain the limitation instead of silently changing models.

For a controlled opening, prefer a strong starting image and `generate_video_from_frames`. Use the image as the actual first frame. Prepare realistic references using [characters and shots](creating-a-realistic-character.md). Honor text-only requests with `generate_video` when supported; do not add reference preparation to an authorized text-only test. Reference-guided generation is currently a preferred Seedance workflow, not a limitation on other models' capabilities.

For a reference-led creator ad, follow [the UGC workflow](ugc-video-structure.md): test the setup, generate the remaining dialogue as individual clips with `model: "gemini-omni"`, then assemble with supporting footage. If the user explicitly wants automatic full-script planning and assembly, use `generate_ugc_video` with the complete script and explicit model. Do not silently replace a requested manual workflow with that tool.

Before executing tools, read [Cospark tools](cospark-tools.md) for uploads, polling, charged retries, and media inspection. For a prompt-only request, return the prompt. For authorized generation, send the completed raw prompt without a second creative rewrite. Use portrait framing for a portrait talking-head test. Choose duration from the dialogue, intended delivery, and supported settings; honor the user's requested length.

## Review the shot

Check that the opening supports the action and hands and objects stay coherent. For speech, preserve and verify the intended line; for silent B-roll, do not introduce dialogue. A single take and a montage need different cut constraints.

Inspect the finished media before claiming that dialogue, gestures, action, or cuts match. Requested timestamps express intent; measure the actual output before choosing edit ranges. Keep final assembly timings separate from source-clip timings.
