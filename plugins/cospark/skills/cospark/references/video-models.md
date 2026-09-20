# Cospark video models

Use automatic selection for standalone video shots unless the user names a model or a workflow needs a specific capability. The reference-led talking-head workflow uses explicit Gemini Omni selection below. Check the connected schema before relying on any listed capability.

| Public model | Duration | Text | Start frame | End frame | References |
| --- | ---: | --- | --- | --- | --- |
| `auto` | Model-dependent | Yes | Yes | Yes | Yes |
| `gemini-omni` | 3–10 seconds | Yes | Yes | No | Images and at most one video; no audio |
| `seedance-2.5` | 4–30 seconds | Yes | Yes | Yes | Images, videos, and audio |
| `minimax-h3-max` | 5–15 seconds | No | Yes | Yes | No |
| `kling-3` | 3–15 seconds | Yes | Yes | Yes | No |
| `kling-2.6` | 5 or 10 seconds | Yes | Yes | No | No |

Automatic selection currently uses Gemini Omni for text-to-video and Seedance 2.5 for frame or reference workflows.

## Talking-head UGC

For reference-led creator ads, default to individual `generate_video_from_frames` clips with explicit `model: "gemini-omni"`, then assemble them with B-roll. Prefer Omni 1.1 Flash when that version is exposed; check the live schema rather than inventing a version parameter. Preserve another requested model.

For explicitly requested automatic orchestration, `generate_ugc_video` supports `minimax-h3-max` and `gemini-omni`; its service default is MiniMax when the model is omitted. Pass the chosen model explicitly, with the full script and starting images.

For image edits, see [characters and shots](creating-a-realistic-character.md) and the live `generate_image` schema for Nano Banana Pro/Flash, quality and aspect-ratio options. Do not infer image capabilities from this video-model table.
