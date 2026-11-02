# Hangman Game

A lightweight, standalone Hangman game that runs in your browser. Choose letters to uncover the hidden word, use the category and hint to guide your guesses, and solve the word before the drawing is complete.

## Get started

1. Download or clone this repository.
2. Open `hangman.html` in a modern web browser.
3. Choose a letter using the on-screen keyboard or your physical keyboard.

No installation, build step, web server, or internet connection is required.

## How to play

- Guess a word one letter at a time.
- You can make up to **six incorrect guesses**.
- Correct guesses reveal every occurrence of that letter.
- Use the displayed category and hint for help.
- Select **New word** to start another round at any time.
- The game has 50 words and shuffles them so each word appears once before the list repeats.
- Your win count is kept for the current page session.

## Features

- On-screen A–Z keyboard and physical keyboard input.
- Responsive layout for desktop and mobile screens.
- Accessible controls, visible keyboard focus, and announced game status.
- Reduced-motion support.
- Fully playable offline with no external libraries or assets.

## Project files

- `hangman.html` — the complete game, including its styles, word list, and game logic.
- `PRD_hangman.md` — product requirements and acceptance criteria.

## Requirements

Any modern browser with JavaScript enabled. All game code and word data are included in `hangman.html`.
