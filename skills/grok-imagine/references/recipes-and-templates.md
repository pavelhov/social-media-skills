# Grok Imagine MOTION recipes and templates

Use these as shot briefs, not magic strings. Replace brackets with actual brand/source details, keep one
shot per request, and verify current mode settings in `tools/integrations/grok-imagine.md`.

## Universal MOTION prompt
```text
MODE: [text-to-video | image-to-video | reference-to-video | edit | extend]
DURATION / FORMAT: [seconds within current limits], [aspect ratio], [draft/final resolution]

OBSERVABLE: [specific subject] [visible action] in [setting], ending with [visible end state].
TIMING: [0-Xs beat]. [X-Ys beat]. [Y-Zs resolution].
CAMERA IDEA: [one move or locked frame], [framing/lens feel], [lighting/palette], [motion character].
AUDIO: Dialogue: "[exact short line]" spoken by [speaker]. Foley: [events].
Ambience: [continuous bed]. Music: [role/energy] | AUDIO OFF.
REFERENCES: [Reference 1 controls ...; Reference 2 controls ...].
PRESERVE: [identity/product geometry/composition/timing/background/audio elements that must not change].
REVIEW: [fidelity, continuity, text/hands, dialogue/sync, rights, disclosure].
```

## Recipe 1 — vertical text-to-video product hook
```text
MODE: text-to-video. 8 seconds, 9:16. Draft at a supported lower resolution.
OBSERVABLE: A sealed matte-white parcel sits on a cobalt workbench. Its paper pull-tab peels itself
open in one clean motion, revealing the orange product case; end on the centered case and intact logo.
TIMING: 0-1s tab snaps upright. 1-5s tab peels and lid opens. 5-8s case settles in hero position.
CAMERA IDEA: locked close three-quarter frame with a very slow push-in; hard side light, crisp shadows;
brand cobalt/orange only.
AUDIO: No dialogue. Foley: paper tear synchronized to the tab, soft case landing. Ambience: quiet studio.
No music.
NAIL: no extra hands, labels, objects, or camera cuts. Human review logo fidelity and foley sync; final
render only after the composition wins.
```

## Recipe 2 — image-to-video from a canonical product still
```text
MODE: image-to-video using the approved still as frame one. 6 seconds, inherit the source composition.
OBSERVABLE: Preserve the bottle, label, cap, tabletop, and framing exactly. Condensation slowly gathers;
one droplet travels down the right edge while a narrow light sweep crosses the glass. End on the same pose.
TIMING: 0-2s condensation appears. 2-5s droplet falls and light sweeps. 5-6s settle.
CAMERA IDEA: locked camera; no reframing, orbit, or zoom. Same warm dusk palette and shallow depth.
AUDIO: soft room tone and one subtle droplet sound; no speech or music.
NAIL: do not rewrite label text, deform bottle geometry, add props, or move the camera. Review every label
frame; reject drift rather than fixing it with more prompt adjectives.
```

## Recipe 3 — reference-to-video with explicit reference roles
```text
MODE: reference-to-video. 10 seconds, 9:16, current supported reference-mode resolution.
REFERENCES: Reference 1 controls the consented performer's appearance and wardrobe. Reference 2 controls
the product's shape, color, and label. Reference 3 controls lighting/palette only.
OBSERVABLE: The performer enters a compact night kiosk, sets the product on the counter, and looks to it;
end with performer and product both readable.
TIMING: 0-3s entrance. 3-7s product placement. 7-10s held end pose.
CAMERA IDEA: one gentle lateral track at waist height; neon magenta/cyan palette from Reference 3.
AUDIO: Footsteps, jacket rustle, product set on wood, distant city ambience. No dialogue.
NAIL: references guide the new composition; none is assumed to be frame one. Confirm likeness permission,
compare identity/product fidelity, and disclose synthetic generation.
```

## Recipe 4 — bounded video edit
```text
MODE: video editing on the permitted source clip.
CHANGE: Replace only the grey jacket with a solid navy jacket; keep natural fabric folds and occlusion.
PRESERVE: face, hair, skin tone, body proportions, performance, hand motion, timing, framing, camera motion,
background, lighting, original dialogue, foley, and ambience. Add no logos or accessories.
REVIEW: compare source and output side by side at the same timestamps. Reject if anything outside the jacket
changed. Preserve disclosure/provenance for the material edit.
```

## Recipe 5 — continuity-first extension
```text
MODE: extend the approved source clip.
OBSERVABLE: Continue the cyclist's existing left-to-right path for one simple action arc; the cyclist passes
behind the foreground tree and exits frame right. End on the empty road for an edit point.
CAMERA IDEA: continue the same pan speed, focal feel, horizon, dusk exposure, and screen direction.
AUDIO: continue the same tire noise, wind, and distant birds without a level jump; no new speech or music.
PRESERVE: cyclist identity/bicycle geometry, road layout, weather, color grade, motion trajectory, and audio
bed. Review the join frame-by-frame and by ear; do not chain extensions to fake a whole film.
```

## Recipe 6 — dialogue and native audio
```text
MODE: text-to-video. 7 seconds, 16:9.
OBSERVABLE: An original, consented fictional spokesperson looks from the product to camera and lifts it once.
TIMING: 0-2s glance and lift. 2-6s line. 6-7s hold.
CAMERA IDEA: locked medium close-up; soft window key, quiet workshop background.
AUDIO: The spokesperson says exactly, "Built to be repaired, not replaced." Foley: light fabric movement
and product latch click. Ambience: low workshop room tone. No music.
NAIL: no extra words, captions, logos, or off-screen voices. Review the spoken line, mouth sync, voice rights,
and product claim before use. Record approved human voice in post if generated delivery is not brand-safe.
```

## Apply templates to the actual shot

Delete irrelevant template fields: an absent character's pouch, wardrobe or voice must not leak into
another shot. Inspect the actual input image for the required initial pose, contacts, prop ownership
and background state before animation. Compare the expected ending with the next shot's beginning.
No prompt guarantees rigid contact, identity, or exact speech. Record unknown checks honestly.
Use the iteration card only inside an approved test/repair scope; preserve successful assets and
check timed-out jobs before retrying. Do not infer reroll permission from remaining budget.

## Cheap iteration card
1. Confirm the mode and rights before rendering.
2. Draft one short useful shot at a supported lower resolution.
3. Change one variable per candidate: action timing, camera, or audio—not all three.
4. Keep prompt, reference set, settings, and output paired for review.
5. Human-select the winner; final-render only that direction at the required supported resolution.
6. Review picture and sound, assemble/caption, then route the approved file through
   scheduling-and-queue to WoopSocial after explicit confirmation.

## Never
Mix incompatible modes in one request · use references without permission · imply a reference guarantees
identity · ask for multiple scenes in one short shot · stack contradictory camera moves · leave audio
unspecified when it matters · trust generated dialogue without listening · make a broad edit without
preservation constraints · chain extensions instead of storyboarding · start with an expensive final batch ·
pass synthetic evidence off as real · claim this skill or WoopSocial rendered the clip.
