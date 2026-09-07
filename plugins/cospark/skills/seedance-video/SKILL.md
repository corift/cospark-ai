---
name: seedance-video
description: Write and execute raw Seedance prompts for short reference-driven videos, including image-to-video, multimodal character and motion references, continuous takes, timestamped action, dialogue, ambient sound, and realistic camera behavior.
---

# Seedance Video

Direct short Seedance clips from text, images, video, or audio references. Use one deliberate raw prompt that makes the reference roles, spatial continuity, performance, camera, physics, and sound unambiguous.

Read [references/examples.md](references/examples.md) whenever composing a new Seedance prompt.

## Use with Cospark

Use Cospark's `generate_video_from_frames` for an exact starting frame, `generate_video_with_references` for guiding references, and `generate_video` for text-only shots when the requested model supports them. Read the connected tool schema for supported model identifiers, inputs, and durations; display names in this guide are not API identifiers. Use `upload_media` for local inputs and `inspect_media` to review completed clips. A complete multi-shot talking-head script belongs in `generate_ugc_video`.

## Respect the workflow boundary

This skill writes or executes a raw Seedance generation. Do not add a scene planner, prompt optimizer, review agent, replacement start-frame workflow, or edited assembly unless the user requests it.

Honor an explicitly requested Seedance version. Otherwise, use the newest Seedance model actually exposed by the selected tool that supports the required inputs and duration; state the choice instead of silently substituting a different model. Do not claim support for a reference type, duration, resolution, native audio, extension, or editing mode until the connected tool exposes it.

If the user asks only for a prompt, return the prompt without generating. When generating, send the finished creative prompt directly without a second creative rewrite.

## Inspect and assign every reference

Before prompting, inspect each supplied asset and give it one narrow job. Use the tool's actual reference syntax, such as `@Image 1`, only when supported.

Useful roles include:

- start frame and initial composition;
- subject identity, face, hair, or wardrobe only;
- location, lighting, texture, or color only;
- prop appearance or packaging only;
- motion, camera path, editing rhythm, or performance only;
- voice, ambience, music, or sound design only.

Write the role map first when there is more than one reference:

```text
REFERENCES
@Image 1: starting frame and exact initial composition.
@Image 2: the woman's identity and wardrobe only; do not copy its background or pose.
@Video 1: camera movement and action rhythm only; do not copy its people or location.
@Audio 1: voice timbre and cadence only.
```

Do not ask one reference to control everything. Do not let a style or motion reference overwrite identity, wardrobe, setting, object count, or opening composition unless requested.

When several people appear, distinguish them by stable visual traits and role. State who is and is not a referenced identity. State whether a person stays in frame, enters, exits, remains seated, or never interacts with an object. This prevents identity swaps and accidental role transfer.

## Compose the raw prompt

Use the smallest set of sections needed for the shot:

1. `REFERENCES` — each asset and its permitted influence.
2. `FORMAT` — exact duration, aspect ratio, visual mode, and whether it is one take or multi-shot.
3. `OPENING FRAME` — camera position, lens feel, subject blocking, and persistent objects.
4. `CONTINUITY LOCKS` — identities, wardrobe, props, geography, and actions that must never occur.
5. `TIMELINE` — chronological visual and performance beats.
6. `PHYSICS` — contact, weight, momentum, wind, cloth, hair, sand, water, spills, or collisions that materially affect the action.
7. `REALISM` — only the capture imperfections that suit the intended footage.
8. `AUDIO` — ambience, effects, dialogue, silence, and music policy.
9. `VOICE` — speaker-specific delivery when spoken audio matters.

Natural prose is fine. Section labels are for clarity, not a mandatory incantation.

## Direct time and motion

For exact choreography, use timestamp ranges that cover the clip in order:

```text
0–2s: [opening beat and initial reaction]
2–5s: [main action and camera response]
5–8s: [consequence, recovery, and final composition]
```

Use timestamps for meaningful beats, not every blink. A beat should state:

- who initiates the action;
- the direction and path of movement;
- the other subject's immediate reaction;
- how the camera responds;
- where important people and objects end up.

Maintain cause and effect. Preserve left/right and foreground/background relationships from one beat to the next. If the camera follows a single continuous path, name the direction and say whether it may reverse. Avoid impossible simultaneous actions or contradictory camera instructions.

For a one-take clip, say so once near the top. Use motivated occlusion, a whip pan, or a subject crossing the lens only when it helps the action; do not describe a hidden cut as a continuous take.

## Protect physical and visual continuity

Lock only details that materially prevent failure:

- exact people and identity ownership;
- object count, holder, hand, and final location;
- who may enter or leave;
- clothing that must persist;
- camera path and final framing;
- contact order in an interaction;
- whether text, logos, bags, weapons, or other risky additions must be absent.

For contact or high-motion action, describe weight transfer and recovery: feet slip or grip, fabric pulls, hair lags behind a turn, sand shifts under a palm, a body stumbles before regaining balance. Use plausible consequences rather than generic phrases such as “realistic physics.”

Do not bury the desired motion under a huge negative list. Prefer a positive invariant—“George remains seated in the lounger for the entire clip”—over several redundant prohibitions.

## Make phone footage feel captured, not rendered

Use imperfections selectively and consistently. Good options include restrained handheld shake, imperfect autofocus, rolling-shutter smear during a fast pan, exposure breathing, wind buffeting the microphone, partial lens flare, salt or dust on the lens, uneven skin texture, flyaway hair, clutter, and off-center framing.

Tie imperfections to causes. Wind can buffet hair, fabric, flags, sand, and audio together. A fast lateral phone movement can create rolling shutter and autofocus lag. Do not stack every artifact into every prompt.

## Direct audio and dialogue separately

Specify the audio layers that should exist:

- environmental bed;
- synchronized contact and movement sounds;
- dialogue with exact speaker attribution;
- music or explicit absence of music;
- moments that remain silent.

Quote exact dialogue once. Keep reactions and acting directions outside quotation marks. For multiple speakers, identify who speaks each line and who remains silent. Define voice character in a separate concise sentence: age range, pitch or resonance, accent if supplied, cadence, emotional state, and whether the delivery is clean, breathless, distant, interrupted, or off-axis.

## Generate safely

Use the user's chosen references directly. Do not create replacement references or materially alter identity, wardrobe, setting, or composition without permission.

Start only the generation the user authorized. Do not retry or create alternatives when another attempt may incur cost without approval. Inspect the result before claiming it followed identity, choreography, dialogue, audio, or continuity when an inspection tool is available.

## Preflight

Before returning or sending the prompt, confirm:

- every reference has one explicit role;
- the requested capabilities exist in the selected Seedance tool/version;
- the opening description matches the actual start frame;
- named subjects cannot be confused or swapped;
- timeline beats fit the duration and preserve spatial continuity;
- camera direction is coherent;
- contact, motion, and environmental physics have plausible consequences;
- exact dialogue appears once with the correct speaker;
- audio layers do not contradict one another;
- negative constraints are short and targeted;
- the prompt requests either a genuine continuous take or intentional shot changes, not both.
