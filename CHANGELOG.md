# Changelog

All notable changes to Claude Knowledge will be documented in this file.

## [0.1.0] - 2026-01-22

### Initial Release - Manual Extraction

Standalone plugin for persistent project knowledge, extracted from claude-router.

**Features:**

| Command | Description |
|---------|-------------|
| `/learn` | Extract insights from current conversation |
| `/learn --deep` | Thorough analysis with forked context |
| `/learn-on` | Enable learning mode (reminder flag) |
| `/learn-off` | Disable learning mode |
| `/knowledge` | View knowledge base status |
| `/learn-reset` | Clear all knowledge (requires confirmation) |

**Knowledge Categories:**
- **Patterns**: Approaches that work well in this codebase
- **Quirks**: Project-specific gotchas and unusual behaviors
- **Decisions**: Architectural choices with their rationale

**Design:**
- v0.1.0 is manual extraction only - `/learn` must be called explicitly
- Learning mode (`/learn-on`) is a reminder flag, not auto-trigger
- Simplified state.json schema (removed router-specific fields)
- Compatible with existing claude-router knowledge directories

**Note:** Future v1.0.0 will add auto-trigger mechanisms (hook-based or notification-based continuous learning).
