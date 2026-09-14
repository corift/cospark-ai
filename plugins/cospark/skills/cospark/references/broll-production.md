# B-roll production

Shared guidance for Gemini and Seedance B-roll, product inserts, and native montages: framing, visible action, source timing, assembly, and review. Apply the selected model skill and current tool schema for execution settings. The Gemini examples and observations below retain their original scope; they are not evidence of identical Seedance behavior.

For montages, start with [Timed B-roll shot prompts](broll-shot-prompts.md), the shared Seedance/Gemini structure endorsed after the seven-shot food test. The single-shot example below serves continuous coverage; it should not replace a requested montage.

## Plan the visible action and opening

Distinguish showing from interacting. Someone recording a meal may only move the phone slightly. Do not add a fork lift, spoon scoop, bite, pour or product pickup unless it serves the requested shot. Those are separate physical actions that change the brief and the difficulty of generation.

Prepare the intended opening composition in the starting frame. For a casual wide phone shot, show the plate or object with surrounding table or room already visible. A tight food photograph will strongly influence the opening even if the prompt asks for wide framing. Find a wider source or adapt and review the frame when needed. Generating a pullback and trimming its opening can rescue useful coverage, but should not be the default way to obtain an ordinary wide shot. Generate a continuous reveal when that move is itself requested.

Define who holds the camera and what their free hand can do. Use ordinary scene light and a suitable phone viewpoint, preserving useful imperfections in the reference. A slight downward angle or top-down shot can both fit UGC; choose based on the brief and reference. Avoid automatically adding a macro view, a push-in, shallow focus or commercial food styling.

## Use explicit time blocks

Establish the scene and essential continuity once. Then use plain timed descriptions: `[0-2s]: ...`, `[2-3s]: ...`. B-roll does not need the talking-head template's `Dialogue` and `Action` labels. Describe what is visible and how the camera moves within each interval. Keep successive ranges non-overlapping and cover the source duration. A continuing movement can span multiple ranges without stopping at each boundary.

Example for an already-wide three-second starting frame:

```text
A casual vertical iPhone rear-camera video of someone showing their meal before eating. Start from the supplied wide image. Preserve the dish, food arrangement, table and ordinary window light. The phone is held at a comfortable seated distance, pointed slightly downward. Keep the whole plate and surrounding table visible.

[0-2s]: The phone drifts slightly sideways at the starting distance. The whole plate and surrounding table remain visible; the meal is untouched.
[2-3s]: A small framing correction keeps the plate in view without moving closer. End during the continuing movement without a freeze or fade.

No hands or utensils enter the shot, no eating, no added objects, no zooms, no cuts, no text, no speech or music.
```

For an interaction, replace the relevant beat with one specific action: name the hand, existing object, movement and resulting state. Do not retain a no-hands or no-utensils restriction that conflicts with it. For a camera reveal, specify the starting view, path, time to reach the ending view, and what remains stationary.

Bracketed timing borrows the explicit intervals used by Cospark's Gemini talking-head prompt planner, not its dialogue/action template. Sully explicitly clarified this distinction for B-roll. A three-second timed pasta take was generated, but it did not isolate the effect of prompt format. Do not claim that brackets alone improve motion or guarantee exact timing.

## Separate generated timing from assembly timing

For a single source shot, avoid requesting unnecessary edits inside the generation. For an explicitly requested native montage, use `[0-2s]: ...`, `[2-3s]: HARD CUT to ...`, and so on. Describe each new view and what happens. Remove any global “one continuous shot” or “no cuts” instruction. A single starting frame anchors only the opening; it does not establish every later setup or guarantee identity consistency.

Choose the route per shot. Generate camera moves that reveal new surroundings or change perspective. Use FFmpeg or an editor for precise cuts and supported crop changes when useful. An energetic montage may use 1–2-second inserts, but a casual showing shot or readable demonstration may need a longer hold. Do not add a tight crop at every cut, particularly when the user wants wider phone framing.

The model's timestamps refer to the source clip. Record source in/out points separately from final timeline positions. Inspect the output before selecting the usable portion; requested move completion times are not measured timings.

## Review the result

- Compare the actual framing with the requested view: plate edges, table context, viewpoint and camera distance.
- Check that only requested actions occur. Distinguish an agent-prompted utensil action from one the model invented.
- Watch the action and camera path at normal speed. For reported lag or stutter, check playback, source cadence, repeated/held frames and export timing before assigning a cause. Matching nominal frame rates does not establish smooth motion. Do not add interpolation or speed changes automatically.
- Verify actual dimensions and duration. Treat resolution as a tool setting, not an adjective in the prompt.
- Review sound separately. Model-generated audio may still be present; mute it in an intended silent assembly. Conflicting automated audio descriptions and transcripts require listening before asserting speech occurred.

## Evidence and scope

In the September 2026 Pinterest food test, three unedited photo references became exact Omni starting frames. The first assembly used manually added punch-ins and agent-prompted fork/spoon interactions. Sully liked the generated footage but wanted wider casual phone recordings of untouched meals. A second batch generated wider views; the edit retained those portions and removed punch-ins and utensil actions. Sully approved the overall direction and reported slight lag, whose cause remains unresolved. These observations support matching source framing and action to the brief; they do not establish a universal model preference, ban top-down shots, or prove that unrelated Pinterest photos will form a coherent creator sequence.
