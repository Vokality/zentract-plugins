---
name: zentract
description: Use Zentract to answer product questions and, after authorization, work with the user's tasks, task creation and updates, projects, clients, time entries, manual time-entry creation, and timers.
---

# Zentract

## Overview

Use Zentract for product information and authorized account actions. Prefer the available Zentract tools for answers about Zentract accounts. If Zentract is unavailable or authorization is missing, say that directly instead of giving an unsupported answer.

## Workflow

1. For product, pricing, FAQ, or API questions, use the public Zentract tools.
2. For requests about "my" work, verify authorization and organization context with `get-current-zentract-context` before listing or changing account data.
3. Use read-only listing tools before writes when the user did not provide an exact ID. For current timer questions, call `get-running-zentract-timer` directly instead of inferring from time-entry lists.
4. For paginated tools, request a focused page size. Zentract currently caps `pageSize` at 25.
5. Create or update tasks only when the user explicitly asks to change task data. If the project ID, task ID, or intended field values are ambiguous, list matching records and ask for confirmation before writing.
6. Start or stop timers only when the user explicitly asks for that action.
7. Report authorization problems plainly. If Zentract needs sign-in or additional access, tell the user what is missing.

## Available Capabilities

Public product tools currently include:

- `get-product-overview`
- `get-pricing-summary`
- `find-faq-answer`
- `get-api-discovery`

Authorized account tools currently include:

- `get-current-zentract-context`
- `list-zentract-tasks`
- `create-zentract-task`
- `update-zentract-task`
- `list-zentract-projects`
- `list-zentract-clients`
- `list-zentract-time-entries`
- `create-zentract-manual-time-entry`
- `get-running-zentract-timer`
- `start-zentract-timer`
- `stop-zentract-timer`

Use each tool's available arguments. Listing tools commonly support pagination, text search, and relevant IDs or status fields. Creating a task requires `projectId` and `title`; optional fields include `description`, `assignedToId`, `status`, `priority`, `dueDate` as an ISO date or datetime, and `isBillable`. Updating a task requires `taskId` and accepts task fields such as `title`, `description`, `assignedToId`, `status`, `priority`, `dueDate`, `isBillable`, and `completeSubtasks` when marking a parent task done. Use `null` to clear nullable task fields such as `description`, `assignedToId`, or `dueDate`. Creating a manual time entry requires `taskId`, `startTime`, and `endTime` ISO datetimes. Starting a timer requires a `taskId`.

## Safety Rules

- Do not infer private Zentract account data from memory, local files, screenshots, or unrelated context. Use Zentract tools for account-specific answers.
- Do not change account data from broad prompts like "look at my tasks" or "what am I working on." Use read-only tools first.
- Create tasks only after identifying the destination project. Update tasks only after identifying the exact task.
- Do not mark a task done, reassign it, clear fields, or complete subtasks unless the user requested or confirmed that specific change.
- Create manual time entries only when the user explicitly asks to add or record historical time.
- Do not expose bearer tokens, OAuth codes, or challenge details beyond what is necessary to explain an auth failure.
- Do not use alternate API calls for private account data unless the user explicitly asks for that fallback and provides the required authorization path.

## Connection Problems

If Zentract tools are not available, tell the user the Zentract connection is not currently available. If account tools fail because authorization is missing or expired, tell the user to reconnect Zentract.
