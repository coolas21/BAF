

Luke Grout

Work IQ

Auto


You said:
it immediatly returned to the prompt, and did not show up in task manager
Copilot said:
That result is not proof the EXE is broken. Native messaging hosts are designed to communicate with Edge through stdin/stdout, so launching the EXE manually without Edge providing that communication can reasonably result in the process exiting. Microsoft documents that Edge normally starts the host and communicates with it using stdio. Native messaging - Microsoft Edge Developer documentation
microsoft

There is one check I think we've missed, and it's a good one.

Check the actual Edge extension ID
Your PAD.ChromiumManifest.json permits these Edge IDs:




Plain Text
kagpabjoboikccfdghpdlaaopmgpgfdc   ← Edge production
imdakehokbgfjhopgeipbokicjpnbipl   ← Edge development
Microsoft says the native host's allowed_origins must contain the ID of the extension trying to communicate with it.
microsoft

Open:



Plain Text
edge://extensions/
Make sure Developer mode is ON.
Find Microsoft Power Automate.
Look for ID underneath the extension.
Compare it to:



Plain Text
kagpabjoboikccfdghpdlaaopmgpgfdc
If the ID is different, paste the ID here. That would be a very meaningful finding because the manifest you pasted only allows the four IDs listed inside it.





Favicon type
Sources
You said:
same
Copilot said:
Good. That eliminates an extension-ID mismatch too.

At this point, I don't think anything is incorrectly installed. We have verified the entire Edge native-messaging chain, and Edge is specifically failing when it attempts to launch the host.

The manual-launch behavior does not prove the EXE is failing, because native messaging hosts use stdin/stdout to communicate with Edge and may exit when launched without that connection. Native messaging - Microsoft Edge Developer documentation
microsoft

My conclusion
The strongest evidence now is:

Power Automate extension: installed/enabled
Extension ID: matches allowed_origins
com.microsoft.pad.messagehost: registered
PAD.ChromiumManifest.json: exists
PAD.BrowserNativeMessageHost.exe: exists
cmd.exe: works
ComSpec: correct
Edge native-messaging policies we checked: not configured
Duplicate MSI installation: not found
Edge service worker: Failed to start native messaging host
PAD.BrowserNativeMessageHost.exe: never starts
So something is preventing Edge from successfully starting that native host.

The company-managed SentinelOne component is a reasonable thing for IT/security to investigate, but we have not proven it is the cause, and I would not disable it yourself.

What I'd send IT
Microsoft Power Automate Desktop web automation stopped communicating with Edge.

The Microsoft Power Automate Edge extension is installed and enabled. Its extension ID matches the allowed Edge production ID in the PAD native messaging manifest.

The extension's service-worker console continuously reports:

Unchecked runtime.lastError: Failed to start native messaging host.

Native host: com.microsoft.pad.messagehost

Executable: PAD.BrowserNativeMessageHost.exe

The native-messaging registry registration, PAD.ChromiumManifest.json, and PAD.BrowserNativeMessageHost.exe have all been verified as present, but PAD.BrowserNativeMessageHost.exe never starts when Edge attempts the connection.

Please check endpoint/security controls, including SentinelOne, for anything blocking Microsoft Edge from launching the Power Automate native messaging host.

That's much more actionable for IT than simply reporting "PAD can't control Edge."





Favicon type
Sources
You said:
could we just make this run in chrome?
Copilot said:
Yes. Chrome is absolutely worth trying, and PAD officially supports Google Chrome for browser automation. It can use either the Power Automate browser extension or WebDriver. Browser automation actions reference
microsoft

Given the problem we've isolated in Edge, Chrome is also a useful test because it tells us whether this is Edge-specific or whether the native messaging host is being blocked system-wide.

Step 1: Install the PAD Chrome extension
In Power Automate Desktop:

Open your flow.
Select Tools → Browser extensions.
Choose Google Chrome.
Let PAD take you through installing Microsoft Power Automate for Chrome.
In Chrome, open:



Plain Text
chrome://extensions/
Verify Microsoft Power Automate is present and enabled.
Microsoft specifically supports installing the Chrome extension from PAD's Tools → Browser extensions menu. Install Power Automate browser extensions
microsoft

Step 2: Don't modify your big flow yet
Let's prove Chrome communication works first.

Once the extension is installed:

Completely close Chrome.
Reopen Chrome.
Open Task Manager → Details.
Look for:



Plain Text
PAD.BrowserNativeMessageHost.exe
Microsoft says one instance of that process runs for each browser type when the extension/native-host connection is functioning. Troubleshoot Browser Extension Errors in Desktop Flows
microsoft

What this test tells us
If PAD.BrowserNativeMessageHost.exe appears with Chrome: excellent. That strongly points us toward the Edge side of the setup, and we can start converting your flow to use Launch new Chrome. PAD provides separate launch actions for Edge and Chrome.
microsoft
+1

If it still does not appear with Chrome: don't bother converting the flow yet. Chrome also depends on the Power Automate browser integration, so we'd likely still have the underlying native-host communication issue.
microsoft

I'd do only that first. Install the Chrome extension, open Chrome, and check Task Manager for PAD.BrowserNativeMessageHost.exe.






Favicon type
Sources

Walk me through installing the Chrome extension

Help me test whether PAD connects to Chrome



Message Copilot




AI-generated content may be incorrect
