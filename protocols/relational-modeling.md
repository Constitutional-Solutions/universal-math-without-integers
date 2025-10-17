# Protocols: Relational Modeling

This document defines protocols for representing, composing, and validating relations as first-class primitives, independent of integer-based counting. It provides a specification and reference implementation guidelines for building systems from relations, transformations, and resonance alignment.

## 1. Scope and Goals

- Represent relations as core data structures
- Enable composition, inversion, and duality of relations
- Model resonance and compatibility between relations
- Support graph-like and topological structures without integer indexing
- Provide serialization and interchange formats

## 2. Relational Primitives

- Entity: a labeled node-like placeholder defined only by its relations
- Relation: a directional mapping between entities with attributes
- Context: a scope that modulates relation semantics (e.g., scale, medium)
- Constraint: invariants that must hold across transformations

Example schema (YAML-like):
```yaml
entity: E
relation:
  from: A
  to: B
  label: "contains"
  attributes:
    strength: ratio(3,2)
    phase: 0.25turn
context:
  scale: logarithmic
  medium: fluid
constraints:
  - invariant: preserve_ratio
```

## 3. Core Operations

- compose(R1, R2): returns R where R1.to == R2.from
- invert(R): swap endpoints and invert attribute mappings
- dual(R): map to complementary semantics (e.g., contains ↔ contained_by)
- lift(R, C): adapt relation into a new context preserving invariants
- resonate(R1, R2): compute compatibility score (0..1) using phase, ratio alignment

## 4. Relation Types

- Structural: adjacency, containment, overlap, intersection
- Transformational: rotate, scale, reflect, translate
- Functional: map, filter, fold, unfold
- Temporal: precedes, follows, synchronizes, entrains
- Resonant: aligns_with, beats_with, phase_locks_with

## 5. Invariants and Validation

Define invariants as predicate functions on relations/graphs:
- preserve_ratio(A,B): ratio(A,B) is constant under allowed transforms
- preserve_topology(G): connectivity class unchanged
- preserve_phase_alignment(R): phase delta within tolerance

Validation protocol:
1) Declaratively define invariants
2) Associate invariants with contexts
3) Check invariants after each operation

## 6. Interchange Format

Provide a textual, line-oriented format optimized for diffs and human review:
```
entity E:name="spiral-seed"
entity F:name="spiral-growth"
relation R:type=scale from=E to=F ratio=phi context=planar
invariant I:type=preserve_ratio target=R tolerance=1e-3
```

## 7. Reference API Sketch

Language-agnostic pseudocode:
```pseudo
record Entity(id, labels)
record Relation(id, from, to, label, attrs, context)
record Context(id, params)
record Invariant(id, predicate)

fn compose(r1, r2) -> Relation
fn invert(r) -> Relation
fn dual(r) -> Relation
fn lift(r, ctx) -> Relation
fn resonate(r1, r2) -> Ratio

fn validate(graph, invariants) -> Report
```

## 8. Graph Model Without Integers

Graphs are modeled by symbolic identifiers and ratios:
- No numeric indices required; entities and relations are addressed by names/paths
- Distances/weights use ratios, not absolute magnitudes
- Paths are sequences of relations with preserved invariants

## 9. Examples

### 9.1 Containment and Symmetry
```
entity A
entity B
relation R1: contains(A,B)
relation R2: rotate(B, angle=1/6 turn)
invariant: preserve_ratio(A,B)
```

### 9.2 Resonant Alignment
```
entity Seed
entity Pattern
relation Grow: scale(Seed -> Pattern, ratio=phi)
relation Osc: oscillate(Pattern, freq=8 Hz, phase=0)
resonance: phase_locks_with(Grow, Osc) when overtone(3:2)
```

## 10. Implementation Notes

- Prefer symbolic IDs and paths over incrementing integers
- Use angle units as turns (0..1) or radians, not degrees if avoid integer partitions
- Represent ratios as rational pairs or continued fractions for exactness
- Provide lossless serialization with comments for human reasoning

## 11. Roadmap

- Define machine-readable schema (JSON Schema / YAML) for relations and invariants
- Implement validators and visualizers
- Create adapters for different domains (geometry, audio, networks)
- Publish test suites under /datasets/relational-cases

## 12. License and Contributions

Open to extensions and empirical challenges. Propose new relation types and invariants via pull requests with examples and tests.
