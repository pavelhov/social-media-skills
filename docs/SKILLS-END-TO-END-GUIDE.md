# Social Media Skills: end-to-end guide

This is the practical companion to the repository [README](../README.md): how to go from an
empty brand folder to a reviewed campaign, then safely schedule it and learn from native
platform analytics. The repository contains **106 Agent Skills**. Each skill is a folder with a
`SKILL.md` routing contract, supporting `references/`, and `evals/evals.json`.

The short version is:

```text
install skills → create one folder per brand → establish brand + voice → strategy + pillars
→ calendar + campaign briefs → write + produce → validate → preview → explicit confirmation
→ publish/schedule → measure in native analytics → audit, test, recycle
```

## 1. Before you start

You need:

- An AI agent that can load [Agent Skills](https://agentskills.io), or Claude's custom-skills
  upload UI.
- A dedicated working folder for each brand. The durable brand files live in that folder, not
  in this library.
- Node.js with `npx` for the recommended Skills CLI or SkillKit installation path; or Git and a
  filesystem-based skill loader for manual installation.
- Optional publishing: a WoopSocial account and an MCP-capable agent. Publishing/API access is
  plan-dependent; use the live [WoopSocial guide](../tools/integrations/woopsocial.md) rather
  than copying connection or platform-limit details into project notes.
- Optional maintainer tooling: Bash, Python 3, and `zip` to validate the repository and build
  uploadable ZIPs/packs.

Two folders have different jobs:

- **Library checkout:** this repository, containing reusable skills and integration guides.
- **Brand workspace:** a clean folder holding `brand-profile.md`, usually `voice.md`, and that
  brand's strategy, calendar, drafts, media, and reporting inputs.

Keep brands isolated. Do not use one shared working folder for multiple clients or brands.

## 2. Install from an empty folder

Choose one installation path. The first is the repository's recommended path.

### Option A — Skills CLI (recommended)

Run this from an empty brand folder or anywhere else; `-g` makes the install global for the
selected agent:

```bash
mkdir my-brand
cd my-brand
npx skills add social-media-skills/skills -g -a claude-code -s '*' -y
```

For a different supported agent, replace `claude-code`. The repository documents these safe
variants:

```bash
# Install for every agent the CLI detects
npx skills add social-media-skills/skills -g -a '*' -s '*' -y

# Open the interactive agent/skill picker
npx skills add social-media-skills/skills

# Install one skill instead of the whole library
npx skills add social-media-skills/skills -g -a claude-code -s reels-script -y
```

Alternative multi-agent installer:

```bash
npx skillkit install social-media-skills/skills
```

After installation, open your agent in `my-brand/`. The exact launch command depends on the
agent; this repository does not prescribe one.

### Option B — Claude Code plugin

Enter these in Claude Code's command interface, not in the shell:

```text
/plugin marketplace add social-media-skills/skills
/plugin install social-media-skills@social-media-skills
```

Then create and enter a brand workspace before starting work:

```bash
mkdir my-brand
cd my-brand
```

The plugin path is the simplest option when you want plugin updates without re-copying folders.

### Option C — manual copy for Claude Code or Claude Desktop

These are the copy commands documented by the repository:

```bash
git clone https://github.com/social-media-skills/skills.git social-media-skills
mkdir -p ~/.claude/skills
cp -r social-media-skills/skills/* ~/.claude/skills/
mkdir my-brand
cd my-brand
```

For a lighter first install, copy the documented starter set:

```bash
cd social-media-skills/skills
mkdir -p ~/.claude/skills
cp -r brand-profile voice-builder audience-research content-pillars content-calendar \
      hook-writer caption-writer short-form-video-script cross-platform-repurposing \
      engagement-routine platform-specs-and-validation scheduling-and-queue ~/.claude/skills/
```

Downloaded a source ZIP instead? Unzip it and copy from its `skills/` directory in the same
way. The README also mentions a Git submodule for tracked installs, but gives no canonical
submodule location or command; choose a location that your particular agent actually scans.
Do not assume a symlink is supported unless that agent's loader documents it.

### Option D — Claude on web or mobile

1. Download a topic pack from the repository's Releases page, or build one as described in
   [Packs](#8-topic-packs).
2. Unzip the **outer pack**. A pack is a bundle of individual skill ZIPs, not one mega-skill.
3. In Claude, open **Customize → Skills → + Create skill**. Code execution must be enabled.
4. Upload each inner skill ZIP, one at a time, in the order in the pack's `README.txt`.
5. Toggle every uploaded skill on, then use one chat per brand.

### Option E — OpenClaw, Hermes, or another Agent Skills loader

The repository documents these filesystem locations:

- OpenClaw: copy skill folders to the workspace `skills/` directory or
  `~/.openclaw/skills/` for all agents.
- Hermes Agent: copy skill folders to `~/.hermes/skills/` or the project's `skills/`
  directory; its marketplace search is `hermes skills search social media`.
- Other frameworks: point the loader at this repository's `skills/` directory or copy the
  individual skill folders into the loader's documented skill directory.

Because generic Agent Skills loaders do not share one filesystem convention, the safest
fallback is **copy the complete skill directory**, not only `SKILL.md`: its references and
eval fixtures belong with it.

## 3. Confirm the installation

Ask the agent:

```text
List the installed social-media skills you can route to. Confirm that brand-profile,
voice-builder, content-calendar, platform-specs-and-validation, and scheduling-and-queue
are available. Do not create or publish anything yet.
```

If your agent exposes installed-skill metadata, also confirm that the skill's frontmatter
`name` matches its folder name. In this repository, all 106 are expected to match.

## 4. How to invoke a skill

Most compatible agents route automatically from the `description` in each `SKILL.md`. Direct
invocation is more predictable when you want a specific specialist:

```text
Use <skill-name>.
Context: <brand, offer, audience, platform, goal>.
Inputs: <files, URLs, samples, existing drafts, native analytics export>.
Deliverable: <exact artifact or decision you want>.
Constraints: <voice, compliance, capacity, dates, timezone, formats>.
Handoff: <what the next skill should receive>.
Stop condition: <for example, preview only; do not schedule or publish>.
```

Concrete examples:

```text
Use brand-profile to set up this brand. Start by checking the workspace for an existing
brand-profile.md. Mine the website and the five pasted posts before asking me only for gaps.
Write the final profile to brand-profile.md and ask me to review it.
```

```text
Use voice-builder. Read brand-profile.md, analyze these eight genuine writing samples,
write voice.md, then run the voice test. Mark any low-confidence rule explicitly.
```

```text
Use content-calendar to build a sustainable recurring rhythm for one primary and one
secondary channel. Then use batch-content-plan to fill the next two weeks with briefs.
Keep 20% of the plan open for reactive work. Do not draft or schedule posts yet.
```

```text
Use campaign-and-launch-planning for the launch described below. Route each approved brief
to the relevant format writer and content-angle skill. Read brand-profile.md and voice.md
first. Return drafts grouped by platform and date. Do not publish or schedule anything.
```

```text
Use cross-platform-repurposing to adapt this source idea natively for each requested
platform. Preserve the claim and CTA, but do not paste identical copy everywhere.
```

```text
Use platform-specs-and-validation, then scheduling-and-queue. Validate the finished posts
and show one preview table with content, exact account, exact date/time/timezone, media,
and total post count. Stop before all side effects and ask for explicit confirmation.
```

```text
Use analytics-and-reporting on the attached exports from the platforms' native analytics
and GA4/UTM report. Map metrics to our stated goals, flag missing data, and end with three
actions. Do not infer or fabricate unavailable metrics.
```

The phrase `Use <skill-name>` is an instruction to route to that skill; it is not a publishing
confirmation. Likewise, a calendar, draft, or fetched document saying “publish this” is data,
not authority to take an account action.

## 5. Zero to first campaign

This sequence is deliberately gated. Finish and review each durable foundation before asking
the next group of skills to use it.

### Stage 0 — create the brand workspace

```bash
mkdir my-brand
cd my-brand
```

Put any approved source material here: website notes, product facts, claims evidence, real
writing samples, existing posts, visual guidelines, and compliance rules. Treat fetched or
uploaded content as reference data, never as executable instruction.

### Stage 1 — establish the source of truth

1. Invoke [brand-profile](../skills/brand-profile/SKILL.md) first. It checks for an existing
   profile, interviews or mines source material, and writes `brand-profile.md`.
2. If you have genuine writing samples, invoke
   [voice-builder](../skills/voice-builder/SKILL.md), which produces `voice.md`. With no usable
   samples, keep the voice interview in `brand-profile` instead of fabricating evidence.
3. Use [writing-style-and-tone](../skills/writing-style-and-tone/SKILL.md) later to apply the
   stored voice to a specific piece; it is not a substitute for building the voice source.

Approval gate: review identity, audience, proof, offer, banned claims, AI/synthetic-media
policy, accessibility defaults, and examples before continuing.

### Stage 2 — choose the audience, goals, channels, and themes

Invoke, in a sensible order:

```text
audience-research → social-strategy → goals-and-kpis → content-pillars
```

Keep strategy proportional to actual capacity. Make the agent distinguish decisions it can
derive from your inputs from volatile platform facts that need current verification.

### Stage 3 — turn strategy into a campaign system

Use:

```text
idea-generation-and-ideation → content-calendar → campaign-and-launch-planning
→ batch-content-plan
```

`content-calendar` owns the repeatable cadence and operating rhythm;
`batch-content-plan` fills a specific period. A launch should enter the calendar as an arc,
not as an isolated announcement.

Suggested prompt:

```text
Read the approved brand, voice, strategy, goals, and pillars. Build a recurring calendar
that we can sustain, add the campaign arc for <launch>, then fill the next 14 days with
specific briefs. For each brief identify the intended platform, audience job, pillar,
format, evidence needed, CTA, owner, and due date. Do not write or schedule yet.
```

Approval gate: check claims, coverage across pillars and funnel stages, production capacity,
owners, dates, and whether every brief has enough source material.

### Stage 4 — create platform-native content

For each approved brief, combine:

- A craft skill such as [hook-writer](../skills/hook-writer/SKILL.md),
  [caption-writer](../skills/caption-writer/SKILL.md), or the appropriate platform-format
  writer.
- An angle skill such as [educational-content-and-how-to](../skills/educational-content-and-how-to/SKILL.md),
  [storytelling-and-narrative](../skills/storytelling-and-narrative/SKILL.md), or
  [social-proof-and-testimonials](../skills/social-proof-and-testimonials/SKILL.md).
- [cross-platform-repurposing](../skills/cross-platform-repurposing/SKILL.md) when one source
  idea needs native versions for multiple platforms.
- [content-research-and-sourcing](../skills/content-research-and-sourcing/SKILL.md) whenever a
  factual claim needs evidence.

Ask for editable drafts and a claim/source ledger. Review every draft before media production
or distribution.

### Stage 5 — create or edit media

Use router skills to choose the craft/tool rather than defaulting to a fashionable generator:

```text
image-prompt / ai-image-editing / ai-video / ai-music-and-sound
→ a named tool skill → human review → editing or clipping skill
```

The individual integration guides explain connection and tool facts. Creative tools generate
or edit assets; the human reviews them. WoopSocial does neither.

Approval gate: check brand fit, accuracy, rights/licensing, disclosure, accessibility, aspect
ratio, captions/alt text, and the final exported file.

### Stage 6 — validate the finished queue

Invoke [platform-specs-and-validation](../skills/platform-specs-and-validation/SKILL.md) and
then [scheduling-and-queue](../skills/scheduling-and-queue/SKILL.md). Validation happens before
the committing action. Require a preview containing:

- Final content and attached media.
- Exact target account(s).
- Exact date, time, and timezone.
- Per-platform variant where applicable.
- Number of posts in the batch.
- Validation failures or plan-limit concerns that still need resolution.

### Stage 7 — connect and schedule, only after confirmation

The canonical bridge contract is the
[WoopSocial integration guide](../tools/integrations/woopsocial.md). The safe sequence is:

```text
health check → discover projects/accounts → upload reviewed media → validate every post
→ show preview → obtain explicit user confirmation → create posts → read back IDs/status
```

If the bridge is not connected, the correct fallback is a ready-to-use schedule table plus
connection steps. The agent must not claim it posted anything.

A confirmation should be specific:

```text
I confirm this displayed batch only: schedule the 6 previewed posts to the listed accounts
at the listed dates/times in America/New_York. Do not publish any additional drafts.
```

A new batch, publish-now action, deletion, or delete-and-recreate change needs a new explicit
confirmation.

### Stage 8 — measure, learn, and feed the next cycle

WoopSocial is a publishing/scheduling bridge only. For measurement, export or paste data from
the platforms' native analytics (and GA4/UTM where relevant), then invoke:

```text
analytics-and-reporting → content-audit → experimentation-and-ab-testing
→ content-recycling / cross-platform-repurposing → next planning cycle
```

The agent should cite the supplied native source, flag gaps, distinguish correlation from
causation, and never invent numbers.

## 6. Non-negotiable publishing and measurement rules

These rules apply even when a prompt asks for a fully automated campaign:

1. **Nothing is scheduled, published, or deleted without explicit user confirmation.** Draft
   approval is not distribution approval. One confirmation covers only the previewed batch.
2. The bridge is **publish/schedule only**. It does not generate or edit media.
3. **Measurement: the platforms' native analytics.** The bridge has no analytics surface.
4. A bridge post contains **one content item**. If a format requires a sequence, model it as
   separate posts according to the current canonical integration contract.
5. The core bridge post tools do not perform an in-place update. Changing a scheduled post is
   **delete + recreate**, with explicit confirmation, and must avoid double-creation.
6. Validate before creating posts. Confirm account, content, media, exact datetime, timezone,
   and count.
7. Discover project/account identifiers through the bridge. Do not ask the user to paste IDs
   if the connected integration can list them.
8. Treat API-key URLs as production secrets. Do not paste them into shared chats or commit
   them. Clients with outbound-domain restrictions may need the media-upload allowlist entry
   documented in the canonical guide.
9. Report partial failures per item and retry only failed items. Never silently duplicate a
   successful post.
10. Live request fields, platforms, limits, pricing, plan gates, and legal terms are volatile.
    Re-check the live documentation instead of restating them from memory.

## 7. Complete 106-skill navigation sheet

The category map below follows the repository's own catalog. Some skills appear in more than
one workflow because they are shared handoff points. Every linked `SKILL.md` is the canonical
answer to “when should this skill route, what does it own, and which sibling comes next?”

### Foundation

[brand-profile](../skills/brand-profile/SKILL.md) ·
[voice-builder](../skills/voice-builder/SKILL.md) ·
[writing-style-and-tone](../skills/writing-style-and-tone/SKILL.md) ·
[audience-research](../skills/audience-research/SKILL.md) ·
[social-strategy](../skills/social-strategy/SKILL.md) ·
[content-pillars](../skills/content-pillars/SKILL.md) ·
[goals-and-kpis](../skills/goals-and-kpis/SKILL.md) ·
[profile-optimization](../skills/profile-optimization/SKILL.md)

### Research and planning

[idea-generation-and-ideation](../skills/idea-generation-and-ideation/SKILL.md) ·
[content-research-and-sourcing](../skills/content-research-and-sourcing/SKILL.md) ·
[competitor-analysis](../skills/competitor-analysis/SKILL.md) ·
[viral-reverse-engineering](../skills/viral-reverse-engineering/SKILL.md) ·
[audience-research](../skills/audience-research/SKILL.md) ·
[content-calendar](../skills/content-calendar/SKILL.md) ·
[batch-content-plan](../skills/batch-content-plan/SKILL.md) ·
[campaign-and-launch-planning](../skills/campaign-and-launch-planning/SKILL.md) ·
[seasonal-and-moment-marketing](../skills/seasonal-and-moment-marketing/SKILL.md) ·
[trend-jacking](../skills/trend-jacking/SKILL.md) ·
[data-and-original-research](../skills/data-and-original-research/SKILL.md)

### Format writers

[hook-writer](../skills/hook-writer/SKILL.md) ·
[caption-writer](../skills/caption-writer/SKILL.md) ·
[linkedin-post-writer](../skills/linkedin-post-writer/SKILL.md) ·
[thread-writer](../skills/thread-writer/SKILL.md) ·
[threads-post](../skills/threads-post/SKILL.md) ·
[text-post-and-microblog](../skills/text-post-and-microblog/SKILL.md) ·
[carousel-writer](../skills/carousel-writer/SKILL.md) ·
[story-writer](../skills/story-writer/SKILL.md) ·
[short-form-video-script](../skills/short-form-video-script/SKILL.md) ·
[reels-script](../skills/reels-script/SKILL.md) ·
[tiktok-script](../skills/tiktok-script/SKILL.md) ·
[scripting-and-storyboarding](../skills/scripting-and-storyboarding/SKILL.md) ·
[reply-and-comment-writer](../skills/reply-and-comment-writer/SKILL.md)

### Content angles and formats

[educational-content-and-how-to](../skills/educational-content-and-how-to/SKILL.md) ·
[storytelling-and-narrative](../skills/storytelling-and-narrative/SKILL.md) ·
[contrarian-and-opinion](../skills/contrarian-and-opinion/SKILL.md) ·
[behind-the-scenes-and-founder](../skills/behind-the-scenes-and-founder/SKILL.md) ·
[before-after-and-transformation](../skills/before-after-and-transformation/SKILL.md) ·
[social-proof-and-testimonials](../skills/social-proof-and-testimonials/SKILL.md) ·
[listicle-and-roundup](../skills/listicle-and-roundup/SKILL.md) ·
[meme-and-culture](../skills/meme-and-culture/SKILL.md) ·
[interactive-content](../skills/interactive-content/SKILL.md) ·
[livestream-and-realtime](../skills/livestream-and-realtime/SKILL.md) ·
[podcast-and-audiograms](../skills/podcast-and-audiograms/SKILL.md) ·
[email-and-newsletter](../skills/email-and-newsletter/SKILL.md)

### Platform playbooks

- Instagram: [instagram-growth](../skills/instagram-growth/SKILL.md) ·
  [instagram-seo](../skills/instagram-seo/SKILL.md) ·
  [instagram-reels-publishing](../skills/instagram-reels-publishing/SKILL.md)
- TikTok: [tiktok-growth](../skills/tiktok-growth/SKILL.md) ·
  [tiktok-script](../skills/tiktok-script/SKILL.md) ·
  [tiktok-photo-mode](../skills/tiktok-photo-mode/SKILL.md) ·
  [tiktok-video-publishing](../skills/tiktok-video-publishing/SKILL.md)
- LinkedIn: [linkedin-growth](../skills/linkedin-growth/SKILL.md) ·
  [linkedin-post-writer](../skills/linkedin-post-writer/SKILL.md) ·
  [linkedin-company-pages](../skills/linkedin-company-pages/SKILL.md)
- X/Twitter: [x-growth](../skills/x-growth/SKILL.md) ·
  [thread-writer](../skills/thread-writer/SKILL.md)
- Threads: [threads-growth](../skills/threads-growth/SKILL.md) ·
  [threads-post](../skills/threads-post/SKILL.md)
- Facebook: [facebook-strategy](../skills/facebook-strategy/SKILL.md) ·
  [facebook-groups](../skills/facebook-groups/SKILL.md)
- Pinterest: [pinterest-growth](../skills/pinterest-growth/SKILL.md) ·
  [pinterest-seo](../skills/pinterest-seo/SKILL.md) ·
  [pinterest-pin-design](../skills/pinterest-pin-design/SKILL.md)
- YouTube: [youtube-long-form](../skills/youtube-long-form/SKILL.md) ·
  [youtube-shorts](../skills/youtube-shorts/SKILL.md) ·
  [youtube-publishing-and-metadata](../skills/youtube-publishing-and-metadata/SKILL.md) ·
  [thumbnail-design](../skills/thumbnail-design/SKILL.md)
- Reddit: [reddit-marketing](../skills/reddit-marketing/SKILL.md). This is advisory-only;
  follow its instruction that the human posts natively.

### Visual and design

[design-and-templates](../skills/design-and-templates/SKILL.md) ·
[thumbnail-design](../skills/thumbnail-design/SKILL.md) ·
[pinterest-pin-design](../skills/pinterest-pin-design/SKILL.md) ·
[quote-cards-and-text-graphics](../skills/quote-cards-and-text-graphics/SKILL.md) ·
[infographic-and-data-viz](../skills/infographic-and-data-viz/SKILL.md) ·
[image-prompt](../skills/image-prompt/SKILL.md)

### AI media and production tools

- Image generation/editing: [nano-banana](../skills/nano-banana/SKILL.md) ·
  [ideogram](../skills/ideogram/SKILL.md) · [flux](../skills/flux/SKILL.md) ·
  [ai-image-editing](../skills/ai-image-editing/SKILL.md)
- Video generation: [ai-video](../skills/ai-video/SKILL.md) ·
  [veo-3](../skills/veo-3/SKILL.md) · [kling](../skills/kling/SKILL.md) ·
  [luma](../skills/luma/SKILL.md) · [runway](../skills/runway/SKILL.md) ·
  [heygen](../skills/heygen/SKILL.md) · [synthesia](../skills/synthesia/SKILL.md)
- Voice, music, and sound: [ai-voiceover](../skills/ai-voiceover/SKILL.md) ·
  [suno](../skills/suno/SKILL.md) ·
  [ai-music-and-sound](../skills/ai-music-and-sound/SKILL.md)
- Editing and clipping: [capcut](../skills/capcut/SKILL.md) ·
  [descript](../skills/descript/SKILL.md) · [opus-clip](../skills/opus-clip/SKILL.md) ·
  [captions-and-clipping](../skills/captions-and-clipping/SKILL.md)
- Design platform: [canva](../skills/canva/SKILL.md)
- On-camera delivery:
  [talking-head-and-piece-to-camera](../skills/talking-head-and-piece-to-camera/SKILL.md)

### Distribution, growth, and monetization

[hashtag-strategy](../skills/hashtag-strategy/SKILL.md) ·
[social-seo](../skills/social-seo/SKILL.md) ·
[ai-search-optimization](../skills/ai-search-optimization/SKILL.md) ·
[cross-platform-repurposing](../skills/cross-platform-repurposing/SKILL.md) ·
[content-recycling](../skills/content-recycling/SKILL.md) ·
[link-in-bio-and-traffic](../skills/link-in-bio-and-traffic/SKILL.md) ·
[lead-magnets-and-funnels](../skills/lead-magnets-and-funnels/SKILL.md) ·
[social-selling-and-dm](../skills/social-selling-and-dm/SKILL.md) ·
[collabs-and-cross-promotion](../skills/collabs-and-cross-promotion/SKILL.md) ·
[ugc-and-influencer](../skills/ugc-and-influencer/SKILL.md) ·
[creator-monetization](../skills/creator-monetization/SKILL.md)

### Community and operations

[engagement-routine](../skills/engagement-routine/SKILL.md) ·
[community-management](../skills/community-management/SKILL.md) ·
[crisis-and-moderation](../skills/crisis-and-moderation/SKILL.md)

### Publishing and measurement

[scheduling-and-queue](../skills/scheduling-and-queue/SKILL.md) ·
[platform-specs-and-validation](../skills/platform-specs-and-validation/SKILL.md) ·
[analytics-and-reporting](../skills/analytics-and-reporting/SKILL.md) ·
[content-audit](../skills/content-audit/SKILL.md) ·
[experimentation-and-ab-testing](../skills/experimentation-and-ab-testing/SKILL.md)

## 8. Topic packs

Pack membership and upload order are canonical in [scripts/packs.json](../scripts/packs.json).
Every pack includes `brand-profile` and `scheduling-and-queue`; packs producing written or
spoken content also include `voice-builder`. Overlap is intentional so each pack can stand
alone.

| Pack | Best starting use |
|---|---|
| Social Media Starter Kit | First brand setup, voice, calendar, initial posts, scheduling |
| Content Calendar & Planning | Recurring calendar, batching, campaigns, seasonal moments |
| Post Writing Essentials | Hooks, captions, text posts, threads, carousels, storytelling |
| LinkedIn Growth | LinkedIn growth, posts, company pages, strategic comments |
| Instagram & Reels Growth | Instagram growth, Reels, Stories, carousels, SEO |
| TikTok Growth | TikTok growth, scripts, photo mode, publishing configuration, trends |
| YouTube Creator Kit | Long-form, Shorts, metadata, thumbnails, storyboards |
| X / Twitter Growth | X growth, threads, standalone posts, replies, trends |
| Facebook Growth | Pages, Groups, short-form video, captions, community |
| Pinterest Growth | Search-led growth, SEO, pin design, traffic |
| Threads Growth | Conversation-led growth, posts, hooks, replies |
| Video Creation Studio | Script, on-camera/AI video, clipping, thumbnail, scheduling |
| Engagement & Community | Engagement routine, community, partnerships, DMs |
| Analytics & Optimization | Goals, native-data reporting, audits, testing, recycling |
| Agency & Client Management | Strategy through reporting for client work |
| Visual & Design | Templates, image tools, graphics, infographics, thumbnails |
| AI Voice & Music | Voiceover, narration, music and sound with licensing review |

For maintainers, build fresh individual skill ZIPs and all packs with:

```bash
./scripts/build-skill-zips.sh
./scripts/build-packs.sh
```

Outputs are generated under `dist/` and `dist/packs/`. The pack builder always rebuilds the
individual skill ZIPs first, embeds any referenced integration guides under the standalone
skill's `references/tools/`, verifies pack membership, and writes upload instructions into
each pack.

## 9. Integrations

The [Tools Registry](../tools/REGISTRY.md) is the index. The durable architecture is:

```text
integration guide (connection/API/volatile facts)
→ tool skill (craft)
→ router skill (chooses tool where applicable)
→ human review
→ scheduling-and-queue bridge
```

| Area | Canonical guides |
|---|---|
| Publishing/scheduling | [WoopSocial](../tools/integrations/woopsocial.md) |
| Image generation/editing | [Nano Banana](../tools/integrations/nano-banana.md) · [Ideogram](../tools/integrations/ideogram.md) · [FLUX](../tools/integrations/flux.md) · [AI image editing router](../tools/integrations/ai-image-editing.md) |
| Video generation | [Veo](../tools/integrations/veo.md) · [Kling](../tools/integrations/kling.md) · [Luma](../tools/integrations/luma.md) · [Runway](../tools/integrations/runway.md) · [HeyGen](../tools/integrations/heygen.md) · [Synthesia](../tools/integrations/synthesia.md) |
| Voice, music, and sound | [ElevenLabs](../tools/integrations/elevenlabs.md) · [Suno](../tools/integrations/suno.md) · [AI music and sound router](../tools/integrations/ai-music-and-sound.md) |
| Editing, clipping, design | [CapCut](../tools/integrations/capcut.md) · [Descript](../tools/integrations/descript.md) · [OpusClip](../tools/integrations/opus-clip.md) · [Clipping](../tools/integrations/clipping.md) · [Canva](../tools/integrations/canva.md) |

Integration pricing, tiers, features, field schemas, and legal terms can change. Follow each
guide's `verify-quarterly` direction and prefer the vendor's live documentation when making a
current decision.

## 10. Update, validate, and build

### Consumers

- Plugin install: use the plugin's update path; no manual copy is required.
- Manual clone/copy install: update the checkout, then re-copy the skill directories:

  ```bash
  cd social-media-skills
  git pull
  cp -r skills/* ~/.claude/skills/
  ```

- If you modify skills locally, fork the repository or keep the modified copy separate so an
  update does not silently overwrite it.

### Contributors and maintainers

Run the repository validator before every commit or pull request:

```bash
./scripts/validate-skills.sh
```

It checks:

1. `SKILL.md`, `references/`, and `evals/evals.json` structure.
2. Frontmatter name/description.
3. Valid eval JSON.
4. Resolution of backticked skill cross-references.
5. Agent Skills description-length limits.
6. Plugin manifest JSON and version synchronization.
7. Pack membership.
8. Banned publishing/analytics claims and stale markers.

Build distributable artifacts only after validation:

```bash
./scripts/build-skill-zips.sh
./scripts/build-packs.sh
```

The release workflow also requires synchronized versions in
[plugin.json](../.claude-plugin/plugin.json) and
[marketplace.json](../.claude-plugin/marketplace.json), a
[VERSIONS.md](../VERSIONS.md) entry, a tag, and fresh generated ZIP attachments. See
[AGENTS.md](../AGENTS.md) for repository ground truths and [CONTRIBUTING.md](../CONTRIBUTING.md)
for the house pattern.

## 11. Troubleshooting

| Symptom | Check or fix |
|---|---|
| Agent cannot find a skill | Confirm the complete `skills/<name>/` directory is in the loader's scanned path, the skill is enabled, and the frontmatter `name` matches the directory. Reload the agent after copying. |
| Claude pack upload fails | Unzip the outer pack and upload the inner per-skill ZIPs individually in `README.txt` order. Enable code execution and toggle each skill on. |
| Output sounds generic | Confirm `brand-profile.md` exists and is current. Build `voice.md` from genuine samples; ask content skills to read both before drafting. |
| Brand voices leak across clients | Use one workspace and one profile/voice pair per brand. Do not run several brands from the same working folder. |
| Calendar is impossible to maintain | Re-run `content-calendar` with real production capacity and the bad-week floor, then use repurposing for secondary channels. |
| Agent chooses the wrong specialist | Invoke it explicitly with `Use <skill-name>` and state the expected deliverable, handoff, and stop condition. Check the target skill's `description` for sibling routing. |
| Publishing bridge is unavailable | Run a health check and follow the canonical connection guide. If it is still unavailable, produce a schedule table; never claim success. |
| Media post creation works but upload fails | Check the outbound-domain allowlist requirement in the canonical WoopSocial guide. Do not guess MIME fields; follow the live schema. |
| Target account is missing | Re-list connected accounts and follow the bridge's account authorization flow. Do not silently skip the target. |
| “9 a.m.” or “tomorrow” is rejected | Supply an exact date, time, and timezone before confirmation. |
| Need to edit a scheduled post | Preview and explicitly confirm a delete + recreate operation. Verify the old post was removed and the new ID was created once. |
| Batch partly fails | Preserve successful IDs, report failures item by item, and retry only failures. |
| No performance data appears | Expected: the bridge has no analytics surface. Export or paste data from the platforms' native analytics and use `analytics-and-reporting`. |
| Validation reports an outdated platform rule | Check the live vendor/bridge documentation and update the relevant `verify-quarterly` reference; do not patch from memory. |
| Repository validator fails | Read the named phase and file in the output, fix only the reported source, and rerun `./scripts/validate-skills.sh`. Do not hand-edit generated `dist/` artifacts. |

## 12. A reusable campaign prompt

Use this after installation from inside a brand workspace:

```text
Run an end-to-end campaign workflow for <brand/offer/campaign>, using the installed social
media skills and preserving review gates.

1. Check for brand-profile.md and voice.md. If missing, route to brand-profile first and
   voice-builder only when genuine writing samples exist.
2. Read or create audience research, social strategy, goals/KPIs, and content pillars.
3. Build a sustainable content calendar, the campaign arc, and briefs for <date range>.
4. Pause for my approval of the plan.
5. After approval, route each brief to the correct format writer, content-angle skill, and
   media router. Cite evidence for factual claims and return editable drafts/assets.
6. Pause for my approval of final content and media.
7. Validate all finished posts. Show one preview table containing what, where, when,
   timezone, media, validation result, and total count.
8. Stop. Do not schedule, publish, or delete until I explicitly confirm that exact batch.
9. After an explicit confirmation, use scheduling-and-queue, report returned post IDs and
   any per-item failures, and do not retry successes.
10. For reporting, use only data I provide from the platforms' native analytics (plus
    GA4/UTM where relevant). Never fabricate unavailable metrics. Feed the findings into
    content-audit, experimentation, and the next planning cycle.
```

That prompt tells the agent how to chain skills, but the individual `SKILL.md` files remain the
source of truth for execution details and routing boundaries.
