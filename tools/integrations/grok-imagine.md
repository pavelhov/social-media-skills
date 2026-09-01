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

## Authentication and side-effect gate

- Create an xAI API key and expose it as `XAI_API_KEY`. Send it only as a bearer token to
  `https://api.x.ai`; never print it, commit it, put it in a prompt, expose it client-side, or read
  credentials from another tool's auth files.
- **Get explicit user confirmation before every paid or quota-consuming render.** Show the final
  prompt, model, mode, duration, aspect ratio, resolution, number of variations, and estimated cost
  first. Approval of a brief is not approval to submit a render.
- A completed render is still a draft. Review it for quality, rights, safety, and disclosure before
  any publishing step. Publishing, scheduling, and deletion each require their own explicit user
  confirmation.

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
Use the direct API or official SDK when a machine-readable request ID, stable polling, and reliable
artifact persistence matter.

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
