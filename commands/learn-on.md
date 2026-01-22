---
name: learn-on
description: Enable learning mode as a reminder to extract insights
---

# /learn-on Command

Enable learning mode.

## Usage

```
/learn-on
```

## What It Does

Activates learning mode as a reminder to run `/learn` before ending your session. The `/knowledge` command will show this reminder when learning mode is active.

Note: In v0.1.0, you must still run `/learn` manually. Learning mode is a reminder flag only.

## Instructions

1. Read `knowledge/state.json`
2. Set `learning_mode` to `true`
3. Set `learning_mode_since` to current timestamp
4. Write updated state back
5. Confirm to user that learning mode is enabled
