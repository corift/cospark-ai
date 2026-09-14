---
name: gemini-video
description: Write and execute Gemini Omni Flash video prompts for talking-head clips, B-roll, product shots, montages, and replacement shots. Use when Gemini is requested or selected; complete multi-shot talking-head scripts use Cospark's full UGC workflow.
---

# Gemini Video

Direct individual clips and requested montages with Gemini Omni Flash. Choose the prompting guidance for the shot; talking-head dialogue and gestures are one mode, not the template for every video.

## Choose the prompting guidance

- **Talking-head dialogue or spoken product handling:** read [talking-head prompting](references/talking-head.md) and its examples. Keep dialogue and actions separate and anchor gestures to spoken phrases.
- **B-roll, silent product shots, or inserts:** read [B-roll production](../cospark/references/broll-production.md). Use plain timed visual descriptions without invented dialogue or talking-head field labels.
- **A generated montage:** read [timed B-roll shot prompts](../cospark/references/broll-shot-prompts.md). Name the cuts explicitly and remove conflicting continuous-shot restrictions.
- **A complete ad with supporting footage:** use [UGC video structure](../cospark/references/ugc-video-structure.md) to plan coverage and assembly. Keep clip prompting here.

Read only the guidance needed for the requested shot. B-roll framing, reference selection, and editing principles are shared with Seedance; the talking-head prompt format and Gemini delivery observations live in this skill.

## Use with Cospark

Check the connected tool schema for supported model IDs, durations, resolution, and inputs. This skill covers Gemini Omni Flash; honor an explicit version and otherwise prefer Omni 1.1 Flash when exposed. If unavailable, explain the limitation instead of silently changing models.

For a controlled opening, prefer a strong starting image and `generate_video_from_frames`. Use the image as the actual first frame. Prepare realistic references using [characters and shots](../cospark/references/creating-a-realistic-character.md). Honor text-only requests with `generate_video` when supported; do not add reference preparation to an authorized text-only test. Reference-guided generation is currently a preferred Seedance workflow, not a limitation on other models' capabilities.

A complete multi-shot talking-head script belongs in [Cospark's full UGC workflow](../cospark/SKILL.md). Pass `model: "gemini-omni"` explicitly, the full script in `prompt`, and starting images according to the connected schema. Omitting the model uses the service's MiniMax default. Do not manually split a full script into independent clip jobs by default.

Use Cospark's shared instructions for uploads, polling, charged retries, and media inspection. For a prompt-only request, return the prompt. For authorized generation, send the completed raw prompt without a second creative rewrite. Default to 9:16 and 8 seconds only for a portrait talking-head test; choose other shot durations and framing from the brief and supported settings.

## Review the shot

Check that the opening supports the action, named hands and objects stay coherent, and timed beats fit the source duration. For speech, preserve and verify the exact line; for silent B-roll, do not introduce dialogue. A single take and a montage need different cut constraints.

Inspect the finished media before claiming that dialogue, gestures, action, or cuts match. Requested timestamps express intent; measure the actual output before choosing edit ranges. Keep final assembly timings separate from source-clip timings.
