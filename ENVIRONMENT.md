# Environment details (fill in what you know)

## Failure
- Exact error message text (copy from the flow run / Errors pane):Correlation Id: 929ddf65-d8b4-4575-871b-4cd08e8482e8

Could not connect to the web extension's native message host within the remaining timeout period (58 seconds).: Microsoft.Flow.RPA.Desktop.Modules.SDK.Extended.Exceptions.InternalActionException: Failed to assume control of Microsoft Edge (communication with Power Automate web extension failed) ---> Microsoft.Flow.RPA.Desktop.UIAutomation.WebAutomation.Core.WebExtensionsBrowser.WebExtensionHostNotAvailableException: Could not connect to the web extension's native message host within the remaining timeout period (58 seconds). ---> System.TimeoutException: The operation has timed out.
   at Microsoft.Flow.RPA.Desktop.UIAutomation.Shared.Rpc.NamedPipesRpcPeer.CreatePipeStream(String pipeName, Boolean isServer, TimeSpan connectTimeout, Int32 bufferSize, CancellationToken cancellationToken)
   at Microsoft.Flow.RPA.Desktop.UIAutomation.Shared.Rpc.NamedPipesRpcPeer..ctor(String pipeName, RpcInterfaceRegistar interfaceRegistar, Boolean isServer, TimeSpan connectTimeout, TimeSpan callTimeout, Int32 bufferSize, ILogger`1 logger, IStreamValidator streamValidator, CancellationToken cancellationToken)
   at Microsoft.Flow.RPA.Desktop.UIAutomation.Shared.Rpc.NamedPipesRpcPeer.ConnectAsClient(String pipeName, RpcInterfaceRegistar interfaceRegistar, ILogger`1 logger, Nullable`1 connectTimeout, Nullable`1 callTimeout, IStreamValidator streamValidator, CancellationToken cancellationToken)
   at Microsoft.Flow.RPA.Desktop.UIAutomation.WebAutomation.Core.WebExtensionsBrowser.Communication.RpcWebExtensionsProxy.Connect()
   --- End of inner exception stack trace ---
   at Microsoft.Flow.RPA.Desktop.UIAutomation.Core.Abstractions.ServiceRouter`1.Invoke(MethodInfo targetMethod, Object[] args)
   at generatedProxy_6.LaunchNewEdge(AutomationRoute, String, String, String, String, LaunchNewEdgeMode, LaunchWindowState, AttachMode, MatchMode, Boolean, TimeSpan, WebPageCourseOfActionIfDialogAppears, Boolean, Boolean, TimeSpan, PiPUserDataFolderMode, String, Boolean, WebAutomationCommunicationMethod, Dictionary`2)
   at System.Reflection.MethodBaseInvoker.InterpretedInvoke_Method(Object obj, IntPtr* args)
   at System.Reflection.MethodBaseInvoker.InvokeWithManyArgs(Object obj, BindingFlags invokeAttr, Binder binder, Object[] parameters, CultureInfo culture)
--- End of remote exception stack trace ---
   at System.Runtime.ExceptionServices.ExceptionDispatchInfo.Throw()
   at Microsoft.Flow.RPA.Desktop.UIAutomation.Shared.Rpc.RpcDispatchProxy`1.GetRemoteResultOrThrow(ISerializer serializer, RPCMessage response, Type expectedResultType, Object additionalContext)
   at Microsoft.Flow.RPA.Desktop.UIAutomation.Shared.Rpc.RpcDispatchProxy`1.Invoke(MethodInfo targetMethod, Object[] args)
--- End of stack trace from previous location where exception was thrown ---
   at System.Runtime.ExceptionServices.ExceptionDispatchInfo.Throw()
   at System.Reflection.DispatchProxyGenerator.Invoke(Object[] args)
   at generatedProxy_2.LaunchNewEdge(AutomationRoute , String , String , String , String , LaunchNewEdgeMode , LaunchWindowState , AttachMode , MatchMode , Boolean , TimeSpan , WebPageCourseOfActionIfDialogAppears , Boolean , Boolean , TimeSpan , PiPUserDataFolderMode , String , Boolean , WebAutomationCommunicationMethod , Dictionary`2 )
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Common.WebAutomationRuntimeServiceProxy.<>c__DisplayClass26_0.<LaunchNewEdge>b__0(IWebAutomationRuntime s)
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Common.WebAutomationRuntimeServiceProxy.ExecuteSafe[T](Func`2 action, TimeSpan timeout)
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Common.WebAutomationRuntimeServiceProxy.LaunchNewEdge(AutomationRoute route, String initialUrl, String edgeTabTitle, String edgeTabUrl, String dialogButtonToPress, LaunchNewEdgeMode operation, LaunchWindowState windowState, AttachMode attachMode, MatchMode matchMode, Boolean waitForWebPageToLoad, TimeSpan waitForPageToLoadTimeout, WebPageCourseOfActionIfDialogAppears courseOfActionIfDialogAppears, Boolean clearCache, Boolean clearCookies, TimeSpan timeout, PiPUserDataFolderMode pipUserDataFolderMode, String pipUserDataFolderPath, Boolean runInPip, WebAutomationCommunicationMethod communicationMode, Dictionary`2 webDriverSessions)
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Actions.LaunchEdgeBase.<>c__DisplayClass83_0.<Execute>b__0(IWebAutomationRuntime s)
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Actions.WebAutomationActionBase.PerformWebAutomationWithLogging[T](Func`2 action, WebAutomationRuntimeLogData requestData, Func`3 resultData)
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Actions.LaunchEdgeBase.Execute(ActionContext context)
   --- End of inner exception stack trace ---
   at Microsoft.Flow.RPA.Desktop.Modules.WebAutomation.Actions.LaunchEdgeBase.Execute(ActionContext context)
   at Microsoft.Flow.RPA.Desktop.Robin.Engine.Execution.ActionRunner.Run(IActionStatement statement, Dictionary`2 inputArguments, Dictionary`2 outputArguments, Guid actionExecutionId)
- Which action fails (e.g. "Launch new Chrome", "Click link on web page"):
- Does it fail every run, or only unattended / scheduled runs?
- Did it ever work? When did it stop? Anything change then (Windows update,
  browser update, PAD update, new PC, password change)? It did work, not really sure when it wuit but it has been a few months

## Browser
- Browser used (Edge / Chrome / Firefox) and version:Edge
- Extension installed: (Power Automate extension for Edge/Chrome) - enabled? yes
- Extension allowed in InPrivate/Incognito? dont know
- Browser launched by flow with a profile / user data folder? dont know
- Does the browser window open to the right page but the flow says it can't find it? yes

## Power Automate Desktop
- PAD version:Version: 11.2609.183.0
Component: Console
Client ID: F3BEA98F02DF476CB1BF57B7A79C5DCA
Session ID: 64584351-7e9f-4595-a102-3ca1f7dbe31b
Correlation ID: 0a1d1979-1c48-4296-a8c0-b4b43e9e36a3

- Licence (free / Premium / per-user / attended / unattended):
- How is the flow triggered (manual, scheduled Task Scheduler, cloud flow)? manual
- Is the PC signed in and unlocked when it runs? Remote Desktop used? yes
- Is PAD running as admin, or the browser running as admin? no

## Website
- Does the site require login (SSO/MFA)? Is it behind iframes/popups? yes, i have to sign in first, but it still does not work
- Is there any API, export, or database behind the pilot data (Excel, SQL, etc.)? yes
- How are cards sent (site form, email, print)? from site, must have browser control
