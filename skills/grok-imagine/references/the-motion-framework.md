# The MOTION framework — direct a Grok Imagine shot that moves and sounds intentional

Grok Imagine prompts work best as short production plans. MOTION keeps the brief concrete enough to
direct while leaving the model one coherent shot to solve. Run every shot through all six gates.

## M — Match the mode
Choose the input contract before writing prose:

- **Text-to-video:** invent the first frame and motion from words. Use for scenes where no source visual
  must be preserved.
- **Image-to-video:** the supplied image is the starting frame. Direct what moves, what stays visually
  stable, and how the camera behaves; do not redescribe a conflicting composition.
- **Reference-to-video:** references guide people, products, clothing, props, or style without becoming
  the required first frame. Label references explicitly and assign each one a job.
- **Video editing:** start from existing footage and request a bounded change. Say what changes and what
  must not change.
- **Extension:** continue from the source video's final frame. Preserve trajectory, screen direction,
  camera energy, lighting, and audio bed unless the transition is deliberate.

One request gets one mode. A pipeline may use several modes, but each output is reviewed before becoming
the next input.

## O — Make it observable
Describe what the audience will literally see:

> [specific subject] [visible action] in [concrete setting], ending with [visible end state].

Replace “feels innovative” with observable direction: “the translucent display unfolds from the device
and the camera reveals the completed dashboard.” Give the subject physical attributes that matter to
identity or brand fit. Avoid long lists of aesthetics that do not change the image.

## T — Time the beats
Write events in chronological order. For a 10-second clip, a useful pattern is:

- **0–2s:** establish subject and hook motion.
- **2–7s:** primary action develops.
- **7–10s:** resolve to a usable end pose or transition frame.

Use the actual requested duration and do not crowd three scenes into one shot. Dialogue must fit the
available time when spoken naturally. If the story needs cuts, split it into separate shot briefs for
human assembly.

## I — Instruct one camera idea
Pick one primary idea—locked-off, slow push-in, lateral track, orbit, handheld follow, crane reveal—and
keep the rest compatible. Add only production details that help:

- framing and aspect ratio;
- lens feel or depth of field;
- lighting/time and palette;
- whether motion should feel smooth, urgent, restrained, or documentary.

Do not ask for “locked camera, sweeping orbit, handheld shake.” When the subject motion is complex,
simplify camera motion. When the camera move is the hero, simplify the subject action.

## O — Orchestrate audio
The current model family generates an audio track by default. Direct it as deliberately as the image:

- **Dialogue:** quote the exact line and identify the speaker. Keep the line short enough for the shot.
- **Foley:** name the events that should synchronize—ceramic set on wood, jacket rustle, latch click.
- **Ambience:** define the continuous bed—quiet kitchen room tone, rain on glass, distant traffic.
- **Music:** state role and energy, not an imitation of a living artist; use properly licensed music in
  post when exact brand music matters.
- **Silence:** request audio off when the clip will be scored or voiced in post.

Review generated dialogue for accuracy, intelligibility, identity, and unintended speech. Preset or
referenced voices never substitute for permission to imitate a real person.

## N — Nail constraints and review
Close the brief with control and an iteration plan:

- Bind references: “Reference 1 controls the product shape and label; Reference 2 controls palette only.”
- For edits: “Change the jacket to navy; preserve face, body motion, timing, framing, background, and audio.”
- For extension: “Continue the same left-to-right walk and dolly speed; preserve dusk light and rain bed.”
- If approved, test short at a supported lower resolution. Each new render consumes quota; an approved
  first-pass budget does not authorize corrective iteration. Use the disclosed repair batch allowance.
- Before animation inspect actual keyframe geometry and prop ownership. Remove copied constraints for
  absent characters/props. Check adjacent shot states and simplify competing motion requirements.
- Record sampled visual checks and ASR as partial evidence; neither proves full audiovisual correctness.
- Human-review picture and sound: brand/identity, geometry, hands, readable text, motion continuity,
  unwanted edits, dialogue, foley sync, artifacts, rights, claims, and disclosure.

## MOTION brief card
```text
MODE: text | image-first | references | edit | extend
OBSERVABLE: subject + visible action + setting + end state
TIMING: ordered beats within the chosen duration
IDEA: one camera move + framing + light/palette + aspect ratio
AUDIO: exact dialogue + foley + ambience + music role | silent
NAIL: reference roles + preservation constraints + draft/final plan + review/disclosure
```
