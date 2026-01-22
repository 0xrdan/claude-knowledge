# Claude Knowledge

**Persistent project knowledge for Claude Code** - Captures patterns, quirks, and decisions that survive session boundaries.

## What This Does

Claude Knowledge builds a persistent understanding of your project by capturing:

- **Patterns**: Approaches that work well in this codebase
- **Quirks**: Project-specific gotchas and unusual behaviors
- **Decisions**: Architectural choices with their rationale

These insights persist across sessions and context compaction, so Claude remembers what it learned even in new conversations.

## Installation

```bash
# Add the marketplace (one-time)
/plugin marketplace add 0xrdan/claude-plugins

# Install the plugin
/plugin install claude-knowledge

# Restart Claude Code to activate
```

## Quick Start

1. **Work on your project** as usual
2. **Run `/learn`** to extract insights from the conversation
3. **Run `/knowledge`** to view accumulated learnings

That's it! Knowledge persists automatically to the `knowledge/` directory.

## Commands

| Command | Description |
|---------|-------------|
| `/learn` | Extract insights from current conversation |
| `/learn --deep` | Thorough analysis with forked context |
| `/learn-on` | Enable learning mode (reminder flag) |
| `/learn-off` | Disable learning mode |
| `/knowledge` | View knowledge base status |
| `/learn-reset` | Clear all knowledge (requires confirmation) |

## How It Works

When you run `/learn`, Claude analyzes the conversation looking for:

1. **Successful approaches** - "This pattern worked for auth in this project"
2. **Unexpected behaviors** - "This module behaves differently than expected"
3. **Decisions made** - "We chose X over Y because of Z"

Each insight is categorized and saved to:
- `knowledge/learnings/patterns.md`
- `knowledge/learnings/quirks.md`
- `knowledge/learnings/decisions.md`

### Example Entry

```markdown
## Quirk: Auth tokens require base64 padding
- **Discovered:** 2026-01-08
- **Location:** src/auth/tokenService.ts
- **Behavior:** JWT tokens use non-standard base64 without padding
- **Workaround:** Use the custom `decodeToken()` helper instead of atob()
- **Confidence:** high
```

## Learning Mode

Enable learning mode as a reminder to extract insights:

```bash
/learn-on   # Enable - /knowledge will remind you to run /learn
/learn-off  # Disable
```

Note: In v0.1.0, learning mode is a reminder flag only. You must still run `/learn` manually.

## Sharing Knowledge

By default, knowledge is gitignored. To share with your team:

1. Edit `knowledge/.gitignore`
2. Comment out or remove `learnings/`
3. Commit the knowledge files

## Migration from claude-router

If you previously used claude-router's knowledge features:

1. Your existing `knowledge/learnings/` files are compatible
2. Simply install claude-knowledge and use the same commands
3. Note: If both plugins are installed, use full command names like `claude-knowledge:learn`

**Recommended:** Use one plugin for knowledge management:
- **claude-knowledge**: If you want ONLY knowledge features
- **claude-router**: If you want routing + knowledge (integrated)

## Version Roadmap

- **v0.1.0** (current): Manual extraction only - `/learn` must be called explicitly
- **v1.0.0** (future): Auto-trigger mechanism (hook-based or notification-based)

## File Structure

```
knowledge/
├── state.json           # Learning mode state
└── learnings/
    ├── patterns.md      # What works well
    ├── quirks.md        # Gotchas and oddities
    └── decisions.md     # Choices with rationale
```

## License

MIT License - see [LICENSE](LICENSE) for details.

---

**Built for the Claude Code community** | [Report Issues](https://github.com/0xrdan/claude-knowledge/issues)
