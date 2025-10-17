# Seed: Reaction–Diffusion (Gray-Scott)

Overview
- Continuous field simulation producing emergent patterns via two-species reaction and diffusion.

Parameters
- feed (f): 0.0–0.1
- kill (k): 0.0–0.1
- da, db: diffusion rates
- dt, steps_per_frame
- palette: name or custom stops
- boundary: wrap | clamp | reflect

Outputs
- Canvas texture, metrics per frame: entropy, edge density, oscillation index, symmetry score.

LES Hooks
- Resonance: palette-frequency alignment metric
- Reciprocity: agent-field mutual influence index
- Reversibility: state rollback and drift monitor
- Dignity safeguard: content filter for sensitive figurative emergence

Procedures
- Initialize with random salt or specified seeds.
- Run simulation; capture snapshots and timelines.
- Enable Fork from snapshot; Remix by blending (f,k) paths.

References
- Gray & Scott 1984, Pearson 1993; GPU implementations available.
