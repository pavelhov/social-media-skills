# Scope, safety, distinctions, and connections

## The three-layer boundary
```text
ai-video                         -> chooses the job and preserves a portable brief
grok-imagine                     -> translates it into provider-specific MOTION shot direction
tools/integrations/grok-imagine.md -> current connection, model, request, polling, and download details
```

This skill is the middle craft layer. It writes prompts and operating decisions. It does not render,
edit, download, assemble, schedule, publish, or measure video.

## Honest execution chain
```text
ai-video -> grok-imagine brief -> external render -> human picture-and-sound review
-> human assembly/captions -> scheduling-and-queue -> WoopSocial
```

- The rendering provider creates individual clips asynchronously.
- A human judges every returned clip and assembles multi-shot work. Never report “the render works” without
  inspecting the artifact.
- **WoopSocial only schedules/publishes** the approved finished export; it does not generate or edit media
  and exposes no analytics. (measurement: the platforms' native analytics).
- Scheduling, publishing, changing, or deleting always requires explicit user confirmation.

## Safety and rights gate
- **Likeness, performance, and voice:** documented permission for the person, source, intended audience,
  context, and commercial use. A public photo or voice clip is not permission.
- **No deceptive synthetic media:** refuse fake endorsements, intimate deepfakes, impersonation, and
  realistic fake-event/fake-evidence footage about real people or organizations. Do not offer a lookalike,
  “parody,” or disclosure workaround.
- **Source rights:** use owned/licensed/permitted images, video, logos, characters, audio, and music.
- **Claims:** synthetic demonstrations must not invent product behavior or customer outcomes. Label
  conceptual visuals when a viewer could mistake them for evidence.
- **Disclosure and provenance:** plan visible/platform metadata disclosure where required; preserve available
  provenance metadata. Disclosure is necessary but does not make a deceptive artifact acceptable.

## Distinct from sibling skills
- **ai-video:** router and vendor-neutral master brief. Read it first.
- **veo-3:** sibling for generated scenes where its current all-round/audio fit wins; compare on the actual
  brief rather than a remembered leaderboard.
- **runway:** sibling for control-led editing, references, and production pipelines.
- **kling:** sibling for its current multi-shot and motion-led workflows.
- **luma:** sibling for cinematic mood/HDR workflows.
- **heygen / synthesia:** avatar presenters and localization, not a generated cinematic scene.
- **image-prompt / flux / nano-banana:** create permitted, brand-true stills that can become image-to-video
  first frames or reference inputs.
- **capcut / descript / captions-and-clipping:** assembly, finishing, and captions after human approval.

Provider strengths and limits change. Route via ai-video, test a representative shot, and mark comparative
claims **verify-quarterly**.

## Human review checklist
- **Picture:** subject and product fidelity; identity/wardrobe/prop continuity; hands, faces, geometry, text;
  action order; camera coherence; edit/extension preservation; unwanted content.
- **Sound:** exact dialogue; speaker/voice permission; sync; unexpected words/voices; foley; ambience; music
  rights and levels.
- **Context:** no invented claim or fake evidence; brand fit; disclosure; provenance; destination-platform
  suitability.
- **Sequence:** side-by-side drift check, seam check, pacing, captions, mix, and final export validation.

## Never claim
- That this skill itself generated, edited, downloaded, or published a clip.
- That a submitted async job completed successfully before the artifact is returned and reviewed.
- That references guarantee identity/brand fidelity, editing preserves everything, or extension is seamless.
- That remembered model IDs, prices, caps, voices, or quality rankings are current.
- That WoopSocial generated/edited the asset or measured its performance.
