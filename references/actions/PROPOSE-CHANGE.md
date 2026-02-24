# Action: Propose Change

When proposing a new change, follow these steps:

1. Ensure `.specrate/changes/` exists; create it if missing.
2. Create a new folder `.specrate/changes/{change-id}/` with a unique `change-id` that describes the change.
   - Scan `.specrate/changes/` for existing change directories and extract the highest numeric prefix (the leading 4-digit number) from existing change ids. Assign the next sequential index, zero-padded to 4 digits. If no changes exist, start at `0001`.
   - Construct the change id as `{index}-{descriptive-part}` (e.g., `0001-add-multi-factor-auth`) or `{index}-{descriptive-part}-{ticket}` if a Jira ticket is provided (e.g., `0001-add-multi-factor-auth-PROJ-123`).
   - Propose a `change-id` based on the user's description if not provided, and confirm it with the user.
   - If the folder already exists, inform the user, suggest amending the existing change instead, and abort the current action.
3. Inside the new folder, create the following required files:
   - `state`: containing the text `PROPOSED` only.
   - `proposal.md`: using the [CHANGES-PROPOSAL.md](../../assets/templates/CHANGES-PROPOSAL.md) template.
   - `spec-delta.md`: using the [CHANGES-SPEC-DELTA.md](../../assets/templates/CHANGES-SPEC-DELTA.md) template.
   - `ticket`: (optional) if the user provides a Jira ticket index, create this file containing the ticket index only (e.g., `PROJ-123`).
4. Fill out the `proposal.md` and `spec-delta.md` files with the relevant information about the change.
5. Optionally, add any additional files related to the change, such as diagrams or supporting documents only if requested by the user.
6. Summarize the created change proposal and provide any next steps if applicable.
