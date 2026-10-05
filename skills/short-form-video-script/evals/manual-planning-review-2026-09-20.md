# Manual planning exercise — 2026-09-20

Scope: U5 story/directing changes, R1–R4. This is an implementation-agent planning exercise and manual
rubric review using the changed scenario prompts. It is not an automated model-evaluation run,
independent review, engine dry run, or visual-quality benchmark. Adding evals.json entries did not
execute models. No media tools, external providers, publishing or installed-skill changes were used.

**No-test exception:** the changed production artifacts are prose and evaluation specifications,
with no runtime code. Verification is the repository validator plus the concrete manual cases below;
there is no new unit test that merely searches prose for expected words. Runtime integration and
independent review belong to the implementing lead. Pending real images/reviews stay pending.

## Case 1 — causal traversal and a late payoff speaker

Inputs: short-form-video-script/causal_traversal_completed_entry_and_interior_cut and
ai-video/story_package_before_route_and_motion. Selected example identity rules: no burned captions,
no music, standalone ending; subscription CLI route locked. No actual boards or cast references supplied.

**Produced planning output**

Story revision example-1. Mira wants the ringing parcel silenced → carries it completely into the paper
clinic → the doctor identifies the parcel as the patient → Dr. Sen listens to it and says “It needs a
nap”; ringing stops and the parcel snores. Visible payoff board P is planned first: Mira left with empty
hands, Sen right with stethoscope touching the one red parcel on the table. No second creature.

Target 23 seconds, 3 planned clips, contingent on the installed locked adapter's duration support.
S1 8s: initial Mira outside holding parcel; 0–1s anticipate, 1–2s “Please stop ringing,” 2–6.5s cross,
6.5–8s hold on empty threshold. Completed end: both feet, torso and parcel beyond the doorway.
S2 7s: hard_cut to established interior with Mira holding the parcel and Sen at an empty table; 0–1s
establish, 1–4s place/release parcel, 4–5.5s Sen asks “Who's the patient?”, 5.5–7s Mira points. Completed
end: parcel resting on table, Mira's hands clear. S3 8s: hard_cut to closer table coverage; 0–3s Sen makes
stethoscope contact/listens, 3–5s exact payoff line, 5–6s snore, 6–8s shared reaction. End on the snoring
parcel, no CTA. Action/speech windows are estimates for read-through, not measured performances.

Cast by shot: S1 Mira only; S2/S3 Mira and Dr. Sen. Named speaker per line as above. Mira and Sen retain
approved faces, clothing, body count/anatomy. One red parcel throughout, owned/held by Mira in S1 and
S2 initial state, released onto table by S2 end, unchanged in S3. Allowed transformations: none. A sound
from the parcel does not authorize turning it into an animal. Start and completed-end boards are
planned for all three shots. Identity refs, local composition and local endpoint targets have separate
roles. The interior board is never S1's endpoint; actual endpoint-pin controls depend on the approved
method and adapter support.

Selected upstream attempt, output hash, outgoing frame/hash and action review are pending for S2/S3;
no hash or successful motion is invented. Payoff/late-cast/cold-reader image review: **pending**. Opening
motion: **blocked**. Execution estimate: three disclosed first-pass calls if supported; CLI media cost
**unknown** until observed, never substituted with API prices. Approval: **not granted**. No repairs
approved, no provider calls made. Full selected-master AV review is also pending.

**Manual rubric result:** expected planning fields, completed entry, deliberate cut, late cast, identity
locks, timing and honest blockers are present. This passes the planning-output self-check; it is not
motion-eligible, cold-reader proof or visual proof.

## Case 2 — rejected payoff still cannot be prompt-repaired

Input: short-form-video-script/payoff_wrong_doctor_blocks_opening.

**Produced response:** “Opening motion stays blocked. The supplied review rejects the payoff doctor's
identity and the extra creature/body count. Correct the payoff still and required cast reference under
the applicable image authorization, then record fresh review of the matching story revision and image
hashes. Review opening eligibility only after that passes. Stronger negative motion wording cannot
repair those supplied pixels. The remaining budget and number of review rounds do not change these
critical results. Preserve existing assets; no new image or video generation is authorized by this
assessment.”

**Manual rubric result:** rejected critical checks remain blocking; specific defects and smallest
prerequisite repair are named. No fabricated image inspection or corrective-generation permission.

## Case 3 — distinct executable hooks under no-caption rules

Input: hook-writer/video_executable_openers_no_caption_identity.

**Produced alternatives for the Case 1 body**

| Option | First frame and timed action | Exact audio | Bridge |
|---|---|---|---|
| Urgency | Medium Mira holding red parcel; 0–1s ring/recoil, 1–2s look to clinic, 2–3s brace door | “Please stop ringing.” during look; ring continues | Enter with parcel; allocate traversal/completion separately |
| Failed solution | Close parcel/Mira's hands; 0–1s sleeve covers it, 1–2s louder ring, 2–3.5s uncover and turn to door | Fabric scrape and ring, no spoken words | Carry it to threshold; selected script expands opener by 0.5s |
| Absurd command | Waist shot Mira/parcel; 0–1s tap to shush, 1–2s answering ring, 2–3s point parcel at door | “Inside. Now.” at 2–3s; single ring | Brace door and cross; do not count brace/traversal as completed in opener |

Text: none. Music: none. Recommendation: Urgency shows the problem and intended destination most
clearly while connecting to the fixed entry. This is a creative judgment, not a retention estimate.
These are alternative performances, not extra scenes. Re-time the selected script before approval.
Muted viewer sees a troubled courier/parcel and destination but cannot hear the ringing cause or the
spoken payoff; no caption override is introduced.

**Manual rubric result:** three distinct performed events, framing, lines/SFX, timing and causal bridges;
no relabelled slogans, no invented performance claim, identity format preserved.

## Case 4 — deliberate transformation with protected identities

Input: short-form-video-script/deliberate_transformation_invariants_and_timing.

**Produced planning output:** Mira folds the parcel to quiet it → it becomes one paper bird and chirps →
Sen reacts to this unauthorized “treatment” with “That is not what I prescribed.” Target 17 seconds,
2 planned clips subject to verified route limits. Start/complete-end boards planned for each.

S1, 9s, table two-shot: Mira left holding one red paper parcel, Sen right, empty tabletop between them.
0–1s Mira appraises it; 1–6s deliberate folding; 6–7s reveal completed paper bird in her hands; 7–8s one
chirp; 8–9s Sen registers the change. Completed end: one fully formed paper bird held by Mira. Dominant
action is the intentional `transformation`, transformation_id parcel_to_bird, with allowed changes
bounded below. The edit to S2 is a `hard_cut` to Sen's closer reaction coverage. Keep the allowed
transformation within S1 separate from the cut between shots; it grants no permission for other mutations.

S2, 8s: initial Sen foreground right, Mira/one bird visible at left edge, no ownership change. 0–1s
inhale/look, 1–5s Sen says “That is not what I prescribed,” 5–8s silent awkward reaction. Completed end:
Sen looking at the paper bird, Mira still holding it. Cast required in both shots: Mira and Sen. Speaker:
Sen only. Neither actor transforms; approved faces, bodies and clothing remain. Object count stays one,
red material remains, owner remains Mira; parcel form alone may become a paper bird. Caption/music/CTA:
none. Physical folding and dialogue receive sequential time, not forced overlap.

Three opening alternatives for the folding action: (A) Mira traces a fold line with a finger, paper
rustle, no speech, then folds; (B) parcel corner pops up like an unfinished wing, Mira notices and
continues that fold, one paper snap; (C) Mira presses the parcel flat, releases it, then decides to fold
it, a flat paper slap. Each is a distinct staged lead-in requiring timing review if selected. No new
actor or spoken claim is added. Payoff board first: Sen's visible reaction with Mira/one bird readable;
exact line as above. Matching image, late-cast and cold-reader review are pending, therefore motion
blocked. No generation.

**Manual rubric result:** named intentional change, one-object/identity/ownership invariants, named
payoff speaker, timing, optional-text policy and executable hook alternatives present. Engine-specific
serialization remains an integration task; this output does not claim schema validation.

## Additional control check

Input: ai-video/unsupported_endpoint_or_stale_outgoing.

**Produced response:** “A prose description is not a submitted endpoint pin. If the approved method
requires that control and the locked adapter cannot send it, launch is blocked pending a revised
approved method; the provider/route stays unchanged. Planned local end boards still belong in review
even when a method does not require endpoint pinning. The changed upstream selection invalidates the
old outgoing evidence: bind the current attempt/output/outgoing-frame hashes and obtain matching action
and continuity review before the dependent shot. No retry or corrective generation follows from the
budget alone.”

**Manual rubric result:** unsupported control and stale evidence are distinguished and both block the
relevant request; no universal provider pin requirement is invented.

## Repository verification

`./scripts/validate-skills.sh` completed with exit 0: **107 skills validated**, all eight gates passed
(structure, frontmatter, eval JSON, cross-references, description lengths, manifests, packs, banned
patterns). This validates library structure, not behavioural model execution or live visual reliability.
