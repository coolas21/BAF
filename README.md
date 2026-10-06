# Pilot Greetings Automations (Power Automate)

Flows that send birthday and anniversary card greetings to pilots by driving
a browser (read data, pick card on website, send).

## How to share a flow
1. In Power Automate Desktop, open the flow in the designer.
2. Press **Ctrl+A** then **Ctrl+C** to copy all actions. They paste as plain text
   (the action definitions), which is what we want.
3. Paste into the matching file in `flows/` (replace the placeholder text).
4. **Remove anything sensitive** first: passwords, API keys, personal emails,
   pilot personal data. Replace with `<REDACTED>`.
5. Commit/push (or just tell Claude the files are updated).

## Files
- `flows/birthday-flow.txt`      - paste birthday flow here
- `flows/anniversary-flow.txt`   - paste anniversary flow here
- `ENVIRONMENT.md`               - fill in the details about your setup
