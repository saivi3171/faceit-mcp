# faceit-mcp

A standalone [MCP](https://modelcontextprotocol.io/) server that gives Claude live **CS2 FACEIT** data — player stats, match history, side-by-side comparisons, leaderboard, and ELO trend.

Works with **Claude Desktop** and **Claude Code**. Single-file, no framework dependencies beyond `mcp`, `aiohttp`, `aiosqlite`, and `python-dotenv`.

## Tools

| Tool | Description |
|------|-------------|
| `get_player_stats` | ELO, skill level, region, lifetime K/D, HS%, win rate, streaks |
| `get_match_history` | Last N matches — map, W/L, K/D, kills, HS%, K/R |
| `compare_players` | Side-by-side stats for 2–6 FACEIT nicknames |
| `get_recent_form` | Aggregated stats from last N matches: win rate, avg K/D, current streak, per-map breakdown |
| `get_match_details` | Full scoreboard for a match by ID — teams, score, all player stats, multi-kills |
| `get_player_map_stats` | Per-map win rate, K/D, HS%, and K/R from lifetime segments |
| `get_leaderboard` | Registered users ranked by live ELO |
| `get_elo_trend` | Stored ELO snapshots for a registered user |

> All tools except `get_leaderboard` and `get_elo_trend` work for **any** public FACEIT player with just an API key. The leaderboard and ELO trend tools require a SQLite DB with registered users (see [DB setup](#leaderboard--elo-trend)).

## Requirements

- Python 3.12+
- [FACEIT Data API key](https://developers.faceit.com/) (free)

## Setup

**1. Clone and install deps**

```bash
git clone https://github.com/bluemadisonblue/faceit-mcp.git
cd faceit-mcp
pip install -r requirements.txt
```

**2. Set your API key**

Create a `.env` file next to the script:

```
FACEIT_API_KEY=your_key_here
```

Or pass it as an environment variable directly in the config below.

## Connect to Claude Desktop

Add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "faceit-cs2": {
      "command": "python",
      "args": ["C:/full/path/to/faceit-mcp/faceit_mcp_server.py"],
      "env": { "FACEIT_API_KEY": "your_key_here" }
    }
  }
}
```

Config file location:
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

## Connect to Claude Code

```bash
claude mcp add faceit-cs2 -- python /full/path/to/faceit-mcp/faceit_mcp_server.py
```

Then set `FACEIT_API_KEY` in the `.env` file next to the script.

## Example prompts

Once connected, just ask Claude naturally:

- *"What are s1mple's lifetime stats?"*
- *"Show me the last 10 matches for NiKo"*
- *"Compare zywoo, device, and sh1ro side by side"*
- *"How has NiKo been performing over his last 20 matches?"*
- *"Show the full scoreboard for match 1-abc123…"*
- *"Which maps does sh1ro perform best on?"*
- *"Show the leaderboard for our group"*
- *"How has my ELO changed over the last month?"*

## Leaderboard & ELO trend

`get_leaderboard` and `get_elo_trend` read from a local SQLite database. By default the DB lives at `~/.faceit-mcp/data.db` and is created automatically on startup.

To populate it, point `DB_PATH` at a database that has a `users` table:

```
DB_PATH=/path/to/your/bot_data.db
```

If you use the companion [CS2 FACEIT Telegram bot](https://github.com/bluemadisonblue/CS2DATA), set `DB_PATH` to the bot's database and these tools will reflect your registered users automatically.

## Environment variables

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `FACEIT_API_KEY` | Yes | — | FACEIT Data API v4 key |
| `DB_PATH` | No | `~/.faceit-mcp/data.db` | SQLite database path |
| `FACEIT_CIRCUIT_FAILURE_THRESHOLD` | No | `4` | Consecutive failures before circuit opens (`0` to disable) |
| `FACEIT_CIRCUIT_OPEN_SEC` | No | `60` | How long the circuit stays open (seconds) |

## License

MIT
