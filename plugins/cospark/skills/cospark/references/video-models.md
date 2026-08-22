# Cospark video models

Use automatic selection unless the user names a model or a workflow needs a specific capability.

| Public model | Duration | Text | Start frame | End frame | References |
| --- | ---: | --- | --- | --- | --- |
| `auto` | Model-dependent | Yes | Yes | Yes | Yes |
| `gemini-omni` | 3–10 seconds | Yes | Yes | No | Images and at most one video; no audio |
| `seedance-2.5` | 4–30 seconds | Yes | Yes | Yes | Images, videos, and audio |
| `kling-3` | 3–15 seconds | Yes | Yes | Yes | No |
| `kling-2.6` | 5 or 10 seconds | Yes | Yes | No | No |

Automatic selection currently uses Gemini Omni for text-to-video and Seedance 2.5 for frame or reference workflows.

`generate_image` currently creates a square 1K image using Cospark's default image model. It does not accept a model override.
