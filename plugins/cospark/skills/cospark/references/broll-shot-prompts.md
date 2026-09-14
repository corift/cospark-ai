# Timed B-roll shot prompts

Use this structure for Gemini Omni and Seedance B-roll montages. Keep model selection, supported duration, resolution, and reference inputs in the relevant model guide and current tool schema.

## Prompt structure

Start with total duration, aspect ratio, shot count and cut count, then describe who is filming, the setting, light and camera style. For a montage of separately filmed moments, say so explicitly: a new subject appears after a cut rather than transforming within a shot.

Give each shot its own time range and short descriptive title. Describe the visible composition, one manageable action or camera movement, and any continuity needed with a previous view. Begin each subsequent shot with `HARD CUT to`. Plain `[0-1s]: ...` or `0.00–1.00s — Shot title` both work as readable directions; the useful structure is explicit intervals and concrete shots, not a particular punctuation style. B-roll needs no `Dialogue` or `Action` field labels.

Use contiguous intervals that cover the requested runtime. Choose beat lengths for the material: fast food diaries or activity montages often use roughly 0.75–1.5 seconds per shot; a continuous camera reveal can need longer. Do not turn a seven-shot example into a fixed count for every duration.

End with a short set of relevant constraints and make responsibility explicit: all requested shot changes and camera moves should occur in the generated video when asking for a native montage. If generating source shots for manual assembly, put the final edit boundaries in the edit plan instead.

## Example: seven-second food diary

```text
Create a 7-second vertical 9:16 food-diary B-roll montage with seven distinct shots and six clean hard cuts. A woman films her own meals with a good phone in an ordinary bright home. Show food and occasionally her hand. Natural food texture, uneven homemade portions, real window light and gentle handheld movement. The cuts skip between separately filmed meals; food never transforms into another dish within a shot.

0.00–1.00s — Breakfast
Overhead handheld view of a fully visible breakfast plate on a wooden table: fried eggs, browned potato rounds, avocado and watermelon. Small camera drift.
1.00–1.75s — Breakfast detail
HARD CUT to a tighter oblique view of the same eggs and potatoes. Brief restrained move closer; preserve the breakfast arrangement.
1.75–2.65s — Mango smoothie
HARD CUT to thick yellow smoothie already pouring into a clear glass on a kitchen counter. The liquid pools and the level rises coherently.
2.65–3.65s — Fish tacos
HARD CUT to two fish tacos on a white plate with corn, mango and cilantro. Small handheld move across the plate.
3.65–4.85s — Papaya boat
HARD CUT to a papaya half filled with yogurt and granola. Her right hand brings a metal spoon into the yogurt and begins a small scoop. Keep the spoon solid and fruit intact.
4.85–5.95s — Pasta detail
HARD CUT to creamy spaghetti with browned chicken in a ceramic bowl. Visible irregular strands and clinging sauce. Subtle handheld drift.
5.95–7.00s — Pasta wide
HARD CUT to the same pasta bowl beside a small salad. Her left hand steadies the rim as the camera eases back slightly. End during the continuing movement.

Each dish appears immediately after its hard cut. No dissolves, morphing meals, spinning plates, slow motion, captions, logos, talking, narration or music. All shot changes and camera moves must be present in the generated video.
```

This is an adapted example, not a verbatim record of a run. The spoon, pour, tighter shots and hand are deliberate parts of this brief. For untouched-food recordings, remove those actions and describe phone movement instead; do not inherit conflicting restrictions from another prompt.

## Inputs, review and editing

Text-only generation is a useful option when the brief permits invented meals or scenes. References help when matching a specific dish, person or setting matters; do not make extra image preparation a prerequisite for an authorized text-only test. An exact starting frame anchors the opening, not every later setup.

Inspect the generated sequence for the requested views, physical interactions, continuity between repeated views and actual cut times. Timestamps direct the model but do not guarantee frame-exact execution. Use FFmpeg or a video editor to adjust joins when needed; generate changes of perspective or reveals when the footage does not contain the necessary view.

## Evidence

September 12, 2026: Sully supplied a Seedance food montage made with this seven-shot structure and strongly preferred it to the preceding Omni food tests. Local inspection found a 7.042-second, 720×1280, 24 fps silent video and the seven requested views in sampled frames. Sully explicitly endorsed this prompt structure for both Seedance and Gemini. This establishes the Seedance result and the preferred shared format; it does not establish Gemini performance on the identical prompt or isolate model choice from the earlier single-shot workflows.
