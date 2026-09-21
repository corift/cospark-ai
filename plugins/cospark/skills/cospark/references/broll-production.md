# B-roll production

Shared guidance for Gemini and Seedance B-roll, product inserts, and native montages: framing, visible action, source timing, assembly, and review. Apply the selected model guide and current tool schema for execution settings. The Gemini examples and observations below retain their original scope; they are not evidence of identical Seedance behavior.

For reference-led B-roll, prepare and animate the individual shots below, then cut their best moments together. For a montage generated inside one clip, use [Timed B-roll shot prompts](broll-shot-prompts.md).

For a full ad, start with the [script-linked storyboard](ugc-video-structure.md#plan-the-spoken-story-and-what-to-show), not a disconnected batch of attractive shots. Check where the creator, supporting activities and real product demonstrations belong. For each missing insert, name its spoken cue, visible action, approximate edited hold and source. Generate only the missing coverage; preserve good existing clips. A revision that needs more B-roll may need different activities and earlier placement, not simply more shots of the same payoff.

## Start with a real shot

For realistic UGC B-roll, find an existing Instagram or TikTok video that already has useful framing, lighting, surroundings and activity. The video does not need to advertise the same product, follow the same script, or match the whole ad. Choose it for the shot you need. A dinner reel can supply cooking coverage for a meal-planning app; a morning routine can supply a countertop or product-handling setup for another product.

First check the video that supplied the creator frame. It may also have the preparation, activity and result shots you need. Otherwise, find another suitable video through [reference discovery](reference-discovery-and-inspection.md). Keep rooms, light, props and wardrobe compatible when the sequence should feel recorded by one person. Do not force an unsuitable shot just to stay with one source. Honor supplied footage and explicit text-only or no-reference requests.

1. Inspect the actual video and extract an original frame for each useful shot. Keep its source link and timestamp; do not use a contact-sheet crop.
2. Make all needed changes in one image edit from that original frame. Preserve what already works. Change only the relevant person, product, clothing or props and remove social overlays. When a person must match the selected creator, attach that creator image as a separate identity reference. Never use the last edited shot as the next shot's source.
3. Choose the image model by the edit, using [the frame-edit model guide](creating-a-realistic-character.md#choose-the-image-model). Simple food or object cleanup can start with Nano Banana 2 / Flash; creator identity edits normally use Pro. Review the frame before animation.
4. Animate the edited frame with one manageable action or small phone movement. Pass it as the actual starting frame. Preserve the requested video model; for Gemini Omni 1.1 Flash, follow [Gemini video](gemini-video.md).
5. Inspect the clip and keep its useful moment. A three-second generation can supply a one- or two-second insert. Cut the shots against the narration, mute unwanted source audio, and avoid adding zooms or speed changes without a reason.

Use the source to guide new footage, not as permission to insert someone else's original video into the finished ad. If a reference shows a different product, use the target product's real assets for its appearance and details; do not carry over the reference brand or invent a working app screen.

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
