# Action: Plan Task

When planning a proposed task, follow these steps:

1. Locate the folder `.tequila/tasks/{task-id}/` with the specified `task-id`.
   - Identify the `task-id` based on the user's description if not provided accurately, and confirm it with the user.
   - If the folder does not exist, inform the user and suggest proposing a new task instead, then abort the current action.
   - If the task is not in the `PROPOSED` state, inform the user and abort the current action.
2. Create the following required files inside the task folder:
   - `subtasks.md`: using the [TASKS-SUBTASKS.md](../../assets/templates/TASKS-SUBTASKS.md) template.
   - Optionally, `design.md`: using the [TASKS-DESIGN.md](../../assets/templates/TASKS-DESIGN.md) template.
3. Fill out the `subtasks.md` file (and `design.md` if present) with the relevant information about the task.
   - If `design.md` is present, fill it out first since it may inform the subtasks.
   - Create actionable subtasks in `subtasks.md` using task list grammar (e.g., `- [ ]` for pending subtasks).
4. Update the `state` file to contain the text `PLANNED` only.
5. Summarize the planned task and provide any next steps if applicable.
