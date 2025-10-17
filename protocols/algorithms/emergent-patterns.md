# Algorithms: Emergent Pattern Generation

This document specifies foundational algorithms for generating emergent patterns from first principles using relation, transformation, and resonance protocols.

## 1. Design Principles
- Minimal seeds and simple rules
- Continuous transforms (rotate/scale/translate) with ratio-based parameters
- Feedback loops and resonance detection for stability selection
- Context-aware operations (media, scale) and invariant preservation

## 2. Canonical Generators

### 2.1 Logarithmic Spiral Generator
Inputs: seed relation, growth ratio φ, rotation per step r_turns
Algorithm:
1) Initialize seed entity E0 and relation R0: scale(E0 → E1, ratio=φ)
2) For step k in [0..N):
   - Rotate by r_turns
   - Scale by φ
   - Append relation to path, validate invariants
3) Yield path and geometry projection
Outputs: path of relations, geometric coordinates (if projected)

### 2.2 Fractal Tessellation (Self-similar Tiling)
Inputs: base polygon relation set, scale ratios, symmetry group
Algorithm:
1) Place base tile under context C
2) Apply symmetry transforms from group G
3) Recursively place child tiles with scale ratios
4) Prune overlaps by relation constraints
Outputs: tile graph, adjacency relations

### 2.3 Torus Standing Wave Lattice
Inputs: torus parameters (major/minor ratios), harmonic set H
Algorithm:
1) Define parametric map on torus by angle turns (u,v)
2) For each harmonic h ∈ H, superpose sinusoidal relation on (u,v)
3) Identify nodal lines where amplitude≈0
4) Extract stable loops and intersections as relation graph
Outputs: resonant loops graph, nodal lattice

## 3. Resonance Detection

Given two relational processes P and Q:
- Compute phase difference Δφ(t) over time/context
- Identify locking when |Δφ| < ε for τ duration
- Detect beats via difference frequency f_b = |fP − fQ|
- Select attractor states where locking persists under perturbation

## 4. Projection to Geometry and Frequency

- Geometry: map relational paths to coordinates via chosen gauge (units cancel)
- Frequency: map cycle times to ratios; annotate overtones and subharmonics
- Topology: compute invariants (winding number, connectivity) without metric

## 5. Reference Pseudocode
```pseudo
fn spiral(seed, phi, r_turns, N) -> Path
  E ← seed
  path ← []
  for k in 0..N-1
    E' ← transform(E, rotate=r_turns, scale=phi)
    path.push(relation(E→E', label="spiral-step", attrs={ratio:phi}))
    assert invariants(path)
    E ← E'
  return path

fn cymatic_torus(params, H) -> Graph
  grid ← sample_param_space(params)
  A ← superpose_waves(grid, H)
  nodes ← find_nodal_loops(A)
  return build_graph(nodes)
```

## 6. Datasets and Tests
- See /datasets/emergence/spiral-cases.yml
- See /datasets/emergence/torus-harmonics.yml
- Test invariants: preserve_topology, preserve_ratio, phase_lock

## 7. Extending Algorithms
- Replace numeric parameters with ratio objects
- Add stochastic resonance via controlled noise relations
- Generalize to higher-dimensional manifolds

## 8. Implementation Notes
- Use continued fractions for φ approximations when discretizing
- Prefer turns for angles and unitless ratios for scales
- Separate generation (relations) from rendering (geometry/frequency projections)
