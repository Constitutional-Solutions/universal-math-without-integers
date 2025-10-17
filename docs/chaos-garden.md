# Chaos Garden: Innovation Hub Module

An interactive experimental sandbox for emergent pattern creation, remixing, and real-time ethical harmonics.

## Purpose
- Provide a safe, playful arena to explore algorithmic emergence and co-creation.
- Integrate with the Living Ethical Spiral for harmony checks and feedback loops.
- Enable branching, remixing, and return-to-root flows across modules.

## Core Features
1. Pattern Seeds
   - Cellular automata (1D/2D), L-systems, reaction–diffusion, boids, iterated function systems, dynamical maps.
   - Audio/visual seeds: frequency lattices, polyrhythms, spectrum interference, phase portraits.
   - Narrative seeds: prompt-patterns to generate symbolic structures and consequence graphs.

2. Interactive Sandbox
   - Parameter panels with live tuning and preset morphs.
   - Multi-view canvases: grid, graph, timeline, spectral, and topological views.
   - Snapshot/recording: save states, timelines, and parameter deltas as "gardens".

3. Ethical Harmony Integration
   - Live checks via the Living Ethical Spiral (LES): resonance index, reciprocity score, reversibility, and dignity safeguards.
   - Red/amber/green feedback with suggestions to re-balance systems.
   - Auto-pauses for boundary violations; annotated diffs to show what changed.

4. Branching & Remixing
   - Fork any snapshot or timeline segment into a new garden.
   - Remix recipes: parameter blends, seed crossovers, constraint transplants.
   - Provenance graph: trace lineage back to ethical root and across modules.

5. Crosslinks to Modules
   - Knowledge Garden: store experiments as living notes with queries and tags.
   - Memory Map: visualize provenance and influence flows.
   - Peer Arena: collaborative playtests, votes, and reflective dialogue rounds.
   - Dreamspace Gallery: showcase generative artifacts and performance captures.
   - Logic & Consequence: attach proofs, constraints, invariants, and safety cases.

6. Starter Experiments (Seeds)
   - Gray-Scott reaction–diffusion explorer with palette harmonics.
   - L-system coral/grove generator with wind/noise coupling.
   - Flocking field with ethical disturbance detectors.
   - Frequency tiling and just-intonation morphs with resonance monitors.
   - Map of maps: logistic/henon/ikeda browsers with bifurcation annotations.

## Data Model (YAML/JSON)
- garden: id, title, description, tags, authors, created_at
- seed: type, source, params_schema, default_params
- run: id, garden_id, seed_id, params, metrics, snapshots[], timeline
- snapshot: t, hash, params, metrics, artifact_refs[]
- metric: name, value, bounds, ethical_flags[]
- remix: parent_run_id|snapshot_hash, transform_spec, rationale
- ethics: les_version, scores {resonance, reciprocity, reversibility, dignity}, notes

## File/Folder Layout
- docs/chaos-garden.md (this spec)
- docs/chaos-garden/README.md (how-to + governance)
- docs/chaos-garden/seeds/*.md (seed docs)
- public/chaos-garden/* (web assets)
- src/chaos-garden/* (client modules)
- src/les/* (ethical spiral interfaces)
- data/gardens/*.json (saved experiments)

## Interface Sketch
- Left: Seed select + Parameters
- Center: Canvas tabs (Render | Graph | Timeline | Spectra)
- Right: LES panel with scores and guidance
- Bottom: Transport (play/pause/step), Snapshot, Fork, Remix, Export

## API Contracts
- POST /api/gardens: create garden
- POST /api/runs: start seed run {garden_id, seed_id, params}
- POST /api/runs/{id}/snapshot: capture
- POST /api/runs/{id}/fork: from snapshot/hash
- GET /api/les/assess?run={id}&t={t}: returns scores/guidance
- GET /api/provenance/{id}: lineage graph

## Ethical Spiral Integration
- Subscribe to LES events; compute scores per frame or snapshot.
- Provide affordances to adjust constraints and document tradeoffs.
- Require commentary for red states before resuming.

## Governance & Contribution
- Roles: Gardener (creator), Weaver (integrator), Keeper (ethics), Scribe (docs).
- PR checklist: tests, LES hooks, provenance updates, docs, starter dataset.
- RFC process for new seeds and metrics; sandbox labels and deprecation policy.

## Crosslinking
- Link back to living-ethical-spiral.html for canonical LES concepts.
- Embed see-also links to knowledge-garden.md, memory-map.md, peer-arena.md, dreamspace-gallery.md, logic-and-consequence.md.

## Next Steps
- Scaffold frontend shells and LES adapter.
- Implement 3 starter seeds and metrics.
- Publish initial gardens and invite remix cycles.
