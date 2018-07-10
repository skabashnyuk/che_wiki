We track support tickets, issues and feature requests using the [GitHub issue tracker](http://github.com/eclipse/che).

Before Submitting an Issue
--------------------------
Check that [the issues page](https://github.com/eclipse/che/issues)
does not already include that problem or suggestion. Do this before submitting an issue.
If you find a match, you can use the "subscribe" button to get notified on
updates. Do *not* leave random "+1" or "I have this too" comments. These comments only
clutter the discussion, and do not help resolving it. Yet, if you
have ways to reproduce the issue or have extra information that may help, 
please leave a comment.

Writing Great Issues and Suggestions
------------------------------------
Please file a single issue per problem and feature request. Do not file combination issues.

The more information you provide, the more likely reproducing the issue and finding a fix will be. 

Thus:
* Provide reproducible steps, the results of the steps, and what you would have expected.
* A detailed description of the behavior that you expect.
* Animated GIFs are a tremendous help.
* Version information of Eclipse Che and Docker.
* Error outputs that may exist in your browser console.

Do not feel bad if we cannot reproduce the issue and ask for more information.

Logs and Debug Information
--------------------------
Yes, we need logs. Attaching logs and screenshots of browser dev console will help identify what has caused a bug or misbehavior, and fix it ASAP. We encourage you spend some time to extract logs and attach them to the issue, along with steps to reproduce. You will find information on how to get logs from different Che components below.

### Workspace Master Logs

We will typically need those logs if:
* Che master itself does not start (you cannot get to User Dashboard or login screen)
* workspaces fail to start
* there are problems with installers and as a result a workspace either fails to start or extra functionality provided by an installer is unavailable

#### How to get master logs on Docker

Run the following command on the host where Che runs:

```
docker logs -f che
```
Logs are also stored in `${LOCAL_STORAGE_DIR}/instance/logs/archive`, so you can get files from this location as well.

#### How to get master logs on OpenShift:

There are multiple ways to get logs:

* using oc client:

```
# eclipse-che is the default namespace, but it can be a different namespace
oc logs dc/che --namespace=eclipse-che
```

* in OpenShift Web Console, pods > che pod:

![OpenShift Web Console: Che Logs](https://user-images.githubusercontent.com/5337267/42504636-0bfd657e-8445-11e8-9e84-8a38da99abfe.png)

### Workspace Agent Logs

Workspace agent is a Tomcat server that starts in a container. WS-agent logs are critical in the following cases:

* there is a bug in the IDE, in a running workspace, for example with project import, project explorer etc
* any issues related to language support

#### How to get workspace agent logs?

Workspace agent isn't the main process in a container so, you cannot get logs using infrastructure commands like `docker logs` or `oc/kubectl logs`. You can still find the logs though. 

There's a button on the consoles panel that will download machine logs.

![Workspace Agent Logs](https://user-images.githubusercontent.com/5337267/42514683-ac1ecae4-8462-11e8-9b64-d4229bac1dae.png)

You can also grab logs as files:
* on Docker at `{HOME}/che/ws-agent/logs`
* on OpenShift/K8S at `/workspace_logs/ws-agent`

### Client requests to workspace master and agents

If an error happens in User Dashboard (communicates with master) or the IDE (communicate with master and ws-agent) it is extremely helpful to have a log of requests that clients initiate.

Preserve log, Network, XHR:

![Http requests](https://user-images.githubusercontent.com/5337267/42517216-e06561a0-8467-11e8-8079-5fb8d2724095.gif)

Capturing websockets communication:

![Websockets](https://user-images.githubusercontent.com/5337267/42517225-e79293da-8467-11e8-8a09-a997dd3e036d.gif)

Here's an example of tracking project import:

![Websockets](https://user-images.githubusercontent.com/5337267/42517870-64a06b44-8469-11e8-96d2-b46033c2703d.gif)

You may also save all requests as HAR:

![Save all as HAR](https://user-images.githubusercontent.com/5337267/42518456-8d6667a8-846a-11e8-924f-f1a569477046.png)

The resulting file might be quite big, so it makes sense to use an external storage to upload it. There are also Chrome extensions like [HTTP trace](https://chrome.google.com/webstore/detail/http-trace/idladlllljmbcnfninpljlkaoklggknp) or [Web Sniffer](https://chrome.google.com/webstore/detail/web-sniffer/ndfgffclcpdbgghfgkmooklaendohaef) that will record https requests for you.

Finally, this is [our issue tracking](https://github.com/eclipse/che/wiki/Issue-Tracking) workflow. This describes what happens once you submit an issue.
