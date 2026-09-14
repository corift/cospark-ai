# Single-entry Cospark skill evaluation

Date: September 14, 2026. Candidate: the single-entry skill in this PR; exact file hashes are recorded in `candidate-files.json`.

## Result

All eight scenario criteria passed manual review of the independent agents' responses and reported file reads. Plugin/skill validation, contained links, reference reachability, YAML parsing, and the single-entrypoint check passed. Both provider example collections are unchanged from the preceding draft.

This is a constrained behavioral evaluation: four independent agents handled the dialogue, montage, research, and full-ad scenarios; a fifth handled the four boundary scenarios. It is not a live server or video-quality evaluation. Test agents could read candidate files but could not call external tools, generate media, or mutate files. Skill discovery was simulated from the candidate metadata, not tested against the user's full installed skill catalog. The following excerpts and file records summarize their returned outputs; the pass judgments are the maintainer's assessment, not an automatic grader.

## Scenarios and observed outputs

| Case | Outcome | Observed behavior |
| --- | --- | --- |
| Gemini dialogue | Pass | Preserved the exact spoken line, 8-second portrait format, and one right-hand gesture. Returned a prompt with separate timed dialogue and actions. |
| Seedance montage | Pass | Four shots, three hard cuts, contiguous intervals from 0 to 7 seconds. Explicitly text-only, with no speech or talking-head labels. |
| Research plan | Pass | Proposed research sources and three distinct concepts; labeled concepts as preliminary and performance as unknown. No invented testimonials or researched references. |
| Coding negative | Pass | Did not activate Cospark; returned `const total: number = 3;`. |
| Copy negative | Pass | Did not activate Cospark; returned “Our app makes meal planning easy.” |
| Missing product | Pass | Activated and asked for the product website or a short description. Did not invent a product or require a full brief. |
| Pending run | Pass | Proposed checking `get_ugc_video_status` on the original `abc123`, respecting returned intervals, and checking partial results. No replacement run. |
| Complete ad | Pass | Planned one complete Gemini UGC run, three separate Seedance B-roll jobs, inspection, narration-based edit timing, and a return to presenter. No new approval gate or fabricated completion. |

### Gemini dialogue

Selected files: `SKILL.md`, `gemini-video.md`, `gemini-talking-head.md`, `gemini-examples.md`.

Output excerpts:

> Dialogue [0-6s]: “I used to dread planning dinner. Now I pick my meals in minutes.”
>
> Action [2.8-4.5s]: On “Now,” she makes one small, natural palm-up gesture with her right hand; her left hand stays relaxed and still.

The full response reserved the remaining time for returning the hand and finishing naturally. It did not read B-roll, Seedance, product research, or tool execution instructions. Image content was supplied as a description, so this does not test image inspection.

### Seedance montage

Selected files: `SKILL.md`, `seedance-video.md`, `broll-production.md`, `broll-shot-prompts.md`.

The response assigned breakfast 0–1.75s, smoothie pouring 1.75–3.75s, tacos 3.75–5.25s, and pasta 5.25–7s. Each later shot explicitly began with a hard cut. It ended:

> Generate entirely from text with no reference images.

It did not read Gemini or talking-head guidance. It requested quiet room/pour sounds but no speech, consistent with the brief's no-speech constraint. These timings are requested directions, not measured generation performance.

### Research plan

Selected files: `SKILL.md`, `product-to-ads.md`, `reference-discovery-and-inspection.md`, `product-to-ads-workflow.md`.

The three concepts were “Answer dinner before dinner,” “From saved to supper,” and “Start the list with the meals.” The response proposed direct-competitor, adjacent-product, and filming-style research, then stated:

> These concepts are preliminary hypotheses, not findings from completed research.

It did not read provider prompts or tool execution guidance. It identified a product demo and audience as useful inputs for the next research stage while still completing the requested plan.

### Boundaries

The boundary agent rejected the coding and spelling requests using metadata alone. For the empty ad brief it read `SKILL.md` and `product-to-ads.md`, then asked:

> What’s the product—can you share its website or a short description?

For the pending-run request it additionally read `cospark-tools.md` and proposed polling `abc123`. It explicitly withheld any completion claim pending a returned status. These four cases shared one agent context, so their isolation is weaker than the four independent scenario runs.

### Complete ad

The agent labeled its entire output simulated. It proposed `generate_ugc_video` once with explicit `model: "gemini-omni"`, the entire 63-word script, and the supplied presenter asset. It retained Seedance for three independent four-second B-roll sources, conditional on live schema support. It would poll original IDs, inspect exact dialogue and joins, then place muted food footage above continuous narration and return to the presenter for the ending.

It read `SKILL.md` and 11 references: UGC structure, Gemini video, Gemini talking-head, Gemini examples, Seedance video, Seedance examples, B-roll production, character/frame preparation, reference discovery, Cospark tools, and model capabilities. It skipped product research and native-montage guidance because the script was supplied and the B-roll would be assembled separately.

No user input was considered blocking under the supplied-asset assumption. Live schemas and tools would still need verification in a real execution. The return value was an execution plan, not a finished video.

## Observations and limits

- The dialogue agent noted that the entrypoint makes examples conditional while the talking-head reference specifically directs reading its examples. It followed the more specific direction; this did not load an unrelated workflow.
- The montage agent noted that Seedance version selection is relevant at execution time. It correctly avoided claiming a verified current version for prompt-only work.
- The full-ad case reads more references because it includes production, both models, sourcing, review, and assembly. Short requests loaded only their relevant subsets.
- Paid actions were unavailable in the harness. We assessed proposed actions; we did not demonstrate server-enforced billing or retry behavior.
- No baseline comparison or live media evaluation was run. These checks support the routing change but do not establish better generated videos.
