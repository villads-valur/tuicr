# tuicr

Terminal UI for Code Reviews - A Rust TUI for reviewing changes made by coding agents.

## Overview

`tuicr` is a terminal-based code review tool designed for reviewing changes made by AI coding agents like Claude, Codex, or similar tools. It provides a GitHub-style diff viewing experience with vim keybindings, allowing you to:

- View all changed files in a continuous, scrollable diff
- Leave comments at the file or line level with types (Note, Suggestion, Issue, Praise)
- Mark files as reviewed
- Copy your review as structured Markdown to clipboard for feeding back to the coding agent

## Features

- **Infinite scroll diff view** - All changed files in one continuous scroll (GitHub-style)
- **Vim keybindings** - Navigate with `j/k`, `Ctrl-d/u`, `g/G`, `{/}`, `[/]`
- **Comments** - Add file-level or line-level comments with types
- **Review tracking** - Mark files as reviewed, persist progress to disk
- **Clipboard export** - Copy structured Markdown optimized for LLM consumption
- **Session persistence** - Reviews auto-save and reload on restart

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/tuicr.git
cd tuicr

# Build and install
cargo install --path .
```

## Usage

Run `tuicr` in any git repository with uncommitted changes:

```bash
cd /path/to/your/repo
tuicr
```

### Keybindings

#### Navigation
| Key | Action |
|-----|--------|
| `j/k` | Scroll down/up |
| `Ctrl-d/u` | Half page down/up |
| `Ctrl-f/b` | Full page down/up |
| `g/G` | Go to first/last file |
| `{/}` | Jump to previous/next file |
| `[/]` | Jump to previous/next hunk |
| `Tab` | Toggle focus between file list and diff |
| `h/l` | Focus file list / diff panel |

#### Review Actions
| Key | Action |
|-----|--------|
| `r` | Toggle file reviewed |
| `c` | Add line comment |
| `C` | Add file comment |

#### Comment Mode
| Key | Action |
|-----|--------|
| `1-4` | Set type: Note/Suggestion/Issue/Praise |
| `Ctrl-S` | Save comment |
| `Ctrl-C/Esc` | Cancel |

#### Commands
| Key | Action |
|-----|--------|
| `:w` | Save session |
| `:e` | Copy review to clipboard |
| `:q` | Quit |
| `:x` / `:wq` | Save and quit (prompts to copy if comments exist) |
| `?` | Show help |

## Review Output

When you export your review (`:e` or confirm on `:wq`), `tuicr` copies structured Markdown to your clipboard:

```markdown
# Code Review: myproject

**Reviewed:** 2024-01-15 10:30:00 UTC
**Base Commit:** `abc1234`
**Files Reviewed:** 3/5

## Files

### M `src/auth.rs` [REVIEWED]

#### File Comments
> **[SUGGESTION]** Consider adding unit tests

#### Line Comments
**Line 42:**
> **[ISSUE]** Magic number should be a named constant

---

## Action Items

1. **`src/auth.rs`:42** - Magic number should be a named constant
```

## Session Persistence

Sessions are automatically saved to `~/.local/share/tuicr/reviews/` (XDG compliant). When you reopen `tuicr` in the same repository, your previous review progress (comments, reviewed status) is restored.

## Development

```bash
# Run in development
cargo run

# Run tests
cargo test

# Format code
cargo fmt
```

## License

MIT
