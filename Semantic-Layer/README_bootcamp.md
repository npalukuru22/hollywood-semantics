# Semantic Layer — Hollywood Semantics 🎬

**Bootcamp project:** Building a text-to-SQL GPT using a semantic layer.

**Live demo:** https://claude.ai/share/7e7ebc68-cdf8-4c9a-9cc1-4187d1b8f56c  
**Full repo:** https://github.com/npalukuru22/hollywood-semantics

---

## What I built

A natural language interface for exploring the 50 greatest Hollywood films of all time. Ask anything in plain English — ratings, box office, actors, genres, decades. No SQL knowledge needed.

---

## The goal

> A semantic layer describing at least a couple of tables, a working GPT that uses it, and a couple of example queries.

**Delivered:**
- 5 tables fully documented
- 11-section semantic layer
- Working GPT as a Claude Project and as a local web app
- 15 verified example queries

---

## What a semantic layer is

A translation layer between a raw database and plain English questions. It defines tables, metrics, dimensions and business rules so an AI can write correct SQL without guessing.

Think of it as the instruction manual you hand to the AI before it answers any question.

---

## The database

Built from IMDb data — 50 iconic Hollywood films curated by rating.

| Table | Rows | Description |
|---|---|---|
| `movies` | 50 | Title, year, runtime, IMDb rating, box office |
| `actors` | 82 | Name, gender, birth year, death year |
| `genres` | 15 | Drama, Crime, Action, Sci-Fi… |
| `movie_genres` | 92 | Links movies to their genres |
| `cast_members` | 80 | Who played what in which film |

---

## The semantic layer

11 sections, designed field by field:

| Section | What it does |
|---|---|
| `meta` | Identity card — name, description, owner |
| `dialect` | DuckDB rules, default limit 10, max 25, formatting |
| `glossary` | Fan vocabulary — blockbuster, flop, cult classic, golden era… |
| `tables` | All 5 tables with column rules and behavioral guidelines |
| `joins` | 4 canonical join paths + honesty advisory for missing data |
| `metrics` | Female lead rate, cult classic score, actor age at release |
| `default_filters` | Always-on rules — min rating 7.0, feature films only, English titles |
| `patterns` | Query templates for the most common fan questions |
| `pitfalls` | 20 real mistakes simulated and tested against the actual database |
| `examples` | 15 question → SQL pairs, all verified and working |
| `assistant_guidelines` | Tone, response structure, gap handling, deceased actors |

---

## Key design decisions

**Glossary defines fan vocabulary precisely**
Words like "blockbuster" ($500M+ box office), "cult classic" (high rating + low gross) and "golden era" (1930-1960) are mapped to exact SQL rules so the AI never guesses.

**20 pitfalls tested against real data**
Before writing the pitfalls section I ran simulations against the actual database. Real problems found: duplicate rows from multi-genre joins, old films with low box office due to era not quality, franchise films appearing as separate rows, partial cast records presented as complete.

**Honesty by design**
The semantic layer explicitly tells the AI what it cannot answer — Oscar data, directors, quotes, complete cast lists — and instructs it to say so clearly and point to IMDb.com instead of hallucinating.

**Two versions built**
- Claude Project — conversational, free, shareable with anyone who has a Claude account
- Local web app (`index.html`) — executes real SQL against a live DuckDB database in the browser

---

## Example questions it answers

- *"What are the top 10 greatest movies of all time?"*
- *"Best crime movies of the 1990s"*
- *"Who starred in The Godfather?"*
- *"Show me cult classics"*
- *"Compare Al Pacino and Marlon Brando"*
- *"Which decade had the best films?"*
- *"Best movies with a female lead"*
- *"How old was Al Pacino in The Godfather?"*

---

## How to run locally

1. Clone https://github.com/npalukuru22/hollywood-semantics
2. Open `index.html` in your browser
3. Enter your Anthropic API key
4. Start asking questions

No installation. No server. Everything runs in the browser.

---

## How to use as a Claude Project (free)

1. Go to claude.ai → Projects → New Project
2. Paste `semantic_layer_complete.yaml` as the project instructions
3. Start chatting — no API key needed

---

Built with Claude · DuckDB · sql.js · IMDb data
