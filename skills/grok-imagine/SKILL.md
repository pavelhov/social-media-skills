---
name: grok-imagine
description: >-
  The Grok Imagine video craft skill — direct short generated shots with native audio across
  text-to-video, image-to-video, reference-to-video, video editing, and extension. Use when someone
  names Grok Imagine / xAI video, wants a Grok-native video prompt, wants to animate a still without
  losing its composition, guide a shot with people/product/style references, make a bounded change
  to existing footage, extend a clip, or plan synchronized dialogue/foley/ambience. Uses the MOTION
  framework. This skill writes provider-specific briefs; it does not render, edit, or publish media.
  Below ai-video, sibling to veo-3, kling, luma, and runway. An external renderer creates clips, a
  human reviews/assembles them, and WoopSocial only schedules/publishes. Consented references and
  voices only; never create deceptive deepfakes or fake-event footage; disclose synthetic media.
version: 1.0.0
---

# grok-imagine

The **Grok Imagine short-shot director** under **ai-video**. It turns a portable video brief into a
Grok-native prompt and mode plan. It does not call a renderer itself: an external render step creates
the clip, a human reviews and assembles it, and WoopSocial only schedules/publishes the finished file.

## The POV: direct what can be seen and heard
Grok Imagine is useful when one short shot needs **motion plus sound**, or when the source itself
should direct the result: a first-frame image, a set of visual references, existing footage, or the
end of a clip. The winning prompt is not a bag of adjectives. It is a tiny production plan: one
visible action, one coherent camera idea, chronological beats, an explicit audio scene, and clear
preservation constraints. For a sequence, write one brief per shot and assemble after rendering.

## Read these first
1. **ai-video** — confirm that Grok Imagine fits the job and preserve a vendor-neutral master brief.
2. **brand-profile** — visual identity, audience, and non-negotiables.
3. **short-form-video-script** or **scripting-and-storyboarding** — when the request spans multiple shots.

## Workflow authority and evidence

User and account constraints govern route, music, captions, runtime and generation consent. Confirm
subscription CLI versus paid API first; the API capability matrix is not a CLI capability guarantee.
Inspect the actual keyframe before animation: performer, pose, contact geometry, opening/obstacle,
prop ownership and background must support the requested action. Reject an inconsistent starting
state before spending video quota; extra negative instructions cannot repair its geometry.

For each shot, remove template instructions about absent characters, clothing and props. Check
starting state → one dominant action → required end state against neighboring shots. Avoid large
motion verbs paired with immobility requirements; stage the intended small movement explicitly.
A reference guides generation; it does not guarantee physical constraints or identity persistence.

Approve planned tests/first passes as a bounded scope. No autonomous corrective rerolls; follow the
account's repair approval rules and preserve originals. After a timeout, inspect job/artifact state
before considering a retry. A budget ceiling is not permission to regenerate.

Separate technical export checks from semantic readiness. Record checks actually performed and
pass/fail/unknown evidence. Contact sheets establish sampled visual evidence; ASR is tentative text,
not proof of exact words, speaker ownership, lip sync, prosody or absence of music. Full audiovisual
claims require actual synchronized review. Unknown/failed essential checks remain review drafts.

## The framework: MOTION
(Depth: `references/the-motion-framework.md`.)
- **M — Match the mode:** text-to-video for invention; image-to-video for a fixed first frame;
  reference-to-video for identity/object/style guidance (and, on CLI `>=1.0.34`, optional literal
  `first_frame`/`last_frame`/`keyframes`); first/last-frame continuity for dependent joins when the
  selected CLI route supports pins; edit for a bounded change to footage; extend to continue from
  the last frame.
- **O — Make it observable:** name the subject, visible action, setting, and end state. Replace abstract
  intent with behavior the camera can record.
- **T — Time the beats:** order events across the 1–15 second generation window; keep one shot and one
  action arc per request.
- **I — Instruct one camera idea:** choose one primary move and compatible framing, lens feel, light,
  and aspect ratio. Contradictory camera instructions create drift.
- **O — Orchestrate audio:** specify dialogue exactly, then foley, ambience, and music—or request a
  silent result. Generated clips include audio by default on the current model family.
- **N — Nail constraints and review:** bind each reference to its job; state what edits must preserve;
  use only approved tests/first passes and repair batches, then review picture and sound.

## Pick the mode before writing the prompt
| Need | Mode | Direction that matters |
|---|---|---|
| Invent a shot from words | Text-to-video | Subject, action, setting, timed beats, camera, audio |
| Animate a designed or product still | Image-to-video | Treat the image as frame one; describe motion, not a new composition |
| Carry a person, product, garment, or style into a new shot | Reference-to-video | Label each reference and say what it controls; style refs alone do not lock frame one |
| Pin exact opening/ending (and optional mid beats) on CLI >=1.0.34 | First/last-frame / keyframes via reference-to-video | Use local `first_frame`/`last_frame` and up to 4 `{image,timestamp_s}` keyframes; inspect stills first |
| Change existing footage | Video editing | State the smallest requested change plus explicit preservation constraints |
| Continue an existing clip | Extension | Continue motion, camera direction, light, ambience, and continuity from the last frame |

Do not combine incompatible modes in one request. If the job needs both an edit and an extension, make
them separate reviewed generations. Exact request fields, current model IDs, caps, auth, and async polling
belong in `tools/integrations/grok-imagine.md`.

## The current reality (verify-quarterly)
The current Grok Imagine video family supports text-to-video, image-to-video, reference-to-video,
video editing, and extension. On subscription CLI `>= 1.0.34`, reference-to-video also exposes native
`first_frame` / `last_frame` / up to 4 mid-clip `keyframes` (OpenMontage: `first_last_frame`). The API
capability matrix is still not a CLI guarantee—confirm route + CLI version before promising pins.
CLI still cannot select Imagine Image 2.0 as a model override. The documented API generation contract
accepts **1–15 seconds** and common social aspect ratios; 480p, 720p, and 1080p are available where the
selected mode supports them. Audio is generated by default and can be disabled; reference mode can use
supported preset voices. Rendering is asynchronous. Mode-specific resolution/duration limits, model
aliases, pricing, rate limits, and voice availability change—verify them in the official xAI docs and
the integration guide before execution.
Full capability notes: `references/grok-imagine-2026-reality.md`. Working prompts:
`references/recipes-and-templates.md`.

## Consent, truth, and provenance (hard gate)
- Use real-person face, body, performance, voice, or identifiable references only with documented
  permission for the intended use. Never build a fake endorsement, sexualized deepfake, or deceptive
  impersonation; do not offer lookalike workarounds.
- Do not create photoreal fake-event or fake-evidence footage about real people or organizations.
  Disclosure does not make deception safe.
- Use only owned, licensed, or otherwise permitted source images, video, logos, music, and characters.
- Plan clear synthetic-media disclosure and preserve available provenance metadata. A human reviews
  the final picture, audio, claims, and context before publishing.

## Honest scope (never violate)
- **This skill writes briefs and prompts; it does not generate or edit video.** Rendering happens in
  an external tool through the connection described in `tools/integrations/grok-imagine.md`.
- **A human reviews every render** for subject/brand fidelity, temporal logic, hands/text, unwanted
  changes, dialogue intelligibility, audio artifacts, and disclosure; a human assembles multi-shot work.
- **WoopSocial only schedules/publishes** the approved export; it has no generation, editing, or analytics
  surface. (measurement: the platforms' native analytics).
- Never claim a render succeeded without inspecting the returned artifact. Never fabricate pricing,
  limits, quality rankings, rights, or performance metrics. Mark volatile details **verify-quarterly**.
- Nothing is scheduled, published, changed, or deleted without explicit user confirmation.

## Where this connects
Router: **ai-video**. Siblings: **veo-3** (all-round generated scenes/audio), **runway** (control-led
editing and consistency), **kling** (multi-shot/motion workflows), **luma** (cinematic mood/HDR), and
**heygen / synthesia** (avatar presenters). Inputs: **image-prompt / flux / nano-banana** for permitted
reference stills. Assembly: **capcut** or **descript**; captions: **captions-and-clipping**. Finished
clips feed **reels-script**, **tiktok-script**, **youtube-shorts**, and
**cross-platform-repurposing**. Publish only through **scheduling-and-queue → WoopSocial**.

## Definition of done
A vendor-neutral brief has been routed through ai-video; the correct Grok Imagine mode is selected;
the prompt follows MOTION with observable action, ordered beats, one camera idea, explicit audio, and
mode-appropriate references/preservation constraints; duration, aspect ratio, and draft/final settings
fit the deliverable and current provider limits; any likeness, voice, source-media, and brand rights are
cleared; deceptive synthetic footage is refused; disclosure/provenance and human picture-plus-sound
review are planned; multi-shot work ends in human assembly; publishing routes through
scheduling-and-queue to WoopSocial only after confirmation; no render, metric, price, or capability is
fabricated.
