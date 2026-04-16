# Diagram Style Guide

> Canonical colors, typography, and conventions for every diagram in the Orbit Tycoon learning series. If you add a new diagram, match these tokens so the whole series reads as one book.

---

## Color tokens

Each token has a semantic meaning. Use the meaning, not the color name, when deciding what to paint.

| Token | Hex | Semantic role | Typical use |
|---|---|---|---|
| `--planet` | `#3B82F6` | Gravity / the planetoid | Planet fill, gravity field, softening radius |
| `--orbiter` | `#F59E0B` | Energy / the player's object | Orbiter glyph, trajectory line, launch impulse |
| `--success` | `#10B981` | Confirmation / green path | Verification checks, "it worked" states |
| `--atmosphere` | `#EF4444` | Danger / atmosphere / pitfalls | Atmosphere ring, decay events, warning callouts |
| `--debris` | `#8B5CF6` | Particles / debris field | Debris dots, stuck-debris visuals, particle emissions |
| `--neutral` | `#6B7280` | UI / scaffolding / axes | Axis labels, grid lines, unemphasized arrows |
| `--bg` | `#0F172A` | Deep-space backdrop | Full-bleed diagram backgrounds, star fields |
| `--fg` | `#E5E7EB` | Primary foreground text | Labels, annotations on dark backgrounds |

### Mermaid `classDef` starter

```mermaid
classDef planet fill:#3B82F6,stroke:#1E40AF,color:#fff;
classDef orbiter fill:#F59E0B,stroke:#B45309,color:#000;
classDef success fill:#10B981,stroke:#065F46,color:#fff;
classDef atmosphere fill:#EF4444,stroke:#991B1B,color:#fff;
classDef debris fill:#8B5CF6,stroke:#5B21B6,color:#fff;
classDef neutral fill:#6B7280,stroke:#374151,color:#fff;
```

---

## Typography in diagrams

- **Font** — default to the diagramming tool's native sans-serif. Don't force a custom face.
- **Label weight** — primary labels bold, annotations regular.
- **Label case** — Sentence case, not Title Case. Never ALL CAPS.
- **Number formatting** — SI units with a thin space (`10 ms`, `1.5 ms`). Decimals max 2 places.
- **Math** — inline math in labels uses Unicode (`r²`, `Δv`, `≈`, `∞`), not LaTeX.

---

## Layout conventions

- **Flow direction** — left-to-right for pipelines, top-to-bottom for hierarchies.
- **Spacing** — generous whitespace; prefer fewer, larger nodes over dense graphs.
- **Arrows** — solid for "always happens," dashed for "optional/conditional," dotted for "data snapshot / cross-tier reference."
- **Legend** — if a diagram uses more than three colors, include an inline legend in the top-right corner.
- **Aspect ratio** — target `16:9` for landscape, `1:1` for radial diagrams (orbits). Avoid extreme tall or wide shapes.

---

## File naming

- `NN-<slug>.svg` for hand-authored SVG (where `NN` is the guide number).
- `NN-<slug>.mmd` for Mermaid source.
- `NN-<slug>.png` for the rendered PNG that ships alongside the `.mmd`.
- Examples: `02-call-graph.svg`, `04-verlet-vs-euler.mmd`, `04-verlet-vs-euler.png`.

---

## Embedding in Markdown

```markdown
![Call graph of orbit-tycoon core systems](images/02-call-graph.svg)
```

Always include descriptive alt text. "Diagram" and "Image" are not descriptive.

---

## Rendering Mermaid → PNG

```bash
mmdc -i docs/images/04-verlet-vs-euler.mmd \
     -o docs/images/04-verlet-vs-euler.png \
     -b transparent \
     -w 1600
```

Width `1600` px renders cleanly on Retina displays and scales down to mobile.
