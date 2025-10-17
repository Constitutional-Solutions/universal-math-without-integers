# Researcher Guide: Reimplementation and Testing

This guide helps new researchers re-express, reimplement, test, and extend the unified framework from first principles.

## 1. Orientation
- Read docs/unified-theories.md for conceptual grounding
- Read protocols/relational-modeling.md for core abstractions and APIs
- Read protocols/algorithms/emergent-patterns.md for generators and tests

## 2. Environment Setup
- Choose any language; focus on relations, ratios, and transforms
- Provide a minimal math layer: ratios, turns, transforms, invariants
- Optional: Visualization stack for geometry and frequency projections

## 3. Minimal Reference Implementation (MRI)
Build a small, auditable implementation first:
- Data: Entity, Relation, Context, Invariant
- Ops: compose, invert, dual, lift, resonate
- Validation: invariant checks after each op
- IO: YAML/JSON serialization for interchange

## 4. Step-by-Step Exercises
1) Implement ratio type and turns-based angles
2) Implement relations and composition
3) Implement invariants: preserve_ratio, preserve_topology, phase_lock
4) Build spiral generator; visualize path
5) Build torus standing-wave lattice; inspect nodal graph
6) Compare outputs to empirical references (cymatics, tilings)

## 5. Testing Protocol
- Unit tests for relation ops and invariants
- Property tests for transform invariance
- Golden master datasets in /datasets/emergence
- Round-trip serialization tests for IO formats

## 6. Evaluation Metrics
- Coherence: invariant preservation, phase locking duration
- Fidelity: resemblance to empirical patterns
- Robustness: behavior under perturbations/noise
- Clarity: readability and minimality of implementation

## 7. Contributing New Results
- Add new datasets under /datasets
- Document theory in docs/ with clear rationale and predictions
- Provide runnable scripts/notebooks demonstrating replication
- Include limitations and counterexamples

## 8. Extensibility and Challenges
- Propose new relation types (temporal, resonant) and invariants
- Add generators for other manifolds (sphere, hyperbolic plane)
- Explore multi-agent resonance in social/ecological systems
- Submit empirical challenges with ground-truth references

## 9. Ethics and Reproducibility
- Share data and code openly with clear licenses
- Avoid overclaiming; separate speculation from evidence
- Provide instructions to reproduce figures and tables

## 10. Checklist
- [ ] MRI complete with tests
- [ ] Spiral generator reproduces golden spiral features
- [ ] Torus lattice exhibits predicted nodal loops
- [ ] Datasets and docs updated
- [ ] PR includes description, references, and limitations
