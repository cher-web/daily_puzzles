# Product Spec

## One-liner

Send a message, get a puzzle. Solve the puzzle, reveal the message.

## Core Flow

1. **Create** — User picks input type (text, voice note, photo)
2. **Generate** — AI transforms input into a mini puzzle
3. **Preview** — Sender reviews and sends
4. **Notify** — Partner gets a push: "You have a new puzzle"
5. **Solve** — Partner plays the puzzle
6. **Reveal** — Original message/media is unlocked on completion

## Input Methods

Users can send their message via any of these — AI extracts the text content from all of them:

- **Text** — typed message
- **Voice note** — transcribed via speech-to-text
- **Photo** — parsed via OCR / image description (e.g. a handwritten note, a screenshot, a sign)

The input method is just delivery. All puzzle generation works from the extracted text.

## Puzzle Types

AI picks the best puzzle type based on the message content, or the sender can choose.

### Connections (like NYT Connections)
- AI finds 16 words/phrases from the message and related context
- 4 hidden groups of 4, each with a shared theme
- Solver picks groups, 4 mistakes allowed

### Wordle (like NYT Wordle)
- AI picks a key word from the message (5 letters)
- Classic wordle rules: 6 guesses, color-coded feedback
- Hint system can reference the original message context

### Crossword (like NYT Mini)
- Small grid (5x5 or 7x7) generated from message keywords
- Clues are derived from the message content, inside jokes, shared context
- Quick to solve — meant to feel like the NYT Mini

## Screens

### Home
- Today's received puzzle (or empty state prompting partner)
- CTA to create a puzzle for partner

### Create
- Input picker: text / voice / photo
- AI generates puzzle → preview
- Difficulty selector: easy / medium / hard
- Send button

### Solve
- The puzzle UI (varies by type)
- Timer + attempt counter
- Reveal animation on completion

### History
- Calendar or timeline view
- Tap any past puzzle to see the original message
- Stats: streak, solve times, total puzzles exchanged

### Profile
- Partner link/pairing
- Streak counter
- Achievements

## Gamification

- **Daily streaks** — consecutive days sending or solving
- **Solve stats** — time, attempts, shown to both users
- **Achievements** — milestone badges (streaks, speed, volume)
- **Reactions** — after solving, partner can send an emoji or short text reaction back to the sender

## MVP Scope

Ship first with:
- Text input only (voice and photo are v2)
- Connections + Wordle + Mini Crossword
- 1:1 pairing only
- Daily streak tracking
- Basic history view

## Future (v2+)

- Voice note input (speech-to-text)
- Photo input (OCR / image parsing)
- Multiple friends/partners
- Puzzle type preferences
- Shared puzzle packs / themed events
- Monetization: premium puzzle types, extra daily sends
