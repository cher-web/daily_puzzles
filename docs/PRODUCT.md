# Product & Design Spec

## One-liner

Send a message, get a puzzle. Solve the puzzle, reveal the message.

---

## Core Flow

1. **Create** — User picks input type (text, voice note, photo)
2. **Generate** — AI extracts text and transforms it into a mini puzzle
3. **Preview** — Sender reviews puzzle, picks type/difficulty, and sends
4. **Notify** — Partner gets a push: "You have a new puzzle"
5. **Solve** — Partner plays the puzzle
6. **Reveal** — Original message is unlocked on completion
7. **React** — Solver sends an emoji or short text reaction back

---

## Input Methods

Users can send their message via any of these — AI extracts the text content from all of them:

- **Text** — typed message
- **Voice note** — transcribed via speech-to-text
- **Photo** — parsed via OCR / image description (e.g. a handwritten note, a screenshot, a sign)

The input method is just delivery. All puzzle generation works from the extracted text.

---

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

---

## Screens

### 1. Onboarding

#### 1a. Welcome
- App logo + tagline: "Puzzles made personal"
- Two CTAs: **Sign Up** / **Log In**
- Warm, playful illustration — two people connected by puzzle pieces

#### 1b. Sign Up
- Fields: display name, email, password
- Or: **Continue with Apple / Google**
- Minimal — get to pairing fast

#### 1c. Pair with Partner
- Two paths:
  - **Send invite** — generates a unique link or 6-digit code, shareable via text/iMessage/WhatsApp
  - **Enter code** — paste or type a code received from partner
- State: waiting for partner to accept (show a simple animation/waiting state)
- Once paired: celebration animation → land on Home

---

### 2. Home

The daily hub. Two clear states:

#### 2a. Puzzle Waiting (you have an unsolved puzzle)
- Card showing:
  - Partner's avatar + name
  - Puzzle type icon + label (e.g. "Connections")
  - Timestamp ("Sent 2 hours ago")
  - Difficulty badge (Easy / Medium / Hard)
- Large **Play** button
- Below: streak counter ("🔥 12 day streak")

#### 2b. No Puzzle Today
- Empty state: "No puzzle yet today"
- Subtle prompt: "Send one to [partner name] to keep the streak alive"
- CTA: **Create a Puzzle**

#### 2c. Puzzle Solved (already completed today)
- Solved card with:
  - Your solve stats (time, attempts)
  - The reaction you sent
  - Tap to revisit the revealed message
- CTA: **Create a Puzzle** (if you haven't sent one today)

#### Navigation
- Bottom tab bar: **Home** | **History** | **Profile**

---

### 3. Create

#### 3a. Input Picker
- Three large tap targets, vertically stacked or in a row:
  - **Text** — keyboard icon
  - **Voice** — microphone icon (v2, shown as locked/coming soon in MVP)
  - **Photo** — camera icon (v2, shown as locked/coming soon in MVP)

#### 3b. Compose (Text)
- Large text input area
- Placeholder: "Write a message for [partner name]..."
- Character guidance (not a hard limit): "Longer messages make richer puzzles"
- **Next** button

#### 3c. AI Processing
- Brief loading state with animation
- "Creating your puzzle..."
- AI extracts keywords, themes, and generates puzzle options

#### 3d. Puzzle Preview
- Show the generated puzzle as the solver will see it (playable preview)
- Options:
  - **Puzzle type selector** — toggle between Connections / Wordle / Crossword (AI recommends one, highlighted as "Best fit")
  - **Difficulty** — Easy / Medium / Hard toggle
  - **Regenerate** — "Try another" button to get a fresh version
- **Send** button (prominent)
- **Back** to edit message

---

### 4. Solve

Each puzzle type has its own solve screen. Shared elements across all:

- **Header**: partner's avatar + "A puzzle from [name]"
- **Timer**: running clock (can be hidden in settings)
- **Attempts/mistakes counter**
- Subtle hint button (uses one of limited hints)

#### 4a. Solve — Connections
- 4x4 grid of 16 word tiles
- Tap to select 4, then tap **Submit**
- Correct group: tiles animate into a colored row at top, group label revealed
- Wrong guess: shake animation, mistake counter increments
- Colors: yellow (easiest) → green → blue → purple (hardest)
- Win: all 4 groups found
- Lose: 4 mistakes used

#### 4b. Solve — Wordle
- 6 rows of 5 letter tiles
- On-screen keyboard at bottom
- Type a word → tap **Enter**
- Tile flip animation revealing colors:
  - Green: correct letter, correct position
  - Yellow: correct letter, wrong position
  - Gray: letter not in word
- Win: correct word guessed
- Lose: 6 guesses used, word revealed

#### 4c. Solve — Crossword
- Mini grid (5x5 or 7x7)
- Tap a cell to select, highlight the across/down word
- Clue shown above or below the grid
- On-screen keyboard
- Navigate between clues with arrows or swipe
- Auto-advance to next empty cell
- Win: all cells filled correctly

#### 4d. Reveal (post-solve)
- Transition animation: puzzle pieces dissolve / unfold / unlock
- Original message displayed in a card:
  - Text message shown in a styled "letter" or "note" format
  - (v2: photo shown full screen, voice note has play button)
- Below the message:
  - Solve stats: time, attempts/mistakes
  - **React** — row of emoji quick-picks (❤️ 😂 😮 🥰 🔥 😭) + text input option
  - **Share** — share your solve stats as an image (like Wordle share)

---

### 5. History

#### 5a. Timeline View
- Scrollable list, grouped by date
- Each entry shows:
  - Date
  - Puzzle type icon
  - Direction: "From [name]" or "To [name]"
  - Status: Solved (with time) / Unsolved / Expired
  - Partner's reaction emoji (if applicable)
- Tap to expand: see original message + solve stats

#### 5b. Stats Summary (top of history screen)
- Total puzzles exchanged
- Current streak + longest streak
- Average solve time
- Favorite puzzle type (most played)

---

### 6. Profile

#### 6a. Your Profile
- Avatar (tap to change)
- Display name
- Partner: [name] — paired since [date]
- **Unpair** option (with confirmation dialog)

#### 6b. Achievements
- Grid of badge icons, unlocked ones highlighted:
  - **First Puzzle** — send your first puzzle
  - **First Solve** — solve your first puzzle
  - **7-Day Streak** — 7 consecutive days
  - **30-Day Streak** — 30 consecutive days
  - **Speed Demon** — solve in under 30 seconds
  - **Perfect Game** — solve Connections with 0 mistakes
  - **Wordsmith** — solve Wordle on first guess
  - **Century** — 100 puzzles exchanged
- Tap a badge for details + date earned
- Locked badges show silhouette + requirement

#### 6c. Settings
- Notifications on/off
- Show/hide timer during solve
- Dark mode / light mode
- Account: change email, password, delete account
- **Send Feedback**

---

## Gamification

- **Daily streaks** — consecutive days where both users sent or solved a puzzle
- **Solve stats** — time and attempts, shown to both users after solve
- **Achievements** — milestone badges (see Profile section)
- **Reactions** — after solving, partner can send an emoji or short text reaction back to the sender

---

## Visual Direction

- **Tone**: warm, playful, intimate — not corporate or competitive
- **Color palette**: soft pastels with one vibrant accent color. Puzzle type colors should be distinct but harmonious
- **Typography**: rounded, friendly sans-serif for headers. Clean readable body font
- **Illustrations**: minimal, line-art style — abstract puzzle motifs, not literal characters
- **Animations**: satisfying micro-interactions everywhere — tile flips, streak fire, reveal unlocks, reaction pops
- **Dark mode**: full support, muted tones, same warmth

---

## Interaction Notes

- All puzzle interactions should feel tactile — tiles should respond to touch with subtle scale/haptic feedback
- Reveal animation is the emotional payoff — make it feel like unwrapping a gift
- Streak counter should be ever-present on Home — it's the primary retention hook
- Push notifications are critical — "You have a puzzle from [name]" is the core re-engagement loop
- Pairing should feel special — it's a commitment moment, not just adding a contact

---

## States & Edge Cases

| Scenario | Behavior |
|----------|----------|
| Partner hasn't signed up yet | Show waiting state with option to resend invite |
| No puzzle received today | Empty state on Home with prompt to send one |
| Both send puzzles same day | Both appear — each user sees their received puzzle on Home |
| Unsolved puzzle from yesterday | Stays accessible in History, marked as "missed" |
| Streak break | Streak resets to 0, show a gentle "Start a new streak" message (not punishing) |
| User unpairs | Confirm dialog, history is preserved but read-only, user returns to pairing screen |
| Long message input | AI selects most meaningful keywords/phrases — not every word makes it into the puzzle |
| Very short message | AI supplements with related words/context to fill puzzle requirements |
| Solver gives up | "Give up" option after minimum time/attempts — reveals message but marks as unsolved |

---

## MVP Scope

Ship first with:
- Text input only (voice and photo shown as coming soon)
- Connections + Wordle + Mini Crossword
- 1:1 pairing only
- Daily streak tracking
- Basic history view
- Emoji reactions

## Future (v2+)

- Voice note input (speech-to-text)
- Photo input (OCR / image parsing)
- Multiple friends/partners
- Puzzle type preferences per pair
- Shared puzzle packs / themed events
- Monetization: premium puzzle types, extra daily sends
