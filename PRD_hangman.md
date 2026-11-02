# Product Requirements Document: Hangman

## Summary

Provide a standalone, browser-based Hangman word game in `hangman.html`. Players guess a hidden word one letter at a time, using up to six incorrect guesses. The game should work when opened directly, without a build step, external libraries, network access, or changes to the existing Memory Game.

## Problem

Players need a simple, familiar word-guessing game that starts immediately in a browser and is usable with either a keyboard or pointer input.

## Goals

- Offer quick Hangman rounds with a varied, built-in word list.
- Explain each word with a category and hint.
- Make guesses easy with both an on-screen alphabet and physical keyboard input.
- Clearly show guessed letters, incorrect guesses, remaining chances, and the win/loss result.
- Keep the page responsive, accessible, and playable offline.
- Keep Hangman separate from the existing Memory Game.

## Non-goals

- Online multiplayer, user accounts, leaderboards, or network services.
- Downloading word lists or loading external fonts, images, scripts, or libraries.
- Changing or combining the Hangman and Memory Game rules.
- Saving a long-term win history; the win count applies to the current page session.

## Target users

Players looking for a lightweight solo word game, including users who prefer keyboard play or need a layout that works on a small screen.

## User stories

1. As a player, I can see the word category and a hint before making guesses.
2. As a player, I can guess letters by clicking buttons or typing letters.
3. As a player, I can tell which letters are correct or incorrect and how many incorrect guesses remain.
4. As a player, I can start another round after winning or losing.
5. As a keyboard or assistive-technology user, I can understand and operate the game controls.

## Requirements

### Game setup and rounds

- Opening `hangman.html` starts a playable round immediately.
- Select each answer and its category and hint from a local, built-in word list. The game must not disclose the answer before the round ends.
- Show the category and a useful hint throughout the round.
- Start each new round with no guessed letters and zero incorrect guesses.
- Randomize a list of 50 distinct words and use each entry once before repeating any word; avoid the same word at the boundary between cycles. Start a newly shuffled cycle after all 50 words have been played.
- Display a **New word** control so players can restart at any time.

### Guessing and game rules

- Provide one on-screen button for each letter A–Z.
- Also accept alphabetic key presses from the physical keyboard. Ignore modified shortcuts, repeated key events, non-letter input, and letters already guessed.
- Each valid, unique letter counts once. Correct guesses reveal every occurrence of that letter. Incorrect guesses increase the incorrect-guess count by one.
- Draw one additional Hangman part for each incorrect guess. The limit is six incorrect guesses.
- Win when every alphabetic character in the answer has been revealed; punctuation such as the hyphen in `yo-yo` is shown automatically and does not require a guess.
- On a win, announce the result, preserve the revealed answer, and increment the session win counter.
- On a loss, reveal the answer and announce the result after the sixth incorrect guess.
- Disable further letter guesses when a round ends. Starting a new word re-enables guesses and clears round-only progress without clearing the session win count.

### Usability and accessibility

- Use native buttons for letter input and the new-round action.
- Make every interactive control keyboard-focusable with a clearly visible focus indicator.
- Provide understandable accessible names and state for letter buttons, progress, the word display, and the drawing.
- Announce status and round results through a polite live region.
- Use a responsive layout that remains usable on narrow mobile screens without horizontal overflow.
- Respect reduced-motion preferences for animations or transitions.
- Maintain readable contrast for text, controls, correct/incorrect states, and focus indicators.

### Technical constraints

- Keep all markup, styling, word data, and game logic in `hangman.html`.
- Use only browser-native HTML, CSS, and JavaScript; do not require a build step, server, or external dependency.
- Keep the game playable offline and leave `memory-game.html` and its saved data unchanged.
- Document how to open and play Hangman in `README.md`.

## Acceptance criteria

1. Opening `hangman.html` directly presents a new word, category, hint, blank slots, an enabled A–Z keyboard, and zero incorrect guesses.
2. Starting 50 consecutive rounds presents all 50 built-in words exactly once; the next round starts a newly shuffled cycle without immediately repeating the last answer.
3. Guessing a correct letter reveals all its occurrences and does not add a drawing part.
4. Guessing a wrong letter adds exactly one drawing part and decrements the remaining chances.
5. Repeated guesses do not count twice, and non-letter or modified keyboard input does not affect the round.
6. Revealing all alphabetic characters wins the round, announces success, and increments wins once.
7. Six incorrect guesses lose the round, show the full answer, and disable further guesses.
8. **New word** starts a fresh playable round after either result or during play, resets round progress, and preserves the session win count.
9. A hyphenated answer reveals its hyphen automatically and can still be won by guessing its letters.
10. Keyboard and pointer input both work, focus remains visible and predictable, and the layout has no horizontal overflow on a narrow screen.
11. The game uses no external runtime dependencies and does not alter Memory Game behavior.

## Manual verification plan

1. Open `hangman.html` directly in a modern browser and verify a round initializes.
2. Guess a correct letter and an incorrect letter using the on-screen buttons; confirm the word and drawing update appropriately.
3. Repeat a guessed letter and press a non-letter key; confirm neither changes the score.
4. Type letters on the keyboard and verify guesses work without interfering with browser modifier shortcuts.
5. Win a round, verify the answer and win count, then start a new word and confirm the win count remains.
6. Lose a round with six incorrect guesses, verify all drawing parts and the answer are shown, and confirm letter input is disabled.
7. Verify a hyphenated word such as `yo-yo` can be solved without guessing punctuation.
8. Navigate controls with Tab and activate them with Enter or Space; verify visible focus and accessible status updates.
9. Test a narrow viewport and confirm the keyboard and game remain usable without horizontal scrolling.
10. Open `memory-game.html` and confirm the existing game remains available and unchanged.

## Implementation status

The standalone game is implemented in `hangman.html`. Review the acceptance criteria and manual checks when making future changes.
