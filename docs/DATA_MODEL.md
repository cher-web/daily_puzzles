# Data Model

## Users

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| display_name | string | |
| email | string | unique |
| avatar_url | string | nullable |
| created_at | timestamp | |

## Pairs

A pair links two users together.

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| user_a_id | uuid | FK → users |
| user_b_id | uuid | FK → users |
| created_at | timestamp | |
| streak_count | int | current consecutive days |
| streak_last_date | date | last date both sent/solved |

## Puzzles

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| pair_id | uuid | FK → pairs |
| sender_id | uuid | FK → users |
| receiver_id | uuid | FK → users |
| input_type | enum | text, voice, photo |
| input_content | text | original message (encrypted) |
| input_media_url | string | nullable, for voice/photo |
| puzzle_type | enum | word_scramble, crossword, cipher, jigsaw, reveal, audio_reassemble |
| puzzle_data | jsonb | generated puzzle structure (clues, grid, etc.) |
| difficulty | enum | easy, medium, hard |
| status | enum | pending, solved, expired |
| created_at | timestamp | |
| solved_at | timestamp | nullable |
| solve_time_seconds | int | nullable |
| solve_attempts | int | default 0 |

## Achievements

| Field | Type | Notes |
|-------|------|-------|
| id | uuid | primary key |
| user_id | uuid | FK → users |
| type | string | e.g. "streak_7", "speed_demon", "first_photo" |
| earned_at | timestamp | |
