# Knowledge Garden (Onboarding)

## Overview
The Knowledge Garden is the gateway for newcomers to learn how to “walk the spiral” through stories, tutorials, and interactive practice.

## Spiral-Linked Extensions

### 1. Onboarding Story: Walking the Spiral

> You stand at the edge of a living spiral, each turn a chapter of understanding. A gentle voice asks: “Will you begin with care?” You nod, and the path illuminates.

- Chapter 1: Care and Consent
  - Learn the foundations of ethical presence
  - Practice consent in knowledge sharing
  - Reference: `./living-ethical-spiral.html#care-consent`

- Chapter 2: Listening for Harmony
  - Learn to sense resonance and disharmony
  - Practice with visual and audio examples
  - Reference: `./resonance-harmonics.md`

- Chapter 3: Patterns in Motion
  - Explore continuous patterns in geometry and music
  - Build a phyllotaxis spiral and listen to its song
  - Reference: `./continuous-patterns.md`

- Chapter 4: Consequence and Responsibility
  - Map actions to outcomes along the spiral
  - Practice consequence tracing with scenarios
  - Reference: `./logic-and-consequence.md`

- Chapter 5: Wisdom in Relation
  - See how knowledge grows through relation and reciprocity
  - Practice mapping your insights in the Memory Map
  - Reference: `./memory-map.md`

- Chapter 6: Create with Beauty
  - Use the Dreamspace Gallery to express your understanding
  - Compose a simple animation with harmonic music
  - Reference: `./dreamspace-gallery.md`

- Chapter 7: Share and Validate
  - Submit your creation to Peer Arena for feedback
  - Reflect on revisions and celebrate growth
  - Reference: `./peer-arena.md`

### 2. Interactive Tutorials

```javascript
const OnboardingTutorials = {
  start() {
    return this.chapter('Care and Consent')
      .then(() => this.chapter('Listening for Harmony'))
      .then(() => this.chapter('Patterns in Motion'))
      .then(() => this.chapter('Consequence and Responsibility'))
      .then(() => this.chapter('Wisdom in Relation'))
      .then(() => this.chapter('Create with Beauty'))
      .then(() => this.chapter('Share and Validate'));
  },
  
  chapter(name) {
    MemoryMap.captureEvent({
      type: 'tutorial_step',
      module: 'knowledge_garden',
      data: { name }
    });
    return Promise.resolve(true);
  }
};
```

### 3. Accessibility and Support

- Alternative text for all visuals
- Audio narration and captioning
- Reduced motion settings
- Glossary of spiral terms in plain language
- Community mentorship links

### 4. Spiral Reference Points

- **Living Ethical Spiral**: `./living-ethical-spiral.html`
- **Resonance Harmonics**: `./resonance-harmonics.md`
- **Continuous Patterns**: `./continuous-patterns.md`
- **Logic & Consequence**: `./logic-and-consequence.md`
- **Memory Map**: `./memory-map.md`
- **Dreamspace Gallery**: `./dreamspace-gallery.md`
- **Peer Arena**: `./peer-arena.md`

---

*The Knowledge Garden welcomes every learner with care, guiding each step along the spiral toward beauty, wisdom, and shared harmony.*
