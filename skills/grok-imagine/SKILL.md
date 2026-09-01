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

## The framework: MOTION
(Depth: `references/the-motion-framework.md`.)
- **M — Match the mode:** text-to-video for invention; image-to-video for a fixed first frame;
  reference-to-video for identity/object/style guidance without fixing frame one; edit for a bounded
  change to footage; extend to continue from the last frame.
- **O — Make it observable:** name the subject, visible action, setting, and end state. Replace abstract
  intent with behavior the camera can record.
- **T — Time the beats:** order events across the 1–15 second generation window; keep one shot and one
  action arc per request.
- **I — Instruct one camera idea:** choose one primary move and compatible framing, lens feel, light,
  and aspect ratio. Contradictory camera instructions create drift.
- **O — Orchestrate audio:** specify dialogue exactly, then foley, ambience, and music—or request a
  silent result. Generated clips include audio by default on the current model family.
- **N — Nail constraints and review:** bind each reference to its job; state what edits must preserve;
  test short/low-resolution first, final-render only the winner, then review picture and sound.

## Pick the mode before writing the prompt
| Need | Mode | Direction that matters |
|---|---|---|
| Invent a shot from words | Text-to-video | Subject, action, setting, timed beats, camera, audio |
| Animate a designed or product still | Image-to-video | Treat the image as frame one; describe motion, not a new composition |
| Carry a person, product, garment, or style into a new shot | Reference-to-video | Label each reference and say what it controls; it does not lock the first frame |
| Change existing footage | Video editing | State the smallest requested change plus explicit preservation constraints |
| Continue an existing clip | Extension | Continue motion, camera direction, light, ambience, and continuity from the last frame |

Do not combine incompatible modes in one request. If the job needs both an edit and an extension, make
them separate reviewed generations. Exact request fields, current model IDs, caps, auth, and async polling
belong in `tools/integrations/grok-imagine.md`.

## The current reality (verify-quarterly)
The current Grok Imagine video family supports text-to-video, image-to-video, reference-to-video,
video editing, and extension. Standard generation accepts **1–15 seconds** and common social aspect
ratios; 480p, 720p, and 1080p are available where the selected mode supports them. Audio is generated
by default and can be disabled; reference mode can use supported preset voices. Rendering is
asynchronous. Mode-specific resolution/duration limits, model aliases, pricing, rate limits, and voice
availability change—verify them in the official xAI docs and the integration guide before execution.
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
