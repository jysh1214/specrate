# Action: Amend Task

When amending an existing task, follow these steps:

1. Locate the folder `.tequila/tasks/{task-id}/` with the specified `task-id`.
   - Identify the `task-id` based on the user's description if not provided accurately, and confirm it with the user.
   - If the folder does not exist, inform the user and suggest creating a new task proposal instead, then abort the current action.
2. Identify the files to be amended based on the user's request (e.g., `proposal.md`, `design.md`, `subtasks.md`, etc.).
3. Make the necessary amendments to the specified files based on the user's instructions.
   - Repeat this step until all requested amendments are made.
   - Check for consistency across related files if applicable to avoid contradictions.
   - Remove directly instead of marking items as deleted if requested.
4. Summarize the amendments made to the task and provide any next steps if applicable.
