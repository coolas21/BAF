# Request: allow Power Automate Desktop browser automation on my work PC

**Summary:** Microsoft Power Automate Desktop (PAD) can no longer control Microsoft Edge on my PC. I use it for an approved-business task (sending birthday and anniversary greetings to pilots from the SkyWest Online crew reports). I believe an endpoint protection rule (SentinelOne) is blocking a Microsoft-signed component. I'm asking security to review it and, if appropriate, allow it. I'm not asking anyone to disable protection.

## Evidence
- Edge extension "Microsoft Power Automate" is installed and enabled; its ID matches the allowed origin in the PAD native-messaging manifest.
- Native-messaging registration (`com.microsoft.pad.messagehost`), `PAD.ChromiumManifest.json` and `PAD.BrowserNativeMessageHost.exe` all exist.
- No Edge native-messaging or extension policies are configured (checked `edge://policy`).
- The extension service-worker console reports: `Unchecked runtime.lastError: Failed to start native messaging host.`
- `PAD.BrowserNativeMessageHost.exe` never starts when Edge tries to launch it.
- PAD fails at "Launch Edge" with: `Could not connect to the web extension's native message host within the remaining timeout period (58 seconds).`
- Installing the Microsoft WebDriver is also blocked with a security warning.
- PAD version: 11.2609.183.0. It worked until a few months ago.

## What I'm asking
1. Check SentinelOne alerts/logs for `msedge.exe` starting `PAD.BrowserNativeMessageHost.exe` (and the WebDriver install).
2. If these are being blocked, add a scoped exception or approval for the Microsoft-signed PAD native host (and WebDriver if you prefer that route) on my machine.
3. If the policy is intentional, tell me, and let me know what approved alternative exists. For example, a scheduled export of the Birthday/Anniversary reports, or an API for sending cards.

## Business purpose
Pull the monthly Birthday and Anniversary reports for a domicile, then send each pilot a greeting card through the SkyWest Online card page.
