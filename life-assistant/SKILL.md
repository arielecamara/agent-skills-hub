---
name: life-assistant
description: Use when managing, logging, and tracking daily routines, habits, wellness, deep work, and personal project logs.
---

# Universal Life Assistant Skill

## Overview
A universal, parameterized workflow for daily habit tracking, routine logging, and project progress management. Designed for universal AI agents (Antigravity, Cursor, Claude, ChatGPT, Windsurf) without any hardcoded personal data.

## When to Use
Use when:
- Initializing or updating structured daily journal logs.
- Tracking self-care, household, health, or workout habits.
- Logging deep work blocks, creative projects, or study sessions.
- Mapping natural language daily check-ins to structured checklists.

Do not use when:
- Managing large-scale software codebases or engineering issue trackers.
- Managing multi-user enterprise project sprints.

## Quick Reference

| Action | Example Trigger | Result |
| :--- | :--- | :--- |
| **Setup** | "Initialize Life Assistant configuration" | Creates `./config.md` with the 4 Level-1 categories. |
| **Initialize Log** | "Create daily log for today" | Generates today's log matching `./config.md`. |
| **Check-in** | "I made my bed and worked on the project report" | Checks off confirmed tasks and logs project work. |
| **Archive** | "Archive past year logs" | Compresses and moves old logs at year-end. |

## Core Patterns

### 1. Setup Phase
Before generating daily logs, check if `./config.md` exists. If missing, prompt the user or copy `config.example.md` to initialize the 4 Level-1 categories:
- **1. Routine & Habits**
- **2. Health & Wellness**
- **3. Work & Projects**
- **4. Social & Leisure**

### 2. Daily Log Initialization Rules
- **Creation Rule:** Only create a daily log file (`YYYY-MM-DD.md`) if the user explicitly requests initialization or mentions daily tasks for that day. Do NOT pre-generate empty logs for inactive days.
- **Checkbox Rule:** All tasks must start unchecked (`[ ]`). Never mark an item as checked (`[x]`) unless explicitly confirmed by the user.
- **Atomicity Rule:** Each checkbox represents a single concrete action.

### 3. Natural Language Logging & Work Integration
- **Fuzzy Task Matching:** Map user statements (e.g., *"I cleaned the kitchen"*) to the corresponding task in `./config.md`.
- **Work Logging:** Consolidate work sessions, deliverables, and study progress under **3. Work & Projects**.
- **Interactive Learning:** When the user completes an unlisted recurring task, ask if they want to add it permanently to `./config.md`.

## Common Mistakes

| Mistake | Prevention / Correction |
| :--- | :--- |
| **Auto-checking tasks** | Never check items without explicit user confirmation. |
| **Pre-creating empty days** | Missing daily files signify inactive days; never pre-generate them. |
| **Multiple actions per checkbox** | Ensure every checkbox is a single atomized action. |
| **Bloated lists** | Keep recurring routines concise; log one-off work notes in the daily entry. |
