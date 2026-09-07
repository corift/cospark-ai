# Seedance prompt examples

Adapt these patterns to the user's references, supported model version, duration, and generation interface. Do not copy identities, dialogue, locations, props, or reference numbers that are absent from the request.

## Reference-driven continuous beach interruption

This is the reusable structure distilled from the supplied beach-video example: narrow reference roles, a persistent one-way camera path, explicit identity separation, timecoded cause and effect, physical consequences, captured-phone imperfections, and layered audio.

```text
REFERENCES
@Image 1: exact opening frame, beach layout, low phone position, and initial blocking.
@Image 2: Maya's face, hair, green plaid bandana, and swimwear only. Do not copy its pose or background.
@Image 3: George's face and wardrobe only: blond man in his mid-20s wearing a yellow T-shirt, black board shorts, and bare feet.

FORMAT
8-second, 9:16 vertical live-action phone video. One continuous handheld take with no cuts. Natural amateur beach footage, not a commercial.

OPENING FRAME
Begin exactly from @Image 1: a low angle beside a towel, with a softly blurred knee in the lower-left foreground, the striped umbrella entering from the upper-right, and the towel and bottle anchored at the lower-right. The camera travels continuously left throughout the clip and never reverses.

CONTINUITY LOCKS
Maya and George retain their assigned identities and wardrobes. George remains seated in the lounger for the entire clip. The running lifeguard is a separate lean, sun-darkened man with wet dark buzzed hair, a soaked gray T-shirt, navy board shorts, and bare feet; he must not resemble George. Nobody carries, steals, drops, or acquires a bag.

TIMELINE
0–1.8s: Maya and George are mid-conversation. Maya glances toward the camera with a tiny amused smile, then resumes speaking to George. Wind pushes loose hair across her face. George remains reclined and answers with a relaxed half-smile.

1.8–2.8s: The lifeguard enters rapidly from behind Maya while running left. His shoulder accidentally clips her upper back. The contact is brief and incidental, not an attack. His momentum continues forward as Maya's torso rotates and she loses balance.

2.8–4.6s: Maya catches herself with one palm in the sand, twists back toward the runner with startled annoyance, then starts to rise. The camera pans left with the runner, briefly losing clean framing as he calls an apology over his shoulder. George remains visible behind her in the lounger.

4.6–5.6s: All three overlap spatially for a moment. Wind, running momentum, and Maya's recovery continue naturally; nobody freezes into a pose.

5.6–8s: George pushes himself partly upright and turns after the runner, calling out once. The runner continues away without looking back. Maya rises fully, brushes sand from one hand, and looks after him. The camera keeps moving left and ends imperfectly framed rather than settling into a staged composition.

PHYSICS
The contact shifts Maya's weight before her hand reaches the sand. Her hand compresses the sand and grains move under her palm. The runner keeps genuine forward momentum. Hair, loose fabric, the umbrella edge, and distant flags respond to the same strong crosswind.

REALISM
Unstabilized handheld phone footage with restrained shake, slight rolling-shutter skew during the pan, autofocus lag, changing exposure, mild lens flare, and occasional wind-blown hair crossing the lens. Natural skin texture and uneven beach clutter. No beauty filter, glossy commercial grade, slow motion, captions, or cinematic transition.

AUDIO
Continuous surf, gusting wind across the microphone, distant beach voices, fabric snapping, running footfalls, the soft body contact, and Maya's hand hitting sand. No music. Maya and George's dialogue is foreground but imperfectly captured; the runner's apology becomes more distant as he exits.

VOICE
George speaks in a relaxed, clean, natural young adult voice with casual pacing. He never sounds like a narrator, announcer, radio transmission, or voice-over.
```

Why it works:

- Each image owns a narrow visual role.
- The incidental runner is explicitly separated from George.
- The camera has one continuous direction and a physically motivated reason to move.
- Every action produces a visible consequence in the following beat.
- Wind affects image, motion, and audio as one shared environmental force.
- The realism cues describe imperfect capture rather than lowering image quality generically.

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
REFERENCES
@Image 1: exact character identity, red track jacket, and opening pose.
@Image 2: nighttime convenience-store location, fluorescent lighting, and color only.
@Video 1: sprint acceleration, low tracking-camera path, and movement rhythm only. Do not copy the runner, wardrobe, background, or audio.

10-second 16:9 live-action continuous tracking shot. The woman from @Image 1 runs through the location from @Image 2. Preserve her face and red jacket throughout.

0–3s: She notices something off-screen right, pivots sharply, and accelerates left. Her planted shoe grips before the trailing foot drives forward. The low camera begins tracking beside her.
3–7s: Match the acceleration and lateral tracking rhythm from @Video 1. Her jacket and ponytail trail the direction changes naturally. Shelves pass with coherent parallax; products remain anchored instead of warping toward the lens.
7–10s: She slows near the exit, catches the door with her left hand, and looks back once while breathing hard. The camera overshoots slightly, corrects, and ends beside her rather than in front of her.

Fluorescent hum, rapid footfalls, clothing movement, the door hinge, and breath synchronized to the action. No music, dialogue, cuts, identity transfer, wardrobe change, duplicated limbs, or copied audio from @Video 1.
```
