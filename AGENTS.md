# Space Exploration Quiz

Single-file, zero-dependency quiz app: everything (HTML, CSS, JS) lives in [index.html](index.html).

## Rules
1. Everything stays in `index.html`. Do not add files, frameworks, npm packages, CDNs, or external fonts/images.
2. It must work when opened directly from disk (`file:///`): no `fetch`, ES modules, or server.
3. Change only what was asked. If the request says "change nothing else", touch only the named element.
4. Reuse the `:root` color variables; do not invent new palettes.
5. Never make answers rely on color alone; keep the ✓/✗ marks and text.
6. Every new animation must be disabled by the `prefers-reduced-motion` block.
7. Use `textContent` for any text that comes from the `questions` data.
8. When adding or removing questions, also update the hard-coded `aria-valuemax="10"` and "of 10" text in the markup.
9. After every edit, reload the page in the integrated browser and click through it.

## Run / verify
- No build or tests. Open `file:///c:/work/space_quiz/index.html` in the VS Code integrated browser and reload after edits.
- Verify interactively: start quiz, answer right and wrong, reach the results screen, check keyboard flow (Tab, A–D keys).

## Structure in `index.html`
- **CSS**: theme colors are custom properties in `:root` — reuse them instead of new hex values. Answer buttons use `.option`, with `.correct` / `.incorrect` state classes and `pop` / `shake` keyframes.
- **Markup**: three `<section>` screens (`#start`, `#quiz`, `#results`) toggled via the `.hidden` class by `show(name)`.
- **JS**: the `questions` array (`q`, `options`, `answer` index, `fact`) drives everything; flow is `startQuiz` → `renderQuestion` → `choose` → `nextQuestion` → `showResults`.

## Accessibility (do not regress)
- `#feedback` is `role="status"` / `aria-live`; the progress bar updates `aria-valuenow`/`aria-valuetext`.
- Focus moves to the question heading, then the Next button, then the results title; keep this when changing flow.
- Keep visible `:focus-visible` rings.
