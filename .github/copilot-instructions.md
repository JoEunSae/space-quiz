# Project Guidelines

## Build and verification

- The app is a standalone `index.html`; no build, test, or lint command is configured.
- To run it, open `index.html` directly in a browser. Verify the welcome screen, answer selection and feedback, progress and score, final results, and restart flow.
- There is no test runner or single-test command.

## Architecture

- HTML, CSS, quiz data, and browser-side JavaScript all live in `index.html`. The page has welcome, quiz, and results sections; `showScreen()` switches between them.
- `questions` is the source of truth for quiz content. `renderQuestion()` builds answer buttons, `selectAnswer()` scores and displays feedback, and `showResults()` selects the final message.
- Quiz state (`questionIndex`, `score`, and `hasAnswered`) exists only in memory for the current page session. There is no server, API, persistence, or dependency installation.

## Code conventions

- Add or edit quiz content in the `questions` array. Each entry has an `icon`, `prompt`, four `options`, a zero-based `answer` index, and a `fact`; keep the correct index aligned with its option.
- Keep screen-specific elements and styling in the existing sections of `index.html`. Theme colors are CSS custom properties in `:root`; the responsive layout and reduced-motion behavior are in the page stylesheet.
- Preserve the existing interaction and accessibility patterns: use buttons for actions and answer choices, update the progress bar's ARIA value, announce feedback through the live status region, and move focus to the new question or next action as screens change.
