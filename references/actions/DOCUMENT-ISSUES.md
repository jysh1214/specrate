# Action: Document Issues

When documenting issues found in a change, follow these steps:

1. Locate the folder `.specrate/changes/{change-id}/` with the specified `change-id`.
   - Identify the `change-id` based on the user's description if not provided accurately, and confirm it with the user.
   - If the folder does not exist, inform the user and abort the current action.
   - If the change is in the `ARCHIVED` state, inform the user that archived changes cannot have issues documented, and abort the current action.
2. Read the relevant change files (`proposal.md`, `spec-delta.md`, `tasks.md`, `design.md`, etc.) and the codebase to understand the change and identify the issues.
3. Check if `issues.md` already exists inside the change folder.
   - If it exists, append the new issues to the existing file.
   - Otherwise, create the file using the [DOCUMENT-ISSUES.md](../../assets/templates/DOCUMENT-ISSUES.md) template.
4. For each issue identified or described by the user, document it with:
   - A clear issue title and description.
   - The root cause explaining why the issue exists.
   - A bullet list of suggested fixes describing possible approaches to resolve it.
5. Update the `state` file to contain the text `FAILED` only.
6. Summarize the documented issues and suggest next steps if applicable (e.g., amending the change, re-planning, re-implementing tasks).
