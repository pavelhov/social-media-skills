# Grok Imagine video in 2026 (verify-quarterly)

This file captures the durable operating reality, not a frozen API table. Model IDs, aliases, prices,
mode caps, preset voices, and rate limits are volatile: verify them against xAI's official video docs and
`tools/integrations/grok-imagine.md` immediately before execution.

## What the current family does
- **Text-to-video:** generates a shot from text. On the current 1.5 generation line, text-to-video creates
  an internal first frame and animates it; the intermediate still is not returned.
- **Image-to-video:** uses a supplied still as frame one and animates it. This is the practical default
  when product shape, typography placement, composition, or brand art direction already exists.
- **Reference-to-video:** uses one or more permitted reference images to guide people, products, clothing,
  props, or style without locking the first frame. Supported preset voices may also guide voice identity.
- **Video editing:** applies a prompted change to supplied footage while attempting to preserve the rest.
  Treat this as a bounded edit, not permission to rewrite everything.
- **Extension:** continues from the source video's last frame. It is useful for a purposeful continuation,
  not a substitute for a shot list.

These are separate modes. Incompatible input types should become separate reviewed requests rather than one
overloaded call.

These documented API capabilities do not establish subscription CLI support; inspect the selected route.

## Subscription CLI frame pins (Grok CLI >= 1.0.34)
As of Grok CLI `1.0.34`, the subscription CLI can pin exact frames on `reference_to_video` / OpenMontage `grok_cli_video`:
- `first_frame` — literal opening frame
- `last_frame` — literal ending frame
- `keyframes` — up to 4 mid-clip `{image, timestamp_s}` anchors (strictly inside the clip)

OpenMontage exposes this as `operation=first_last_frame` (and related aliases) with a minimum-version gate, not an exact pin. Prefer these for dependent continuity joins when the authorized route is CLI subscription. Soft image references and extension remain fallbacks when pins are unavailable or the beat is a hard cut.

Still not CLI-selectable: Imagine Image `2.0` as an explicit model override (`image_gen` still takes prompt/aspect_ratio only). REST may default to Image 2.0 / Video 1.5; do not claim CLI image-model pinning from the API matrix.

## Duration, resolution, audio, and async behavior
- Standard generation accepts **1–15 seconds**. That makes outputs shots, not complete long-form videos.
- The provider currently exposes **480p, 720p, and 1080p where the mode supports them**. Text-to-video and
  image-to-video on the current 1.5 line support native 1080p; reference, edit, and extension constraints may
  differ. Verify the selected mode instead of assuming every combination reaches 1080p.
- Generated video includes an **audio track by default** on the current line; audio can be disabled. Prompt
  dialogue, foley, ambience, and music separately. Reference-to-video can use supported preset voices; custom
  audio reference availability is restricted and must not be promised.
- Rendering is **asynchronous**. A submitted job is not a finished artifact, and a completed URL may be
  temporary. Submission, polling, download/storage, errors, and exact fields belong to the integration guide.

## The quality reality
- One generation is one short shot. A 30–60 second piece needs a script, multiple generated shots, human
  selection, and assembly in an editor.
- Text is not a reliable product-label workflow. Start from a verified brand/product still when exact visual
  fidelity matters, then review every frame where the label is visible.
- References improve direction; they do not guarantee identity, object geometry, or continuity. Keep a
  canonical reference set and compare related shots side by side.
- Editing can change more than requested. State preservation constraints and reject any result that alters
  identity, timing, framing, background, or audio outside the approved change.
- Extension can drift. Continue only a short, simple action; compare the seam for motion, camera, light,
  subject identity, and audio continuity.
- Generated audio is a draft until heard. Check spoken words, speaker identity, synchronization, foley,
  levels, unexpected voices, and music rights.

## Cost control without inventing prices
Cost varies by duration, resolution, mode, and current provider pricing. The practical loop is stable:

1. Lock the mode, aspect ratio, and one-shot storyboard before rendering.
2. If explicitly included in the approved scope, test at a supported lower resolution and useful duration.
3. Change one prompt variable at a time; log the prompt/reference set with each candidate.
4. Final-render only the chosen composition at the required resolution.
5. Follow the approved repair batch, not merely a retry budget. Remaining quota is not permission to reroll.
   Inspect timed-out job state before any retry; preserve completed originals and selected assets.

Never quote a remembered price, model alias, rate limit, reference cap, or voice roster as permanent.
**Verify-quarterly** and verify again before a large batch.

## Rights, consent, and truth
- A reference is not permission. Use real-person likeness, body, performance, or voice only with documented
  consent covering the intended commercial/contextual use.
- Do not create fake endorsements, intimate deepfakes, deceptive impersonation, or photoreal fake-event /
  fake-evidence footage about real people or organizations. “Satire” and disclosure do not cure deception.
- Use permitted source media, logos, characters, and music. For high-stakes commercial/legal questions,
  get qualified review; this skill is not legal advice.
- Disclose material AI generation/editing as required by the platform, jurisdiction, and brand policy.
  Preserve available provenance metadata and never remove disclosure to pass synthetic footage as real.

## Official source of truth
- Video capabilities: https://docs.x.ai/developers/model-capabilities/video/generation
- Image-to-video: https://docs.x.ai/developers/model-capabilities/video/image-to-video
- Reference-to-video: https://docs.x.ai/developers/model-capabilities/video/reference-to-video
- Video editing: https://docs.x.ai/developers/model-capabilities/video/editing
- Video extension: https://docs.x.ai/developers/model-capabilities/video/extension
- Current models/pricing: https://docs.x.ai/developers/models and https://docs.x.ai/developers/pricing

Last reviewed: 2026-09-18. Re-verify quarterly.
