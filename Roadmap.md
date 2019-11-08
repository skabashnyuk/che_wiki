# Eclipse Che Roadmap
Eclipse Che follows a release cycles with a sprint planned every 3 weeks, with a new release after every sprint. For serious issues, we occasionally make a bug fix release during a sprint. While working on a current sprint, we plan the following sprint. We thematically break the major functionality into epics that have sub-issues that can span many sprints, and sometimes across many releases. We do our best to incorporate all of a feature into a single release, but it often requires that we break functionality across multiple release milestones.

The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

Full details of all of the work in a specific release is included in the [Changelog](https://github.com/eclipse/che/blob/master/CHANGELOG.md) file, which is updated after every release.

# Current sprint planning

At any time you can see what is being worked on:
- See [high level planning per sprint per team](https://github.com/eclipse/che/labels/kind%2Fplanning)
- See [issues in the current sprint](https://github.com/eclipse/che/labels/sprint%2Fcurrent-sprint).
- See [issues planned for the following sprint](https://github.com/eclipse/che/labels/sprint%2Fnext-sprint).
- See [PRs in code-review](https://github.com/eclipse/che/pulls?q=is%3Apr+is%3Aopen+label%3Astatus%2Fcode-review).

# Our plans for the next 6-12 months

## Ease of use
### P1
* Error reporting, Diagnostic Mechanism and Troubleshooting \
We have found that currently, diagnosing problems in Che is quite difficult. Our approach is to improve logging, make it easier to collect information for reporting problems and to provide guides for troubleshooting when something goes wrong
* Usage metrics
We want to collect metrics on how users are using Che in order to identify what workflows are important, what works well and what needs improvement
* Workspaces CRD and beyond
Establish a standard custom resource definition (based on the devfile format) that describes a cloud development workspace. Provide a controller that creates a Che workspace from such a definition.
* Smoother installation (good defaults)
We get many questions related to installing and configuring Che. We need to work on our installer and our documentation to make this experience smoother
* Fix dashboard workspace editing
Make it easier to create and edit workspaces. Includes great editing support for devfiles.
* Live tutorial documents
Provide tutorial documents where the user can execute actions in a Che workspace just by clicking a link in the tutorial document. We used to have this in Che 6, but need the same for Theia-based workspaces.
### P2
* On the go workspace configuration
The idea is to configure the workspace from inside the workspace, for example by adding additional plugins. Depending on the change, this might require a restart of the workspace.
* Workspace state in devfile
We would like to store more of the dynamic configuration of the workspace (for example user settings) inside the devfile in order to be able to share as much of the work environment as possible.

## Developer experience
### P1
* Dogfooding (develop Che using Che)
If we’re not using Che to develop Che, how can we convince anyone else to do so? There are a couple of roadblocks currently, for example not being able to build new images in Che. But we also need to define and simplify our processes for doing self-hosting.
* Improve quality practices for Che and Theia
This includes requiring docs PR’s for every code change and improved tests with the Theia editor (“definition of done”)
### P2
*   10 min turnaround for all changes
The process from making a code change and being able to test this change in a realistic environment must be less than 10 mins. This will encourage doing smaller, more robust changes and attract contributors beyond the core team.
* Enable new contributors 
Right now, it’s very hard to just come to the Che repo and start contributing. A developer should be able to start developing any part of Che without consulting anyone on the current development team.

## Performance
### P1
* 5s workspace startup 
Startup time should be competitive with a local IDE. Dogfooding should give us an idea what value of “5” is the correct one.
* rsync to get faster workspace boot and multi-pod workspaces
The performance of persistent volume implementations are not a good fit for a development environment. The idea is to use container-local volumes and to synchronize those volumes with persistent storage elsewhere.
* High latency user experience in the browser
The behaviour of the IDE is confusing when there is high network latency. We need to make degrade gracefully and make the user aware of the problem.
* Scalability, Performance and Working with high latency
We need to provide guidelines for what the requirements are with respect to memory, number of cores and network bandwidth and latency.
### P2
* Che plugins caching mechanism
Che plugin contents are usually downloaded from third party sites, for example a github release page. Providing a “local” cache (and possibly prepopulating it) would improve workspace startup time and improve reliability. 

## Hybrid Cloud
### P1
* Building container images in the inner loop
In order to be a true hybrid cloud IDE, we need to be able to build images inside Che. This is also necessary to do self hosting.

# Past Releases

| Sprint start | Sprint end | Sprint number | Release |
|---------------|---------------|-------|-------------------|
| 9-Aug-2017	| 29-Aug-2017	| 136	| [5.17.0](https://github.com/eclipse/che/releases/tag/5.17.0) |
| 30-Aug-2017	| 19-Sep-2017	| 137	| [5.18.0](https://github.com/eclipse/che/releases/tag/5.18.0) ([release notes](https://che.eclipse.org/release-note-5-18-993516476315))|
| 20-Sep-2017	| 10-Oct-2017	| 138	| [5.19.0](https://github.com/eclipse/che/releases/tag/5.19.0) |
| 11-Oct-2017	| 31-Oct-2017	| 139	| [5.20.0](https://github.com/eclipse/che/releases/tag/5.20.0), [6.0.0-M1](https://github.com/eclipse/che/releases/tag/6.0.0-M1) |
| 1-Nov-2017	| 21-Nov-2017	| 140	| [5.21.0](https://github.com/eclipse/che/releases/tag/5.21.0), [6.0.0-M2](https://github.com/eclipse/che/releases/tag/6.0.0-M2)  |
| 22-Nov-2017	| 12-Dec-2017	| 141	| [5.22.0](https://github.com/eclipse/che/releases/tag/5.22.0), [6.0.0-M3](https://github.com/eclipse/che/releases/tag/6.0.0-M3)  |
| 13-Dec-2017	| 2-Jan-2018	| 142	| [6.0.0-M4](https://github.com/eclipse/che/releases/tag/6.0.0-M4)  |
| 3-Jan-2018	| 23-Jan-2018	| 143	| [6.0.0](https://github.com/eclipse/che/releases/tag/6.0.0) ([release notes](https://che.eclipse.org/release-notes-eclipse-che-6-0-43feff5797e5)) |
| 24-Jan-2018	| 13-Feb-2018	| 144	| [6.1.0](https://github.com/eclipse/che/releases/tag/6.1.0) |
| 14-Feb-2018	| 6-Mar-2018	| 145	| [6.2.0](https://github.com/eclipse/che/releases/tag/6.2.0) |
| 7-Mar-2018	| 27-Mar-2018	| 146	| [6.3.0](https://github.com/eclipse/che/releases/tag/6.3.0) |
| 28-Mar-2018	| 17-Apr-2018	| 147	| [6.4.0](https://github.com/eclipse/che/releases/tag/6.4.0) |
| 18-Apr-2018	| 8-May-2018	| 148	| [6.5.0](https://github.com/eclipse/che/releases/tag/6.5.0) |
| 9-May-2018	| 29-May-2018	| 149   | [6.6.0](https://github.com/eclipse/che/releases/tag/6.6.0) |
| 30-May-2018	| 19-Jun-2018	| 150 | [6.7.0](https://github.com/eclipse/che/releases/tag/6.7.0) |  |
| 20-Jun-2018	| 10-Jul-2018	| 151	| [6.8.0](https://github.com/eclipse/che/releases/tag/6.8.0) |
| 11-Jul-2018	| 31-Jul-2018	| **152** |  [Sprint planning](https://github.com/eclipse/che/issues?utf8=%E2%9C%93&q=label%3Akind%2Fplanning+Sprint%3A+152)  |
| 1-Aug-2018	| 20-Aug-2018	| 153 |  |
