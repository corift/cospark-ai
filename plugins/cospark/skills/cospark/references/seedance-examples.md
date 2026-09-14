# Seedance prompt examples

Adapt these patterns to the user's references, supported model version, duration, and generation interface. Do not copy identities, dialogue, locations, props, or reference numbers that are absent from the request.

Choose the example closest to the task: a beach interaction with several people, a simple product reaction, separate identity and motion references, or a Seedance 2.5 documentary sequence. The lengths and headings are examples, not a required prompt format.

## Reference-driven continuous beach interruption

Adapted from the supplied beach-video example. This shows how to keep several people distinct, give the camera a clear path, and connect each action to a visible reaction.

```text
References
@Image 1: exact opening frame, beach layout, low phone position, and where people and objects start.
@Image 2: Maya's face, hair, green plaid bandana, and swimwear only. Do not copy its pose or background.
@Image 3: George's face and wardrobe only: blond man in his mid-20s wearing a yellow T-shirt, black board shorts, and bare feet.

The scene
8-second, 9:16 vertical live-action phone video. One continuous handheld take with no cuts. Natural amateur beach footage, not a commercial.

Camera
Begin exactly from @Image 1: a low angle beside a towel, with a softly blurred knee in the lower-left foreground, the striped umbrella entering from the upper-right, and the towel and bottle anchored at the lower-right. The camera travels continuously left throughout the clip and never reverses.

What stays consistent
Maya and George retain their assigned identities and wardrobes. George remains seated in the lounger for the entire clip. The running lifeguard is a separate lean, sun-darkened man with wet dark buzzed hair, a soaked gray T-shirt, navy board shorts, and bare feet; he must not resemble George. Nobody carries, steals, drops, or acquires a bag.

Action
0–1.8s: Maya and George are mid-conversation. Maya glances toward the camera with a tiny amused smile, then resumes speaking to George. Wind pushes loose hair across her face. George remains reclined and answers with a relaxed half-smile.

1.8–2.8s: The lifeguard enters rapidly from behind Maya while running left. His shoulder accidentally clips her upper back. The contact is brief and incidental, not an attack. His momentum continues forward as Maya's torso rotates and she loses balance.

2.8–4.6s: Maya catches herself with one palm in the sand, twists back toward the runner with startled annoyance, then starts to rise. The camera pans left with the runner, briefly losing clean framing as he calls an apology over his shoulder. George remains visible behind her in the lounger.

4.6–5.6s: All three overlap spatially for a moment. Wind, running momentum, and Maya's recovery continue naturally; nobody freezes into a pose.

5.6–8s: George pushes himself partly upright and turns after the runner, calling out once. The runner continues away without looking back. Maya rises fully, brushes sand from one hand, and looks after him. The camera keeps moving left and ends imperfectly framed rather than settling into a staged composition.

Movement
The contact shifts Maya's weight before her hand reaches the sand. Her hand compresses the sand and grains move under her palm. The runner keeps genuine forward momentum. Hair, loose fabric, the umbrella edge, and distant flags respond to the same strong crosswind.

How it is filmed
Unstabilized handheld phone footage with restrained shake, slight rolling-shutter skew during the pan, autofocus lag, changing exposure, mild lens flare, and occasional wind-blown hair crossing the lens. Natural skin texture and uneven beach clutter. No beauty filter, glossy commercial grade, slow motion, captions, or cinematic transition.

Sound
Continuous surf, gusting wind across the microphone, distant beach voices, fabric snapping, running footfalls, the soft body contact, and Maya's hand hitting sand. No music. Maya and George's dialogue is foreground but imperfectly captured; the runner's apology becomes more distant as he exits.

Voice
George speaks in a relaxed, clean, natural young adult voice with casual pacing. He never sounds like a narrator, announcer, radio transmission, or voice-over.
```

What to take from this example:

- Each image's contribution is clear.
- The runner is clearly a different person from George.
- The camera has one continuous direction and a physically motivated reason to move.
- Every action produces a visible consequence in the following beat.
- Wind affects image, motion, and audio as one shared environmental force.
- Camera imperfections are tied to the filming conditions.

## Simple image-to-video product reaction

Use fewer sections for a straightforward clip.

```text
@Image 1 is the exact first frame and identity reference.

8-second 9:16 continuous handheld smartphone video. Preserve the woman, kitchen, outfit, and exactly one drink can from @Image 1. She keeps the can in the same right hand throughout.

0–2s: She looks from the can to the lens with a skeptical eyebrow lift and says, “I genuinely thought this was going to taste weird.”
2–5.5s: She takes one small sip, pauses as the surprise registers in her eyes, and gives a restrained approving nod. The phone drifts slightly as though held by a friend.
5.5–8s: She lowers the can to chest height, turns its existing label toward the camera, and says, “Okay, I was wrong.” She finishes with a small amused smile rather than a posed product hold.

Natural kitchen room tone, a quiet sip, and soft clothing movement. No music, captions, added cans, label changes, hand switching, cuts, zooms, or extra dialogue.
```

## Separate identity from motion reference

Use this when a reference video supplies movement but must not overwrite the subject.

```text
References
@Image 1: exact character identity, red track jacket, and opening pose.
@Image 2: nighttime convenience-store location, fluorescent lighting, and color only.
@Video 1: sprint acceleration, low tracking-camera path, and movement rhythm only. Do not copy the runner, wardrobe, background, or audio.

10-second 16:9 live-action continuous tracking shot. The woman from @Image 1 runs through the location from @Image 2. Preserve her face and red jacket throughout.

0–3s: She notices something off-screen right, pivots sharply, and accelerates left. Her planted shoe grips before the trailing foot drives forward. The low camera begins tracking beside her.
3–7s: Match the acceleration and lateral tracking rhythm from @Video 1. Her jacket and ponytail trail the direction changes naturally. Shelves pass with coherent parallax; products remain anchored instead of warping toward the lens.
7–10s: She slows near the exit, catches the door with her left hand, and looks back once while breathing hard. The camera overshoots slightly, corrects, and ends beside her rather than in front of her.

Fluorescent hum, rapid footfalls, clothing movement, the door hinge, and breath synchronized to the action. No music, dialogue, cuts, identity transfer, wardrobe change, duplicated limbs, or copied audio from @Video 1.
```

## Seedance 2.5 documentary sequence

Adapted from the user-supplied Seedance 2.5 / Higgsfield prompt about a summer day in Seoul. The generated output has not been reviewed. This adaptation resolves the original's morning/afternoon and shop restrictions, simplifies crowded actions, and makes the cuts and changes over time explicit. Use the requested 30-second length and 1080p output only if the selected tool supports them; set output options through the tool where available.

```text
Create a 30-second, 1080p personal home video showing small moments from a warm summer afternoon in an older residential neighborhood in Seoul. Use seven shots with simple cuts between them. The cuts skip time during the afternoon; the sequence does not happen in thirty seconds of real time. The footage should feel spontaneous, intimate, and observed by a friend.

Subject and setting
The same young Korean man in his early twenties appears throughout. He has realistic skin texture, messy medium-length dark hair, very subtle stubble, and a relaxed expression. He wears a loose washed-black T-shirt, olive-beige trousers, worn white sneakers, and a simple silver wristwatch. Keep his face, build, hairstyle, clothing, and watch consistent across shots. His hair and clothes become wet during the rain and stay damp afterward.

Narrow concrete alleys, low-rise homes, rooftop terraces, external staircases, potted plants, laundry lines, parked bicycles, overhead wires, and a tiny neighborhood shop. A few residents pass in the distance. Keep the area quiet and lived-in, with no tourist landmarks or prominent branding.

Camera
A friend films with an older consumer digital camera while sitting or walking nearby. Use restrained handheld shake, soft detail, slightly muted colors, and mild digital noise. The operator occasionally frames a little late or takes a moment to find focus. Exposure adjusts when the camera moves between sunlight and shade. Keep movement casual and at human height, without gimbal moves, slow motion, or dramatic lighting.

00:00–00:05 — Rooftop
He sits beside an old plastic chair, looking across the neighborhood. Wind moves his hair and T-shirt. The camera finds focus on his face as he notices his friend, gives a small nod, and looks away with a faint smile.

00:05–00:10 — Alley
Cut to him already walking through a narrow alley with his hands in his pockets. The camera follows several steps behind. He passes potted plants and parked bicycles, then glances back briefly without stopping. The framing drifts as the friend walks.

00:10–00:14 — Basketball
Cut to him near a wall, already holding an old basketball beneath a nearby hoop. He takes one casual shot, misses, and laughs quietly. The ball hits the ground and rolls toward the wall as the camera follows it a little late. Leave it there when the shot ends.

00:14–00:19 — Cold drink
Cut to him outside the neighborhood shop with one newly bought, open bottle. He takes a sip, lowers it, and watches someone cycle past. Keep the bottle in his right hand and clear of his face after the sip. The camera stays nearby, loosely framed.

00:19–00:23 — Rain
Cut to later in the afternoon, with the bottle put away and both hands empty. A summer shower is already falling. He looks up, smiles, and jogs toward a covered walkway. The friend hurries after him. His shirt darkens where the rain hits and his wet hair falls across his forehead. His feet land firmly on the wet concrete.

00:23–00:27 — Shelter
Cut to him beneath the walkway, catching his breath. His shirt and hair remain wet, with heavy rain behind him. He wipes his forehead, looks toward the street, then notices the camera and gives a small, unposed smile. The camera becomes steadier as his friend stops walking.

00:27–00:30 — Walking away
Cut to later, after the rain has eased. He walks away down the wet lane in the same damp clothes, turns his head, and gives a tiny wave. The camera lingers behind him. End abruptly at thirty seconds, as if the recording was stopped, with no fade-out.

Sound
Use only sounds from the scene: distant traffic, birds, wind, footsteps on concrete, the basketball hitting the rim and ground, quiet shop activity, a small laugh, rain, and water dripping from the roof. Match footsteps and impacts to the visible action. Keep street ambience consistent through the early cuts and let rain dominate the later shots. No music, narration, or clearly spoken dialogue.

The feeling comes from the small moments: noticing a friend, missing a shot, taking a break, and getting caught in the rain. Keep expressions understated and allow the camera to observe without anyone deliberately posing.
```

What to take from this example:

- Establish the person and setting once, then write each shot as a short scene.
- Name cuts and skipped time so a change of location or weather is intentional.
- Carry changes forward, including wet clothing and objects being put away.
- Let actions and camera behavior create the mood: a late framing correction or a brief glance can be more useful than another mood adjective.
- Budget each shot for a few readable actions, and describe sound that belongs to those actions.
