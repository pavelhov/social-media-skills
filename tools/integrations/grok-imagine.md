# Grok Imagine (xAI video) — integration guide

The canonical connection guide for the `grok-imagine` mini-skill. Grok Imagine renders video;
`ai-video` routes the job and writes the portable brief; a human reviews and assembles the result;
the finished file publishes through `scheduling-and-queue → WoopSocial`.

> **Verify quarterly.** Model IDs, mode support, pricing, limits, and CLI commands change. Treat
> xAI's official docs as the source of truth:
> `https://docs.x.ai/developers/model-capabilities/video/generation`, the related mode pages,
> `https://docs.x.ai/developers/models/grok-imagine-video-1.5`,
> `https://docs.x.ai/developers/rest-api-reference/inference/videos`, and
> `https://docs.x.ai/build/modes-and-commands`.

## Select the authorized execution route first

Read the user's route, budget and account rules before selecting a connection. A subscription-backed
Grok CLI workflow and the paid xAI API are separate authorization and capability contracts.

- **Subscription CLI selected:** use the existing authenticated CLI through the approved local adapter.
  Inspect its supported operations, parameters, installed version and returned receipts. Do not create
  an API key, call paid API endpoints or substitute a provider without authorization. API model names,
  preset voices, audio switches, editing/extension, durations and resolutions below do not establish
  CLI support. Record the actual observed model identifier, or unknown; do not relabel an endpoint.
- **API selected:** use the API/SDK instructions and verified API pricing below.
- **Cost:** subscription access does not mean unlimited or free media. If media cost is not exposed,
  report it as unknown and disclose call counts/quotas. Coding-agent session dollar totals are not
  media charges. Never use API per-second prices as a subscription CLI quote.
- A request for reliability or better quality does not authorize switching billing routes.

## Authentication and side-effect gate

- For an authorized API workflow, create an xAI API key and expose it as `XAI_API_KEY`. Send it only as a bearer token to
  `https://api.x.ai`; never print it, commit it, put it in a prompt, expose it client-side, or read
  credentials from another tool's auth files.
- **Obtain approval for a concrete generation scope or bounded batch before spending quota.** Disclose
  route, shot/action plan, mode, duration, aspect ratio, resolution, planned calls and known/unknown
  media cost. A full-run approval covers its disclosed first-pass calls; do not ask again per call.
  Follow stricter account repair rules. A spending ceiling alone never authorizes corrective rerolls.
  Before corrective generation, disclose affected shots, preserved assets, method and attempt allowance
  and obtain approval unless that exact repair batch is already approved. Do not expand scope or
  change provider/billing route silently. Preserve originals and successful selected shots.
- A completed render is still a draft. Record separate technical, visual, audio and story checks;
  complete synchronized review of the selected master is required for full audiovisual claims. Unknown
  or failed critical checks cannot become a pass after more review rounds. Review rights and disclosure
  before any publishing step. Publishing, scheduling, and deletion each require their own explicit user
  confirmation.

## Story readiness and role-preserving control mapping

Before mapping a shot into the selected adapter, require a causal script (desire → action → consequence
→ visible payoff), completed local shot states, explicit cast/speakers and payoff/late-cast board review.
An opening board alone is insufficient. Wrong, missing, unknown or stale critical cast/action,
speaker/source, possession or payoff evidence blocks motion; a numeric allowance or review-round ceiling
cannot waive it. A wrong still cannot be repaired by stronger negative motion wording.

Plan and review local start and completed-end boards. That does not universally require submitting
an endpoint pin; the approved method decides required execution controls. Carry separate bindings for
identity references, start composition, the shot's local end target and
supported timed keyframes. Record intended roles, input hashes and actually submitted controls; same
bytes do not collapse separate roles. Verify the installed CLI adapter's supported operations and
combinations. Do not apply the API matrix below to the CLI, invent a media-model ID, silently drop a
required endpoint/control, or describe a prompt-only request as pinned. An unsupported required binding
must fail before launch and be resolved within the authorized route/scope.

Use explicit `continuous`, `hard_cut`, `match_cut` or `transformation` transitions. An exterior
entry ends with completed traversal; a deliberate interior cut has its own start composition. Never
bind the following storyboard as the current ending automatically. Bind dependent shots to the selected
upstream attempt/output hash and observed outgoing frame/action evidence; changed bytes or selections
require fresh dependent review. Identity anchors describe design, not observed continuity.

The complete portable directing method is in
`skills/grok-imagine/references/shot-continuity-and-control-roles.md`; the script/brief owners are
`short-form-video-script` and `ai-video`. These labels describe control purposes, not new provider
fields. Keep route-aware receipts and selected/rejected attempt evidence; reconcile a timed-out job
using its original job/session identity before considering any new attempt. File existence or size
alone is not permission to reuse or retry.

## Connection options

### 1. Direct xAI API or official Python SDK — automation lane

Use the direct API for repeatable integrations. Video jobs are asynchronous:

1. `POST /v1/videos/generations`, `/v1/videos/edits`, or `/v1/videos/extensions`.
2. Capture the returned `request_id`.
3. Poll `GET /v1/videos/{request_id}` until `done`, `failed`, or `expired`.
4. When `done`, verify `respect_moderation`, download the MP4 immediately, and persist the job
   metadata alongside it.

The official `xai_sdk` Python client exposes `client.video.generate(...)` and
`client.video.extend(...)`; the convenience methods perform polling and return the completed
response. Use `start()` / `extend_start()` plus `get()` when the caller needs explicit timeouts,
poll intervals, cancellation, or durable job-state handling. Handle terminal failures and timeouts;
never retry blindly in a way that can spend credits twice.

This API/SDK path is the deterministic choice for scripted submit → poll → download workflows.

### 2. Grok Build CLI — interactive convenience lane

Grok Build's interactive TUI exposes:

```text
grok
/imagine-video <prompt>
```

The CLI also supports agent-driven headless sessions with `grok -p "..."`. That is useful for
interactive or supervised convenience, but it is not the same contract as calling the video API:
the agent chooses actions, and its output is less deterministic for submit/poll/download
automation. The documented CLI has **no top-level `grok video ...` subcommand**; do not invent one.
For an authorized API workflow, prefer the direct API or official SDK when machine-readable job IDs
and polling are needed. A subscription-only lock takes precedence: use and validate the approved CLI
adapter, surface its limitations, and never switch to paid API automatically.

## Models and capability matrix (verify-quarterly)

| Mode | Model / endpoint | Current useful limits |
|---|---|---|
| Text-to-video | **grok-imagine-video-1.5** via `/v1/videos/generations` | 1–15s; 480p/720p/1080p; native audio by default; configurable aspect ratio |
| Image-to-video | **grok-imagine-video-1.5** via `/v1/videos/generations` with `image` | Source image becomes the starting frame; 1–15s; up to 1080p |
| Reference-to-video | **grok-imagine-video-1.5** with `reference_images` and/or `reference_audios` | Up to 7 reference images and 3 preset voices; up to 15s; capped at 720p |
| Video editing | **grok-imagine-video** via `/v1/videos/edits` | MP4 input up to 8.7s; preserves duration/aspect; output matches input resolution up to 720p |
| Video extension | **grok-imagine-video** via `/v1/videos/extensions` | MP4 input 2–15s; adds 2–10s; preserves aspect/resolution; output capped at 720p |

Supported generation aspect ratios currently include `1:1`, `16:9`, `9:16`, `4:3`, `3:4`,
`3:2`, and `2:3`. Image-to-video defaults to the input ratio; overriding it can stretch the image.
Editing and extension do not accept custom aspect ratio or resolution.

Generated videos include audio by default on **grok-imagine-video-1.5**; request silent output with
`generate_audio: false`. Reference-to-video can select preset voices by `voice_id`. Custom voice
audio is restricted to trusted partners on request, so do not promise arbitrary voice cloning or
upload a person's voice without documented consent.

Only one request mode can be active. In particular, do not combine `image` with
`reference_images`, or combine reference-to-video with image-to-video, editing, or extension.

## Cost and artifact persistence

**Approximate API output pricing, verify-quarterly:** **grok-imagine-video-1.5** is currently about
$0.08/sec at 480p, $0.14/sec at 720p, and $0.25/sec at 1080p, plus applicable media-input charges.
Estimate the whole request before confirmation: duration × resolution rate × variations, plus
inputs. Prefer short 480p/720p tests before an approved master render.

Completed jobs normally return an xAI-hosted **temporary URL**. Download promptly if the artifact
must survive. Where persistent xAI storage is appropriate, use the documented Files API
`storage_options` and retain the returned `file_id`; request a public URL only when sharing is
actually required, and treat it as a disclosure surface. Never treat a temporary output URL as an
archive.

## Safety, rights, disclosure, and provenance

- Use only owned or licensed source media and consented likenesses, performances, and voices. Do
  not create deceptive impersonation, fabricated real-event footage, or fake testimonials.
- Respect provider moderation. A filtered or `respect_moderation: false` result is not a candidate
  for publishing or a reason to weaken safeguards.
- Disclose synthetic or materially altered video wherever platform rules, law, or brand policy
  require it. Preserve prompts, source permissions, model/mode, generation date, and edit history as
  provenance; do not claim an embedded watermark or C2PA signal unless the exported file is checked.
- Do not put secrets, personal data, confidential client material, or unlicensed assets in prompts
  or references.

## Publish handoff

Grok Imagine only generates or modifies the asset. After human review and editing, pass the
finished file to `scheduling-and-queue`, which follows `tools/integrations/woopsocial.md` for media
upload, validation, and publish/schedule operations. WoopSocial is publish-only: it does not
generate or edit video, and it has no analytics surface (measurement: the platforms' native
analytics). Nothing is scheduled, published, or deleted without explicit user confirmation.

## Related

Mini-skill: `grok-imagine`. Router: `ai-video`. Sibling guides:
`tools/integrations/veo.md`, `tools/integrations/kling.md`, `tools/integrations/luma.md`,
`tools/integrations/runway.md`, `tools/integrations/heygen.md`, and
`tools/integrations/synthesia.md`. Publish bridge: `tools/integrations/woopsocial.md`.
