# Script anatomy, causal boards and executable shots

## Start with a payoff card

Before opening-shot spending, supply:

- Story revision, premise, desire, chosen action, consequence and visible payoff.
- Payoff still and identity references for every late cast member; exact payoff speaker and line.
- What the viewer must see to understand the consequence, including prop ownership and body state.
- Named review predicates, actual evidence/asset hashes, reviewer and pass/fail/unknown status.

Ask a cold reader to recount the causal chain from the ordered boards without the explanatory pitch.
Record their actual answer. A self-check can catch omissions but is not independent cold-reader evidence.
If no reviewer or images are available, mark those checks pending and block motion. Writing the desired
answer or “doctor correct” into a template does not prove the reviewed still contains the correct doctor.

## Beat sheet and local shot record

Target runtime first, derived from the complete performance (honor an explicit duration lock). Clip
count follows the beats and authorized provider limits; a story beat, edited shot and provider clip are
not automatically one-to-one. A held reaction may deserve more time than a fast transition.

```text
STORY REVISION / TARGET RUNTIME / PLANNED CLIP COUNT:
IDENTITY RULES: voice, novelty, captions/text, music, CTA/continuation, route, delivery
CAUSAL CHAIN: desire -> action -> consequence -> visible payoff
PAYOFF + LATE CAST REVIEW: assets/hashes, predicates, reviewer/evidence, status
COLD-READER REVIEW: actual answer/evidence, uncertainty or pending

SHOT ID / PURPOSE / LOCAL DURATION:
INITIAL STATE: location, framing, body pose, contacts, opening/obstacle geometry
REQUIRED CAST: named visible actors; named offscreen actors/audio sources if needed
ACTION: one dominant observable action, ordered sub-beats
COMPLETED END STATE: observable completion + readable hold; never only intention or mid-action
INVARIANTS: cast identity, body count/anatomy, prop count/appearance/owner, screen direction
ALLOWED TRANSFORMATIONS: none, or named transformation_id, what changes when, what must remain
COVERAGE: viewpoint/framing/move and what the audience must see
TIMING: action windows, exact named speaker lines, pauses, SFX, compatible overlaps
TEXT: none if forbidden; otherwise only approved text
TRANSITION TO NEXT: continuous | hard_cut | match_cut | transformation; reason
PLANNED BOARDS: local start + completed-end boards for review
INPUT ROLES: identity reference | start composition | end target | timed keyframe as supported
DEPENDENCY: selected upstream attempt/output hash + observed outgoing evidence, or none
REVIEW: cast, completed action, speaker/source, possession, payoff; evidence and pass/fail/unknown
```

Plan both local start and completed-end boards for review. A planned/reviewed end board does not
mean every route must submit an endpoint pin; map only the controls required by the approved method
and supported by the adapter. Do not turn these portable labels into invented provider parameters. **ai-video** maps the plan into
the authorized renderer's supported controls. Prompt intent, approved stills and observed output are
different evidence; keep their roles separate even when two assets happen to share bytes.

## Transition taxonomy

| Transition | What must be planned and reviewed |
|---|---|
| `continuous` | The next shot continues the same action/state. Bind to the selected preceding attempt and observed outgoing frame/action evidence; preserve positions, possession, direction and relevant sound. |
| `hard_cut` | A deliberate edit changes location, time or coverage. State what changed and what persists; establish the new space. Show the preceding necessary action completing before the cut. Do not interpolate the two spaces. |
| `match_cut` | An intentional edit matches a chosen shape, pose or movement. Name the match and any space/time change; preserve identity/possession as required. Similar framing is not evidence of continuous physical travel. |
| `transformation` | Name the intentional transformation (transformation_id), what transforms, the mechanism/timing and unchanged identities, bodies or props. Review the intended change separately from accidental mutation. |

Never bind the next storyboard as the current shot's end target merely because it comes next. An
exterior entry endpoint and an interior establishing composition have different jobs. A new location
can be a deliberate cut without pretending the renderer traverses both spaces in one interpolation.

## Worked planning case — courier enters a folding doorway

Fictional example, not a brand premise or generated-media review. No on-screen text or music; dialogue
and SFX carry the sound-on version. Runtime estimate **23 seconds**, **3 planned clips**, subject to the
approved route's verified limits and natural read-through. No generic clip grid is assumed.

**Causal chain:** courier Mira wants her ringing parcel silenced → carries it fully through a paper
clinic doorway → discovers the parcel is the patient → Dr. Sen examines the parcel, which stops ringing
and snores. The parcel remains visibly the same parcel; the doctor is the named payoff speaker.

**Payoff first:** board P shows Mira screen left with empty hands, Dr. Sen screen right, one red parcel
on the exam table, Sen's stethoscope touching it. Sen says “It needs a nap.” The parcel snores. Lock Sen's
approved appearance and voice before opening motion. No extra patient or creature. No visual review
has occurred in this textual example: payoff/late-cast/cold-reader review remain pending; motion blocked.

| Shot | Local state → action → completed end | Action and dialogue timing | Transition |
|---|---|---|---|
| S1, 8s | Mira outside, parcel in both hands, doorway visibly wide enough → braces door and crosses with parcel → both feet, torso and parcel entirely beyond threshold; doorway empty | 0–1s anticipate; 1–2s Mira: “Please stop ringing.”; 2–6.5s crossing, paper rustle/ringing; 6.5–8s empty-threshold hold | `hard_cut` to clinic interior; entry must be completed first |
| S2, 7s | Interior wide, Mira holding parcel, Sen beside empty table → Mira puts parcel down, releases it → parcel rests alone on table, both hands visibly clear | 0–1s establish; 1–4s placement/release; 4–5.5s Sen: “Who's the patient?”; 5.5–7s Mira points to parcel | `hard_cut` to closer payoff coverage of the same table; possession persists |
| S3, 8s | Same parcel on table, Sen's instrument in hand, Mira visible at left edge → Sen listens and diagnoses → contact shown, ringing stops and parcel audibly snores, both react | 0–3s contact/listening; 3–5s Sen: “It needs a nap.”; 5–6s snore; 6–8s reaction/hold | Standalone ending |

**Invariants in every relevant shot:** Mira/Sen remain their approved identities; each retains the
approved body and clothing; one red parcel, no duplicate or new creature. S1 owner Mira; S2 transfer to
table completed; S3 parcel remains on table. Transformations: none; sentient sound does not authorize
turning the parcel into a body. Name cast shot by shot: Mira in S1, Mira and Sen in S2/S3. Never “if the
doctor appears.” The interior is not S1's pinned ending. Its initial pose must agree with S1's accepted
outgoing evidence and the explicit cut; changed S1 selection invalidates the dependent review.

## Three alternative executable openers for that body

1. **Urgency:** medium shot; parcel rings in Mira's hands; she recoils then looks at the doorway. First
   words: “Please stop ringing.” Ringing stops her mid-step. Bridge: she braces the doorway to enter.
2. **Failed solution:** close shot; Mira covers the parcel with her sleeve, but the ring sounds louder;
   she uncovers it and turns toward the doorway. No words; fabric scrape and ring. Bridge: same entry.
3. **Absurd command:** waist-level shot; Mira taps the parcel to shush it; it answers with one sharp
   ring, and she points it toward the clinic. First words: “Inside. Now.” Bridge: same entry.

Each opener needs its own timed beat-sheet revision if selected. These are alternatives, not three
extra scenes. Recommend the first for a clear problem/destination pairing; that is a creative judgment,
not a retention prediction. Keep the downstream payoff unchanged or explicitly revise and re-review it.

## Cut-test and review

Remove a beat only if it neither establishes a necessary fact, advances causality, delivers the payoff
nor supplies needed comprehension/reaction time. Retention dips are hypotheses about problems, not
proof of their cause. Validate with the platforms' native analytics, not invented viral statistics.
After rendering, review selected footage and synchronized audio: sample frames cannot establish the
full entry action, speaker ownership, exact dialogue or timing. Unknown/failed critical checks keep the
result draft regardless of budget or number of review rounds.
