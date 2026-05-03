# Hollywood Semantics 🎬

A natural language interface for exploring the 50 greatest Hollywood films of all time — powered by a semantic layer and Claude AI.

Ask anything in plain English. No SQL knowledge needed.

---

## What it does

Type a question like *"best crime movies of the 90s"* or *"who starred in The Godfather?"* and get a clean, formatted answer drawn from a real database of 50 iconic films, 82 actors and 15 genres.

---

## What's in this repo

| File | Description |
|---|---|
| `SL/semantic_layer_complete.yaml` | Full 11-section semantic layer — tables, metrics, glossary, joins, pitfalls, examples and assistant guidelines |
| `hollywood_semantics.html` | Self-contained web app — open locally in any browser |
| `hollywood.db` | DuckDB database with 50 movies, 82 actors, 15 genres |
| `README.md` | This file |

---

## The semantic layer

The semantic layer is the core of this project. It has 11 sections:

| Section | Purpose |
|---|---|
| `meta` | Identity card — name, description, owner |
| `dialect` | DuckDB rules, default limits, formatting |
| `glossary` | Fan vocabulary — blockbuster, cult classic, golden era… |
| `tables` | All 5 tables with column rules and behavioral guidelines |
| `joins` | 4 canonical join paths + honesty advisory |
| `metrics` | 3 non-obvious metrics — female lead rate, cult classic score, actor age |
| `default_filters` | 6 always-on rules — min rating 7.0, feature films only… |
| `patterns` | 6 query templates for the most common fan questions |
| `pitfalls` | 20 real mistakes tested against the actual database |
| `examples` | 15 question → SQL pairs, all verified and working |
| `assistant_guidelines` | Tone, response structure, gap handling, deceased actors |

---

## The database

Built from IMDb data, curated to the 50 greatest Hollywood films.

| Table | Rows | Description |
|---|---|---|
| `movies` | 50 | Title, year, runtime, IMDb rating, box office |
| `actors` | 82 | Name, gender, birth year, death year |
| `genres` | 15 | Drama, Crime, Action, Sci-Fi… |
| `movie_genres` | 92 | Links movies to their genres |
| `cast_members` | 80 | Who played what in which film |

---

## How to run it locally

1. Clone this repo
2. Open `hollywood_semantics.html` in your browser
3. Enter your [Anthropic API key](https://console.anthropic.com)
4. Start asking questions

No installation. No server. No dependencies. Everything runs in the browser.

---

## Example questions

- *"What are the top 10 greatest movies of all time?"*
- *"Best crime movies of the 1990s"*
- *"Who starred in The Godfather?"*
- *"Show me cult classics"*
- *"Compare Al Pacino and Marlon Brando"*
- *"Biggest blockbusters by box office"*
- *"Best movies with a female lead"*
- *"Which decade had the best films?"*

---

## How to use it as a Claude Project

1. Go to [claude.ai](https://claude.ai) → Projects → New Project
2. Paste the contents of `SL/semantic_layer_complete.yaml` as the project instructions
3. Start chatting — no API key needed, no setup, free to use

---

## Design decisions

- **Semantic layer first** — all business logic lives in the YAML, not in the code
- **20 pitfalls documented** — each tested against real data to prevent hallucination
- **Fan vocabulary** — glossary maps words like "blockbuster" and "cult classic" to exact SQL rules
- **Honesty by design** — the GPT knows what it can and cannot answer and says so clearly
- **No raw IDs ever shown** — movie_id, actor_id, genre_id stay hidden from users always

---

Built with Claude · DuckDB · sql.js
