# Project Guidelines

## Project Shape

- This is a dependency-free browser quiz. The complete app lives in [`index.html`](../index.html); do not introduce a server, bundler, framework, or package manager for ordinary changes.
- Keep the three concerns together in `index.html`: the `<style>` block defines the visual system and responsive layout, the HTML defines the quiz/results shell, and the `<script>` owns question data and state transitions.
- Quiz state is intentionally small and local: `currentQuestion` and `score` drive `renderQuestion()`, `selectAnswer()`, and `showResults()`. New quiz behavior should flow through these functions rather than adding parallel state.
- The `questions` array is the single source of truth for the ten questions. Each item must retain the `{ question, answers, correct, explanation }` shape, with `correct` as the zero-based answer index.

## Build, Test, and Lint

- There are no build, test, lint, dependency, or package-manager commands in this repository.
- Validate changes by opening [`index.html`](../index.html) directly in a browser and exercising answer selection, progress/score updates, feedback, the final results screen, and restart behavior.
- When changing interaction or accessibility behavior, also verify keyboard focus and the reduced-motion behavior in a browser.

## Conventions

- User-facing copy is Korean and the document language is `ko`; preserve Korean labels, feedback, and explanations when adding or editing quiz content.
- Use the existing CSS custom properties in `:root` for palette changes. Preserve the colorful space theme, responsive layout, and the existing `.answer` state classes (`.correct` and `.incorrect`) instead of creating duplicate button styles.
- Answer buttons are generated dynamically by `renderQuestion()`. Attach behavior when creating each button and disable all answer buttons after the first selection so a question can only be answered once.
- Preserve the accessibility hooks: semantic headings/fieldset, `role="progressbar"` with updated `aria-valuenow`, live regions for score/feedback, visible `:focus-visible` styles, and `prefers-reduced-motion` support.
- Keep decorative emoji and visual-only labels hidden from assistive technology with `aria-hidden="true"`; use the surrounding semantic text for accessible names.
- Keep the app self-contained and use browser-native APIs only. Avoid adding external fonts, scripts, images, or runtime fetches unless the project requirements explicitly change.
