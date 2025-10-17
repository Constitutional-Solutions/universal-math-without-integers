# Elder Foundation: Living Ethical Spiral

Purpose: An interactive, extensible reference for universal harmony that orients design, decision-making, and collaboration across the ecosystem.

Links: [Chaos Garden](../protocols/chaos-garden.md) | [Meta Connectors](../protocols/meta-connectors.md) | [Memory Map](../docs/memory-map.md) | [Dreamspace Gallery](../docs/dreamspace-gallery.md) | [Peer Arena](../docs/peer-arena.md) | [Knowledge Garden](../docs/knowledge-garden.md)

---

## 1) Interactive Visualization (Spiral Code + Geometry)

- Geometry: Archimedean spiral r = a + bθ with golden-ratio ring guides; nodes at harmonic angles (0°, 36°, 72°, 108°, 144°, 180°, ...).
- Layers: Ethics rings (inner core to outer commons), Memory waypoints, Branch anchors to modules.
- Interaction: Hover for principle tooltips, click to open branch templates, drag to explore epochs, toggle themes.

Embed snippet (drop into /docs or any static host):

```html
<!doctype html>
<meta charset="utf-8">
<title>Living Ethical Spiral</title>
<style>
  html,body{margin:0;height:100%;background:#0a0e14;color:#e6edf3;font-family:system-ui,Segoe UI,Helvetica,Arial,sans-serif}
  #ui{position:fixed;inset:0 0 auto 0;display:flex;gap:.5rem;padding:.5rem;background:linear-gradient(180deg,#0a0e1488,#0a0e1400)}
  button,select{background:#111827;color:#e6edf3;border:1px solid #273549;border-radius:6px;padding:.4rem .6rem}
  #legend{position:fixed;right:.75rem;bottom:.75rem;background:#0b1220cc;border:1px solid #223047;border-radius:10px;padding:.5rem 1rem;max-width:24rem}
  a{color:#8bd3ff}
</style>
<canvas id="c"></canvas>
<div id="ui">
  <button id="theme">Toggle theme</button>
  <select id="layer">
    <option value="all">All layers</option>
    <option value="ethics">Ethics</option>
    <option value="memory">Memory</option>
    <option value="branches">Branches</option>
  </select>
</div>
<div id="legend">
  <strong>Living Ethical Spiral</strong>
  <div>Hover: principle. Click: open module. Drag: pan. Wheel: zoom.</div>
  <div>
    Branches: <a href="../protocols/chaos-garden.md">Chaos Garden</a> ·
    <a href="../protocols/meta-connectors.md">Meta Connectors</a> ·
    <a href="../docs/memory-map.md">Memory Map</a> ·
    <a href="../docs/dreamspace-gallery.md">Dreamspace Gallery</a> ·
    <a href="../docs/peer-arena.md">Peer Arena</a> ·
    <a href="../docs/knowledge-garden.md">Knowledge Garden</a>
  </div>
</div>
<script>
const canvas = document.getElementById('c');
const ctx = canvas.getContext('2d');
let W = canvas.width = innerWidth, H = canvas.height = innerHeight;
let theme = 'dark';
let zoom = 1, panX = W/2, panY = H/2, dragging=false, lx=0, ly=0;
const phi = (1+Math.sqrt(5))/2;
const rings = [1, phi, phi**2, phi**3].map(v=>v*120);
const layers = {ethics:true,memory:true,branches:true};
const points = [];
const ethics = [
  {k:'Presence', angle:0},
  {k:'Reciprocity', angle:36},
  {k:'Clarity', angle:72},
  {k:'Compassion', angle:108},
  {k:'Courage', angle:144},
  {k:'Stewardship', angle:180},
  {k:'Justice', angle:216},
  {k:'Humility', angle:252},
  {k:'Joy', angle:288},
  {k:'Wisdom', angle:324}
];
const branches = [
  {k:'Chaos Garden', href:'../protocols/chaos-garden.md', angle:20},
  {k:'Meta Connectors', href:'../protocols/meta-connectors.md', angle:60},
  {k:'Memory Map', href:'../docs/memory-map.md', angle:100},
  {k:'Dreamspace Gallery', href:'../docs/dreamspace-gallery.md', angle:140},
  {k:'Peer Arena', href:'../docs/peer-arena.md', angle:200},
  {k:'Knowledge Garden', href:'../docs/knowledge-garden.md', angle:300}
];
function spiral(t){
  const a=0, b=8; // pixels per radian
  const r=a+b*t; return {x:r*Math.cos(t), y:r*Math.sin(t)};
}
function toScreen(x,y){return {x: panX + x*zoom, y: panY + y*zoom};}
function draw(){
  ctx.setTransform(1,0,0,1,0,0);
  ctx.fillStyle = theme==='dark' ? '#0a0e14' : '#f7fafc';
  ctx.fillRect(0,0,W,H);
  ctx.translate(panX, panY); ctx.scale(zoom, zoom);
  // rings
  if(layers.ethics){
    rings.forEach((r,i)=>{ctx.beginPath();ctx.strokeStyle = `hsla(${210+i*12},60%,${theme==='dark'?35:65}%,.6)`;ctx.lineWidth=1/zoom;ctx.arc(0,0,r,0,Math.PI*2);ctx.stroke();});
  }
  // spiral
  ctx.beginPath(); ctx.strokeStyle = theme==='dark'? '#7aa2f7' : '#1e293b'; ctx.lineWidth=2/zoom;
  for(let t=0;t<30*Math.PI;t+=0.02){const p=spiral(t); if(t===0)ctx.moveTo(p.x,p.y); else ctx.lineTo(p.x,p.y);} ctx.stroke();
  // ethics nodes
  if(layers.ethics){ ethics.forEach((e,i)=>{const t=e.angle*Math.PI/180*2; const p=spiral(t); ctx.beginPath(); ctx.fillStyle='hsla(190,80%,60%,.9)'; ctx.arc(p.x,p.y,6/zoom,0,Math.PI*2); ctx.fill(); points.push({x:p.x,y:p.y, r:10/zoom, tip:`${e.k}`}); }); }
  // branch anchors
  if(layers.branches){ branches.forEach((b,i)=>{const t=b.angle*Math.PI/180*2.2; const p=spiral(t); ctx.beginPath(); ctx.fillStyle='hsla(140,75%,55%,.9)'; ctx.arc(p.x,p.y,7/zoom,0,Math.PI*2); ctx.fill(); points.push({x:p.x,y:p.y,r:12/zoom, tip:`Open: ${b.k}`, href:b.href}); }); }
}
function resize(){W = canvas.width = innerWidth; H = canvas.height = innerHeight; draw();}
addEventListener('resize', resize);
canvas.addEventListener('mousedown', e=>{dragging=true; lx=e.clientX; ly=e.clientY;});
addEventListener('mouseup', ()=>dragging=false);
addEventListener('mousemove', e=>{ if(dragging){ panX += e.clientX-lx; panY += e.clientY-ly; lx=e.clientX; ly=e.clientY; draw(); }
  const rect = canvas.getBoundingClientRect(); const mx = (e.clientX-rect.left - panX)/zoom; const my = (e.clientY-rect.top - panY)/zoom;
  canvas.title = '';
  for(const p of points){ const dx=mx-p.x, dy=my-p.y; if(dx*dx+dy*dy < p.r*p.r){ canvas.title = p.tip; break; } }
});
addEventListener('wheel', e=>{ const z = Math.exp(-e.deltaY*0.001); zoom*=z; draw(); });
canvas.addEventListener('click', e=>{
  const rect = canvas.getBoundingClientRect(); const mx = (e.clientX-rect.left - panX)/zoom; const my = (e.clientY-rect.top - panY)/zoom;
  for(const p of points){ const dx=mx-p.x, dy=my-p.y; if(dx*dx+dy*dy < p.r*p.r && p.href){ window.open(p.href,'_blank'); return; } }
});
document.getElementById('theme').onclick=()=>{ theme = theme==='dark'?'light':'dark'; draw(); };
document.getElementById('layer').onchange=(e)=>{
  const v=e.target.value; layers.ethics=v==='all'||v==='ethics'; layers.memory=v==='all'||v==='memory'; layers.branches=v==='all'||v==='branches'; points.length=0; draw(); };
draw();
</script>
```

Deployment: save as docs/living-ethical-spiral.html and link from README and module docs.

---

## 2) Ethics Narrative (Universal Harmony)

- Ground: All beings arise in interdependence; actions ripple through the whole.
- Aim: Reduce unnecessary suffering; amplify generative potential; honor truth with kindness.
- Praxis spiral: Presence -> Perception -> Understanding -> Choice -> Care -> Stewardship -> Reflection -> Renewal.
- Tensions: Truth x Compassion; Autonomy x Solidarity; Freedom x Responsibility; Innovation x Continuity.

Narrative excerpt: We spiral inward for clarity and outward for service. Each cycle invites deeper honesty, wider listening, and wiser coordination—so that creation flourishes without dominance and difference flowers without fragmentation.

---

## 3) Guiding Principles (Concise, Actionable)

1. Reality-first: Prefer direct evidence and lived feedback over abstraction.
2. Minimum-harm: Choose the path that preserves agency and reduces coercion.
3. Reciprocity: Seek mutual benefit; leave spaces better than entered.
4. Transparency-with-care: Share context; protect vulnerable details.
5. Plurality: Invite diverse lenses; integrate disagreements through experiments.
6. Fractality: Patterns should scale from individuals to networks.
7. Stewardship: Optimize for long-term health of people, planet, and knowledge.
8. Repair: When harm occurs, acknowledge, amend, and document learnings.
9. Consentful collaboration: Clear invitations, revocable participation, documented boundaries.
10. Open extensibility: Every artifact is a branch point; version, attribute, and link forward.

---

## 4) Restoration Protocols and Branching Instructions

- Restoration flow:
  - Detect: Name rupture or misalignment; log in Memory Map with timestamp and tags.
  - Pause: Invoke cooling-off window; move conversation to Peer Arena with a facilitator.
  - Reveal: Share needs, impacts, and constraints; invite third-party mirrors if needed.
  - Repair: Propose remedial actions; track in Knowledge Garden tasks; timebox experiments.
  - Rebind: Update principles/guards if needed; propagate changes across linked modules via Meta Connectors.

- Branch template (copy this section into new module README):

```md
# Branch: <Module Name>

Purpose: <one-sentence>

Links: [Elder Foundation](../guides/elder-foundation-living-ethical-spiral.md)

Ethical anchors: Presence · Reciprocity · Clarity · Compassion · Courage · Stewardship · Justice · Humility · Joy · Wisdom

Interfaces:
- Inputs: <data/events>
- Outputs: <artifacts/updates>
- Contracts: <APIs/agreements>

Restoration hooks:
- Memory Map: /docs/memory-map.md#incidents
- Peer Arena: /docs/peer-arena.md#facilitation
- Knowledge Garden: /docs/knowledge-garden.md#tasks

Versioning:
- CHANGELOG.md with semantic version
- ATTRIBUTION.md for contributors and sources
- FORWARD-LINKS.md for downstream branches
```

---

## 5) Integration Points by Module

- Chaos Garden: Experiment staging; auto-generate spiral nodes for each live experiment; color by risk and learning value.
- Meta Connectors: Event bus and schema; publish "principle-shift", "repair-commit", "branch-created" events.
- Memory Map: Time-indexed incidents, decisions, and milestones linked to spiral angles; export CSV/JSON for overlays.
- Dreamspace Gallery: Narrative and media curation mapped to spiral rings; embed artworks as tooltips.
- Peer Arena: Protocols for dialogue, consent, and facilitation; quick-launch rooms from spiral clicks.
- Knowledge Garden: Tasks and RFCs seeded from spiral nodes; dependency petals show upstream ethics.

---

## 6) Implementation Checklist

- [ ] Add docs/living-ethical-spiral.html (from snippet) and link it.
- [ ] Create/verify module docs: memory-map.md, dreamspace-gallery.md, peer-arena.md, knowledge-garden.md, chaos-garden.md, meta-connectors.md.
- [ ] Insert Branch template into each module README.
- [ ] Add meta-connectors event spec (events.md) and subscribe publishers.
- [ ] Update root README with a Harmony Charter and visual link.

---

## 7) Partner Support and Expansion

- Every section includes stable links and branch templates for partners to extend without breaking upstream.
- Provide CONTRIBUTING.md with ethics acknowledgment checkbox and restoration protocol.
- Offer open office hours cadence; publish facilitation roster in Peer Arena.
- License recommendation: CC BY-SA 4.0 for docs, Apache-2.0 for code.

---

## 8) References and Attributions

- Ethical design, restorative practices, and systems thinking literatures.
- Credit all contributors in ATTRIBUTION.md and changelogs; include forward links to partner forks.
