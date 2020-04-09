## Purpose and Audience ##
These conference calls are meant for the Che adopters and contributors to chat about some project development details (can be planning, concerns, or more technical details). The goal is to better synchronize and organize efforts of the various contributors in order to make Che better.

It's open to anyone interested. You don't need to have a long history with Che to attend the talk, listen and ask relevant questions.

## When and Where ##
These meetings take place every [Monday, 7:00 AM PST](https://www.wolframalpha.com/input/?i=Monday+7%3A00+AM+PST). You can be part of the meeting (mic + chat + video cam) with [BlueJeans](https://bluejeans.com/2488406763). Chat link updated 18-Mar-19. Calendar [link](https://calendar.google.com/event?action=TEMPLATE&tmeid=NzBzajBjOWtjNG82Y2I5azYwcjMwYjlrNnNxMzhiYjFjY3A2OGI5bzc1Z21jcGhwY2NyamlkcjNjOF8yMDE5MDcwOFQxNTAwMDBaIHN1dGFuQHJlZGhhdC5jb20&tmsrc=sutan%40redhat.com).

# Next meeting 13-April-2020
The next Che dev meeting will take place on Monday April 13th 2020. You are welcome to add the topics you would like to discuss or propose a demo during the call: [Google Doc](https://docs.google.com/document/d/1duuavOXVAJNbzU8nIltraDKx5YH2Z34Qwx7AeLnhhzU/edit?usp=sharing)

# 6-April-2020
## Agenda:
#Agenda
1. Demo: Smartface Mobile Development IDE on Che (Smartface Team)
2. License check for kubernetes-image-puller (planned to be contributed to the Eclipse Foundation but not clear where exactly - new-project, sub-project, part of ecdtools). How can we get the initial review without CQ:
https://github.com/eclipse/che/issues/16321#issuecomment-608559780  (Ilya)
3. The state of 7.11.0 release?  (Ilya)
4. Cancel the next call ? as it is public holliday in several countries ? FR, BE, CZ, DE, IE, UK (Sun)

Recording: 
https://youtu.be/h0qtw3816P4

Minutes: [Google Doc](https://docs.google.com/document/d/e/2PACX-1vTVHtnOe3zJUrhBAGQkPBKc92Nc79RdZYWDJLUQmtNichxGw_-mdi3-ubVtEn698DLLI2Kyk2ulb6P4/pub)

# 30-March-2020
## Agenda:
1. Che release process: skip RC, go directly to R. Fail faster and get more releases out in 1/5th the time (1 day, not 4-5) (Nick)
2. Youtube channel for video recordings, demos, training materials. (Sergii Kabashniuk)
3. Dashboard Next direction. Existing POC of the new UD (Oleksii Orel)
4. Looking for volunteers (NA and APAC time zones in particular) to participate to RH Virtual Summit - Community central: Goal: answer to questions related to Che in Chat rooms (Sun).
5. Team updates

Recording: 
https://youtu.be/cpMTKGO02Nc

Minutes: [Google Doc](https://docs.google.com/document/d/e/2PACX-1vRYHOHkEKGnOIR-gYXYSIIx9s4IdOIHkblNIuXmv0uh8VIODANchNAAXJRb1G4YV2ia-xvHsmFylRoY/pub)


# 23-March-2020
## Agenda:
1. Che commands as Theia tasks, what are the next steps? Following [15540#issuecomment-599462786](https://github.com/eclipse/che/issues/15540#issuecomment-599462786) and [12709#issuecomment-601769959](https://github.com/eclipse/che/issues/12709#issuecomment-601769959) (Sun)
2. Che release candidate testing flow (Mykhailo)
   - what do we do about unreleased operator and chectl (7.9.2) when we need them to test che 7.9.2.RC bits?
   - Currently use nightly/next but if there are breaking changes in master, that won’t work (as we discovered during 7.9.2 / 7.11 last week)
   - Could we do RC builds for operator and chectl too?
   - Or just release them completely (full R, no RC pre-release) like we do for che-theia and registries?
   - It has been decided to start providing chectl:rc and che-operator:rc (dedicated  issue).
3. Updates on progress made on the implementation of CoEditing Skeleton in Eclipse Che 7 (Live collaboration) - Quick Demo (Rijul/Sun)
4. How to use Image digests instead of tags in time of Eclipse Che deployment by chectl? It seems we support it now but I can’t find the doc. (Dmytro)
5. Docs PR (Sergii Kabashniuk)
6. Area labels and triage instructions updated (Mario) 

Recording: 
https://youtu.be/2xWpUChqHr8

Minutes: [Google Doc](https://docs.google.com/document/d/e/2PACX-1vSICRK0q1Qq9xP_BdYGFr-kRI9PlZJJHphAUzhkWPe0Qg4bsevoCQkeEWx5U1AWAmjKQEX3aupKEFwq/pub)


# 16-March-2020
## Agenda:
* Bug in exposing route (Sun)
* Consider launching Happy Path tests on others repos except Che, like workspace-loader, dashboard (is not moved yet but eventually it will be soon) (Serhii Leshchenko)
* When adding new che-theia api should the new api always be added to @eclipse-che/plugin API or should it be split into its own module depending on the contents. Relevant PR: https://github.com/eclipse/che-theia/pull/597 (Josh Pinkney)
* Ensuring non-codeowner contributions are included in releases (Angel Misevski)
* Team updates

Recording: 
https://youtu.be/DsxEwg-2-e0

Minutes: [Google Doc](https://docs.google.com/document/d/e/2PACX-1vSxS9FHjEw4AOLKJtwZruJC9YBM4NG1kk05z7LjJphEwl25ne5MmI9gxFXC5A3XpCn-sppyI4btgVcd/pub)



# 9-March-2020
## Agenda:
* 2 meetings in the calendar - can we remove one of them? (Ilya)
* Team updates

Recording: https://youtu.be/HWNQShe69_0


Minutes: [Google Doc](https://docs.google.com/document/d/e/2PACX-1vQoojvqfcGyJoKvSxfgD0LmpltR_PNnHvnh4ttrftU9XWwJ1W1yo2RzC0r6cekHHNqA-fNKn2C15K72/pub)

# 2-March-2020
## Agenda:

* Selenium tests. Maintenance costs. Sergii Kabashniuk, Radim Hopp
* 7.9.0 issues caught on Hosted Che staging: Ilya Buziuk
  * Workspace stop time increased significantly after the 7.9.0 update #16200 
  * LS for default PHP stacks not working #16196
* Release 7.9.1 - Sergii Kabashniuk

Minutes:  [Google Doc](https://docs.google.com/document/d/e/2PACX-1vTQEYEgOhdhU-Jx0crY3_LmG3UM8EfxiFLCZCbbTUSWjoT0NPQy5xm1AqlW1TXy57OoNJCLNsZ87BZC/pub)

# 24-February-2020
## Agenda:
* Move this to HackMD.io or eventually Che (Sun)
* Taking notes of this call next week (Florent on PTO next week) -> mario ? (Florent - 1mn)
* Google Summer of Code discussion (Sun)
* Status of 7.9.0 release (Ilya) 
* Users branches survey (Mario)

Minutes:  [Google Doc](https://docs.google.com/document/d/e/2PACX-1vQg10YnJx8byOJhI-uhuBGZtaDh-mOpGSNR7XK9a44Ta1WClBMChpwweip_j5SPA4di87IBELHByvKG/pub)

# 17-February-2020
## Recording
https://youtu.be/ye-3Tvp7oQs

## Notes and Minutes
### Your work is new, &/or noteworthy! (Nick) AI: all committees, contributors, users, customers, support, docs
- Please [tell the world](https://www.google.com/url?q=https://www.eclipse.org/lists/che-dev/msg03578.html&sa=D&ust=1582041846808000) about it!

- (aka self-assessment of [interesting GH issues](https://www.google.com/url?q=https://github.com/eclipse/che/issues?utf8%3D%25E2%259C%2593%26q%3D%2Bmilestone%253A7.9.0%2Blabel%253Anew%2526noteworthy%2B&sa=D&ust=1582041846808000), and setting correct milestone fix version & doneness)


### Che release process update (Nick) AI: release owners & prod team
- Now we start on [Tuesday 09:00 EST / 15:00 CEST / 16:00 EEST](https://www.google.com/url?q=https://www.eclipse.org/lists/che-dev/msg03577.html&sa=D&ust=1582041846809000)(to avoid sliding past the weekend)
- Want to do as before in the past with an expected release date (no shift)




### Topic branches in private forks - (Nick) AI: committees and contributors
(vs. cluttering the origin repos & forgetting to take out your trash): best practices/least effort. [Discussion](https://www.google.com/url?q=https://www.eclipse.org/lists/che-dev/msg03575.html&sa=D&ust=1582041846810000)

*   Best way for “single contributions” should be in private forks/branches
*   Only if really need (like contributing with several people)
*   Sergii: why we should enforce that: no technical reason
*   → use forks as much as possible but try to avoid branches in the repository.
*   Mykola: what is the problem if users clean up branches after the merge ?
*   Mario: Would avoid to see branches
*   Matter of taste, so probably we would need a vote ?
*   Sun: More and more contributors : hard to follow
*   AI: @Sun: survey to follow-up


### New committers recently approved Who's next ? (Nick) AI: contributors?

*   Tom George
*   Eric Williams
*   Yana Hontyk

Who will be next? :D -> Flavius

*   Next one should be Flavius
*   [https://projects.eclipse.org/projects/ecd.che/elections/election-flavius-lacatusu-committer-eclipse-che](https://www.google.com/url?q=https://projects.eclipse.org/projects/ecd.che/elections/election-flavius-lacatusu-committer-eclipse-che&sa=D&ust=1582041846830000)

### PR check jobs migrated to ci.centos.org (Radim)

*   Who should be in the admin list?
*   Who should be the committers
*   Radim will provide a link on how to do that for internal Red Hat people.
*   For now, could start with [https://github.com/orgs/eclipse/teams/ecd-che-committers/members](https://www.google.com/url?q=https://github.com/orgs/eclipse/teams/ecd-che-committers/members&sa=D&ust=1582041846830000)
*   See if we can automatically sync it or if continue manually
*   AI: @Radim: how to trigger the test again, how to reach ppl if there is an issue in the check, etc.

### Using digests rather then tags for image references and commit hash rather then master branch for samples (Mario)

*   [https://github.com/eclipse/che/issues/16047](https://www.google.com/url?q=https://github.com/eclipse/che/issues/16047&sa=D&ust=1582041846813000)
*   [https://github.com/eclipse/che/issues/15898](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15898&sa=D&ust=1582041846813000)


*   Build of Che more repeatable/reproducible from external images
*   Avoid tags and use digest instead
*   Same approach should be followed for examples like using a specific tag instead of a branch
*   Use of forked repository ? to avoid deletion on upstream repositories
*   →


### Promote builtin-related plugin issues to P1 (gattytto)

[https://github.com/eclipse/che/issues/16057](https://www.google.com/url?q=https://github.com/eclipse/che/issues/16057&sa=D&ust=1582041846815000)
Postponed discussion (mic issue from gattytto)


### Team update:

####   Eclipse Codewind (Public holiday on 2/17 in Toronto, no attendance)

*   Codewind 0.10.0 currently on track to GA on Feb. 18.
*   0.10.0 needs to stay on Che 7.5.1.  Currently blocked by [#15658](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15658&sa=D&ust=1582041846816000)before Codewind can move up to a newer version of Che.  More background info can be found on Codewind issue [#2203](https://www.google.com/url?q=https://github.com/eclipse/codewind/issues/2203&sa=D&ust=1582041846816000)

####   Hosted Che

*   Adapt Hosted Che 'k8s-image-puller' to the upstream needs [#15385](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15385&sa=D&ust=1582041846817000) \[WIP\]
*   Backup and Disaster Recovery documentation [#14240](https://www.google.com/url?q=https://github.com/eclipse/che/issues/14240&sa=D&ust=1582041846817000) \[WIP\]
*   Enabling telemetry on Hosted Che \[DONE\]

####   Platform

*   [https://github.com/eclipse/che/projects/15](https://www.google.com/url?q=https://github.com/eclipse/che/projects/15&sa=D&ust=1582041846818000)

####   Deploy

*   \[Troubleshooting capabilities\] Checking minimal version of k8s/openshift/helm
*   Some changes in \`chectl\` to be able to deprecate \`deploy\_che\` in future

####   Controller

*   [https://github.com/eclipse/che/projects/16](https://www.google.com/url?q=https://github.com/eclipse/che/projects/16&sa=D&ust=1582041846818000)

####   [Languages](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15796&sa=D&ust=1582041846819000)

*   [DONE] Update Debugger for Java and Language support for Java to latest[#15560](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15560&sa=D&ust=1582041846819000)
*   [WIP] Working on enabling Find All references extension
*   [WIP] VS Code API tests (PR Check) [che-theia/pull/597](https://www.google.com/url?q=https://github.com/eclipse/che-theia/pull/597&sa=D&ust=1582041846820000)
*   [WIP]  Some CRW plugin/image/devfile: started camel-k devfile
*   Doc air-gap procedures

*   [WIP]  npm + global doc by thomas, gradle

####   [Plugins](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15862&sa=D&ust=1582041846820000)

*   Help with vue plugin which is almost done
*   [Vale plugin](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15856&sa=D&ust=1582041846821000) now in the plugin registry
*   [OpenShift authentication provider merged](https://www.google.com/url?q=https://github.com/eclipse/che/pull/15963&sa=D&ust=1582041846821000)
*   More investigation into [task clicking delay issue](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15277&sa=D&ust=1582041846821000)
*   [Provided the ability](https://www.google.com/url?q=https://github.com/eclipse/che/issues/16002&sa=D&ust=1582041846822000) to add a public SSL key to the Java trusted key store
*   [Clarified docs](https://www.google.com/url?q=https://github.com/eclipse/che-docs/pull/1074&sa=D&ust=1582041846822000) for adding a VS Code extension to Che

####   Editors

*   Switched Che Theia to using VS Code’s built-in extensions for grammars/syntax highlighting instead of Eclipse Theia’s Textmate grammars [che-theia#618](https://www.google.com/url?q=https://github.com/eclipse/che-theia/pull/618&sa=D&ust=1582041846822000)
*   More secure Theia WebViews, on a separate origin [che-theia#591](https://www.google.com/url?q=https://github.com/eclipse/che-theia/pull/591&sa=D&ust=1582041846823000)
*   Working on upgrading Monaco editor in Eclipse Theia from 0.18.0 to 0.19.3 [theia#6900](https://www.google.com/url?q=https://github.com/eclipse-theia/theia/issues/6900&sa=D&ust=1582041846823000)

####   Devex:

*   [Devfile 2.0](https://www.google.com/url?q=https://github.com/che-incubator/devworkspace-api/issues/15&sa=D&ust=1582041846823000)and [PoC for devfile as a stack definition](https://www.google.com/url?q=https://github.com/che-incubator/devworkspace-api/issues/25&sa=D&ust=1582041846824000)
*   [Che Plugin dependencies resolution](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15966&sa=D&ust=1582041846824000)
*   Created all the subtask for the [async PV mount epic](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15384&sa=D&ust=1582041846824000)
*   Che RAM and CPU requirements documentation

####   Documentation

*   Yana Hontyk is now an Eclipse Committer
*   WIP Dogfooding che-docs [https://github.com/eclipse/che/issues/15866](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15866&sa=D&ust=1582041846825000)

####   QE

*   All QE jobs moved, now fine-tuning them.  
    

####   Che CI & Build Process Updates (Prod Team)

*   Trying a new Che release process for 7.9: see above

## Attendees:

1.  Florent Benoit (taking notes)
2.  Sun Tan
3.  Artem Zatsarynnyi
4.  Beau Morley
5.  David Festal
6.  Dmytro Nochenov
7.  Fabrice Flore-Thébault
8.  Esteban Basso aka gattyto
9.  Maksym Shaposhnyk
10.  Mario Loriedo
11.  Michal Vala
12.  Mykola Morhun
13.  Oleksii Orel
14.  Radim Hopp
15.  Rick Wagner
16.  Roman Nikitenko
17.  Sergii Kabashniuk
18.  Serhii Leshchenko
19.  Thomas Maeder
20.  Vitaliy Gulyy
21.  Vladyslav Zhukovskyi



# 10-February-2020
## Recording
https://youtu.be/KC8ZuhTzeLk

## Notes and Minutes
### Triage proposal (Sun)

- Sun presenting proposal:
  - [link](https://docs.google.com/presentation/d/e/2PACX-1vQr-DPCxHRcd3y7M7IVSSeEHkcWWBxHlHgZXww9WwPf2UDZ9eESAs7GlnAXcePw2woOnQ-NKUifWChp/pub?start=false&loop=false&delayms=3000)  to the slide-deck 
- Priority might differ based on developer’s feeling
- Issue affecting dogfooding might have a low severity while as user it might impact them with a higher priority.

### Dashboard / own repo (sergii)
Move the dashboard to its own github repository https://github.com/eclipse/che/issues/15266

- May solve issue about using java for one project and typescript for another one
- Split dashboard in its own repository (and probably workspace-loader)
- Needs to wait 7.10 release for that (after CRW 2.1)
- Maybe we could move che-server to another repository as well (and keep only che as being an assembly)

### Documentation about che server environment variables
	
https://www.eclipse.org/che/docs/pages/che-7/administration-guide/ref_configuring-system-variables.html Documentation about che server environment variables.

- Do you have feedback on this new page ?

### Definition of workspace sharing

*   Sharing : More than just sharing the editor. It can include the ssh stuff, tokens, etc.
*   Maybe investigate “pair programming” and drop the direct share.
*   Option could be to disable some security injection (no ssh, no token, etc) in that mode.
*   Proper messaging + document what is doing “sharing”

### Che docs team collaboration

*   Good job on collaboration between platform and doc team but:
*   Some PRs may be delayed since a long time without any feedback (stay there for too long)
*   → Try to keep PR as small as possible to do a better review
*   Will create a new che docs channel on mattermost to ping Doc people.
*   [https://mattermost.eclipse.org/eclipse/channels/che-docs](https://www.google.com/url?q=https://mattermost.eclipse.org/eclipse/channels/che-docs&sa=D&ust=1581422028283000)

### Teams updates:
#### Eclipse Codewind (Elson can’t attend this week so just provide update in here)

*   Reviewed devfile 2.0 proposal and added requirements: [https://github.com/che-incubator/devworkspace-api/issues/15](https://www.google.com/url?q=https://github.com/che-incubator/devworkspace-api/issues/15&sa=D&ust=1581422028268000)

#### Hosted Che

*   Adapt Hosted Che 'k8s-image-puller' to the upstream needs [#15385](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15385&sa=D&ust=1581422028269000)
*   Backup and Disaster Recovery documentation [#14240](https://www.google.com/url?q=https://github.com/eclipse/che/issues/14240&sa=D&ust=1581422028269000)
*   Enabling telemetry on Hosted Che

####   Platform

*   [https://github.com/eclipse/che/projects/15](https://www.google.com/url?q=https://github.com/eclipse/che/projects/15&sa=D&ust=1581422028270000)

####   Deploy

*   \[Troubleshooting capabilities\] Checking minimal version of k8s/openshift/helm
*   Some changes in \`chectl\` to be able to deprecate \`deploy\_che\` in future

####   Controller

*   [https://github.com/eclipse/che/projects/16](https://www.google.com/url?q=https://github.com/eclipse/che/projects/16&sa=D&ust=1581422028270000)

####   [Languages](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15796&sa=D&ust=1581422028271000)

- [DONE] Upgrade vscode-xml plugin to 0.10.1 [#15592](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15592&sa=D&ust=1581422028271000)
- [WIP] Working in fixing Find All references (for typescript plugin)
- [WIP] VS Code API tests (PR Check) [che-theia/pull/597](https://www.google.com/url?q=https://github.com/eclipse/che-theia/pull/597&sa=D&ust=1581422028272000)
- [WIP] Some CRW plugin/image/devfile: started camel-k devfile
- Doc air-gap procedures
  -   [DONE] Maven/Go/dotnet
  -   [WIP] npm + global doc by thomas

####   [Plugins](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15862&sa=D&ust=1581422028273000)

*   Concluded face-to-face meetings in Cherkasy, travel back for non-Cherkasy teammates
*   Opened PR for [Vale plugin addition](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15856&sa=D&ust=1581422028273000) to the registry
*   Opened [PR](https://www.google.com/url?q=https://github.com/eclipse/che/pull/15963&sa=D&ust=1581422028274000) for OpenShift connector authentication work
*   Discussions and PRs opened for [task clicking delay issue](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15277&sa=D&ust=1581422028274000)

####   Editors
####   Devex:

*   [Devfile 2.0](https://www.google.com/url?q=https://github.com/che-incubator/devworkspace-api/issues/15&sa=D&ust=1581422028274000) and [PoC for devfile as a stack definition](https://www.google.com/url?q=https://github.com/che-incubator/devworkspace-api/issues/25&sa=D&ust=1581422028275000)
*   [Che Plugin dependencies resolution](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15966&sa=D&ust=1581422028275000)
*   Created all the subtask for the [async PV mount epic](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15384&sa=D&ust=1581422028275000)

####   Documentation
*   Yana Hontyk is now an Eclipse Committer
*   WIP Dogfooding che-docs [https://github.com/eclipse/che/issues/15866](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15866&sa=D&ust=1581422028276000)

####   QE
*   All jobs moved, now fine-tuning them.  

####   Che CI & Build Process Updates (Prod Team)
*   No Che process updates this week
*   CRW 2.1 Quay images updated to Che 7.8, but [having problems deploying](https://www.google.com/url?q=https://issues.redhat.com/browse/CRW-625&sa=D&ust=1581422028277000) w/ crwctl. Cannot open a workspace: could be related to upstream che-operator issue [pull/166](https://www.google.com/url?q=https://github.com/eclipse/che-operator/pull/166&sa=D&ust=1581422028277000)

## Attendees:
1. Florent Benoit (taking notes)
1. Anatolii Bazko
1. Angel Misevski
1. Beau Morley
1. David Festal
1. Eric Williams
1. Fabrice Flore-Thébault
1. Gennady Azarenkov
1. Ihor Vinokur
1. Ilya Buziuk
1. Josh Pinkney
1. Lukas Krejci
1. Mario Loriedo
1. Martha Benitez
1. Mykhailo Kuznetsov
1. Nick Boldt
1. Oleksii Orel
1. Radim Hopp
1. Rick Wagner
1. Sergii Kabashniuk
1. Serhii Leshchenko
1. Sopot Cela
1. Stevan LeMeur
1. Sun Tan
1. Thomas George
1. Viktor Kuznietsov
1. Vitaliy Gulyy
1. Vladyslav Zhukovskyi


# 3-February-2020
## Recording
https://youtu.be/rQ1521HkRhc

## Notes and Minutes
### Making the call weekly?
- Before we had one internal meeting at Red Hat and Community call
- Want to merge two of them and will then get a weekly meeting

### Update of owners of the different components of Eclipse Che
- It also includes all repositories like che-plugin-registry, che-theia, etc.
- What is happening if a committer which is not a codeowner approve a PR then it’s merged and it breaks !
- Make enhancement on the template to really test the PR and not because they like the idea
- Want to have an agreement this week so we can decide what to do on all the projects in a common way.

### Teams updates
#### Eclipse Codewind
  -   Codewind 0.8.0 Jan 23 GAed
  -   Presented a talk on Codewind and Che on Devconf.cz conference in Czech Republic
  -   Next: Work on adding Codewind as part of the devfile registry, will create PR for adding Codewind to the Che plugin registry

#### Hosted Che

*   [Update Hosted Che to the latest 7.8.0 upstream version](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15871&sa=D&ust=1580829986269000)
*   [k8s-image-puller](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15385&sa=D&ust=1580829986270000) (faster workspace startup)
*   [Backup and Disaster Recovery documentation](https://www.google.com/url?q=https://github.com/eclipse/che/issues/14240&sa=D&ust=1580829986271000)

####   [Platform](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15869&sa=D&ust=1580829986271000)

*   [https://github.com/eclipse/che/projects/15](https://www.google.com/url?q=https://github.com/eclipse/che/projects/15&sa=D&ust=1580829986272000)

####   [Deploy](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15839&sa=D&ust=1580829986273000)
- Finalizing POC TLS by default (created a [PR #476](https://www.google.com/url?q=https://github.com/che-incubator/chectl/pull/476&sa=D&ust=1580829986273000))  
- Continue working on improving installation capabilities

####   [Controller](https://www.google.com/url?q=https://github.com/eclipse/che/projects/16&sa=D&ust=1580829986274000)

*   User Dashboard will be be configurable enough for reusing in Hosted Che soon [https://github.com/eclipse/che/issues/15462](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15462&sa=D&ust=1580829986275000)
*   Get started page improvements
*   Active developing Workspace CR Controller 

Actual status of sprint can be found at [https://github.com/eclipse/che/projects/16](https://www.google.com/url?q=https://github.com/eclipse/che/projects/16&sa=D&ust=1580829986276000)

####   [Languages](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15796&sa=D&ust=1580829986276000)

*   Call hierarchy API
*   Enable “References View”
*   VS Code API tests (PR Check)
*   Some CRW plugin/image work
*   Doc air-gap procedures

####   [Plugins](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15862&sa=D&ust=1580829986278000)
####   [Editors](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15628&sa=D&ust=1580829986278000)
####   Devex:

*   [Che-theia build fix](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15851&sa=D&ust=1580829986279000) and [CDN support fix](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15791&sa=D&ust=1580829986279000)
*   [Asynchronously attach PVs to Workspaces](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15384&sa=D&ust=1580829986280000)
*   [New Devfile and DevWorkspace API](https://www.google.com/url?q=https://github.com/che-incubator/devworkspace-api&sa=D&ust=1580829986280000)
*   [Cloud Shell Spec](https://www.google.com/url?q=https://github.com/openshift/enhancements/pull/182&sa=D&ust=1580829986281000)

####   Documentation
####   QE

*   che-bot token is finally on ci.centos.org
*   migrating remaining jobs from ci.codenvycorp.com

####   Che CI & [Build Process](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15506&sa=D&ust=1580829986283000) Updates (Prod Team)

*   3 of the 9 build stages scripted by Prod Team w/ RELEASE.md docs & used for Che 7.8.0 release; the rest of the stages are documented too, with 3 more scripted. Also have an [updated template](https://www.google.com/url?q=https://github.com/eclipse/che/pull/15875/files&sa=D&ust=1580829986283000) for creating [release issues](https://www.google.com/url?q=https://github.com/eclipse/che/issues/15860&sa=D&ust=1580829986284000) so it’s easier to track owner/status & verify artifacts are live. Remaining 3 stages will be scripted in future (requires Nexus integration).
*   [Sprint 179 plan](https://www.google.com/url?q=https://hackmd.io/fdo9FSNiQU2tL-jka33_HA?both&sa=D&ust=1580829986284000)

## Attendees
1. Florent Benoit (taking notes)
1. Anatolii Bazko
1. Andrew Mak
1. Angel Misevski
1. Beau Morley
1. David Festal
1. Elson Yuen
1. Gennady Azarenkov
1. Ilya Buziuk
1. Jag
1. Jonathan West
1. Joshua Pinkney
1. Mario Loriedo
1. Martha Benitez
1. Mykhailo Kuznetsov
1. Mykola Morhun
1. Nick Boldt
1. Oleksii Orel
1. Radim Hopp
1. Rajiv
1. Sakib Hasan
1. Sergii kabashniuk
1. Serhii Leshchenko
1. Sun Tan
1. Thomas Maeder
1. Tibor Dancs


# 20-January-2020
## Recording
https://youtu.be/1U_ZQ_th5hc

## Notes and Minutes

### Update from teams
#### Elson:
- Codewind team. GA, Jan 23 v0.8.0
- Added support Helm 3 - removal of the insecure non-default tiller
- Planning to propose some changes on devfile definition, e.g. volume definition, commands and actions
#### Mario:
- Want to have a list of teams on Wiki
- Want to have a list of areas on Wiki (need a quick update before assigning teams and labels)
- Want to avoid to set ‘team/**’ label
- If someone is starting to work on the issue, it needs to be assigned to someone

#### Sun:
- new proposal about issue triaging at next call

## Attendees
1. Florent Benoit (taking notes)
1. Andrew Mak
1. Beau Morley
1. Carl Anderson
1. Elson Yuen
1. Jag
1. Jasper
1. John Collier
1. Jonathan West
1. Josh Pinkney
1. Mario Loriedo
1. Martha Benitez
1. Mykola Morhun
1. Rajiv
1. Sarah I
1. Sun Tan
1. Thomas Maeder
1. Travis Wang


# 6-January-2020
## Recording
https://youtu.be/5dBdz2mXlyo

## Notes and Minutes
### Update from Che teams (Sun)
- RH Language team, working on Quarkus extensions (Thomas)

### New teams at Red Hat (Florent)
https://docs.google.com/presentation/d/1WHBFZ1q7ym2jQ2hersSakF48saMrk6v0eEmTvwMfXM0/edit#slide=id.g6d3396950e_2_0

### Web Browsers compatibility improvements
- Better handling with Firefox with like font issues, etc
- If you have problems, please report issues
- Safari: not yet supported, issue on login.

### Update on troubleshooting installation and getting logs (Stevan)
- Tricky to retrieve the logs of the container, etc.
- Epic related to improve the troubleshooting report
  - https://github.com/eclipse/che/issues/14882
  - https://github.com/eclipse/che/issues/15485
- Will help you to retrieve what you’re doing



### TLS by default (Stevan)
Same experience than when using final product
- https://github.com/eclipse/che/issues/14742
- Self-certificate will be provided as well (if no real certificates are provided)

### Better log message when workspace is not starting (Stevan)
Much more easier to get the log and get the root cause (still in progress)


## Attendees
1. Florent Benoit (taking notes)
1. Andrew Mak
1. Beau Morley
1. Fabrice Flore-Thébault
1. John Collier
1. Keith
1. Martha Benitez
1. Nick Boldt
1. Rick Wagner
1. Stevan LeMeur
1. Sun Tan
1. Thomas Mader




# 9-December-2019
## Recording
https://youtu.be/QJnAFsUs43Q

## Notes and Minutes
### Update from Che teams
- Goal is to give more update from each che team from Red Hat
- Being more open to give status

Refactor of the plug-in broker by Angel: PR https://github.com/eclipse/che-plugin-broker/pull/80
Issue: https://github.com/eclipse/che/issues/14494

Benefit: allow to work on each side of the broker separately, and logic could be extracted and used in other places like plugin-registry.etc
-1500 lines dropped after refactoring

Question by Tim: does it affect performance ?

Very easy to improve the downloading process. Workspace starting twice in a row shouldn’t download new stuff anymore
Some logic should be extracted to plug-in service to be a service always available instead of starting/stopping stuff.

### CodeReady Workspaces 2.0 shipped and availability 
- Huge topic for Red Hat teams
- Installation in restricted environments
- All has been developed upstream so AirGap mode is also available in Eclipse Che 7

### UXD work - update 
- Working with Stevan for a while and how to make a plan
- Welcome page use-case for example
- Another item is about theme (colors that developers like, etc)
  - User study
  - Theming survey : https://docs.google.com/forms/d/1i_dOLcQ_HmWwwBIz2C201MhgvTC0ACJbKr6lC1LbVjU/edit
- Stevan: avoid back/forward steps and perform all the stuff directly within the IDE

## Attendees
1. Andrew Mak
1. Angel Misevski
1. Beau Morley
1. Elson Yuen
1. Fabrice Flore-Thébault
1. Florent Benoit (taking notes)
1. Ilya Buziuk
1. John Collier
1. Martha Benitez
1. Mykola Morhun
1. Nick Boldt
1. Oleksandr Andriienko
1. Rajiv
1. Rick Wagner
1. Stevan LeMeur
1. Serhii
1. Sun Tan
1. Tim deBoer
1. Travis Wang


# 25-November-2019
## Recording
https://youtu.be/c8X3khqYEaU

## Notes and Minutes
### Code Owner - review
- Many codeowners but usually other ppl review PR
- Busy people and then it doesn’t work as it seems to be a slow process for external contributors.
- How to move forward ?
  - Update codeowners
  - Responsibility of committers ?
- Conclusion: Postpone : wait new team re-org of Red Hat teams and discuss it after

### Status of Che4Z 
- Broadcom folks online: 
- https://www.eclipse.org/che/docs/che-7/eclipse-che4z/
- Sun: want to get some demos of Che4z. Would be nice in a next call

### Clarification of use of VSCode plugin in Che Workspaces 
- VSCode marketplace term of use does not allow end-users to use direct pointers.
- But we can pull from a running workspace and it’s not compliant with TOS
- Plugin registry shouldn’t have links to the marketplace as well
- Note that some VS Code extensions also can’t be run outside of Microsoft Product based on their license.

### Chatroom snapshot
Stevan LeMeur - 5:03 PM
Agenda for today : https://docs.google.com/document/d/1duuavOXVAJNbzU8nIltraDKx5YH2Z34Qwx7AeLnhhzU/edit
Stevan LeMeur - 5:03 PM
looks empty right now :)
Stevan LeMeur - 5:03 PM
feel free to take 2min to add items you would like to discuss
Ilya Buziuk - 5:05 PM
shouldn't we review codeowners after teams reorg?
Ilya Buziuk - 5:07 PM
There is a mailing thread `Updating Eclipse Che codeowners` started by Angel
Stevan LeMeur - 5:11 PM
https://www.eclipse.org/che/docs/che-7/eclipse-che4z/
Stevan LeMeur - 5:16 PM
https://github.com/eclipse/che-plugin-registry/blob/master/v3/plugins/redhat/java8/0.50.0/meta.yaml


## Attendees
1. Andre Mak
1. Beau Morley
1. Elson Yuen
1. Florent Benoit (taking notes) (thank you!)
1. Fabrice Flore-Thébault
1. Ilya Buziuk
1. Jag
1. John Collier
1. Joshua Pinkney
1. Martha Benitez
1. Mykola Morhun
1. Oleksandr Andriienko
1. Oleksii Orel
1. Rajiv
1. Sergii Kabashniuk
1. Serhii Leshchenko
1. Stevan Le Meur
1. Sun Tan
1. Travis Wang
1. Vitaliy Gulyy


# 28-October-2019
## Recording
https://youtu.be/7nQq_LclZ3I

## Notes and Minutes
### 1. Feedback from Eclipse Con Europe
- Feedback from John, Mario and Florent that were present
- Eclipse Theia day
  - Roadmap about Eclipse Che @ Theia projects
- Good conversations with community
- Typefox want to provide alternate VS Code marketplace
  - Discussed if Che metadata would fit inside this model
- Tim joined the meeting as well
  - Fit to scale (LSP), Workspaces as kubernete resources (David’s talk)
- John: Including codewind plug-ins in Eclipse Che plugin registries.

### 2. Release 7.3.1
- Patch release (tuesday)
- Will be used in Red Hat CodeReady Workspaces

## Attendees:
1. Andrew Mak
1. Angel Misevski
1. Beau Morley
1. Carl Anderson
1. Elson Yuen
1. Fabrice Flore-Thébault
1. Florent Benoit
1. Ilya Buziuk
1. Jag
1. John Collier
1. Mario Loriedo
1. Mykola Morhun
1. Oleksandr Andriienko
1. Oleksii Orel
1. Roman Nikitenko
1. Serhii Leshchenko
1. Steven Hung
1. Tim deBoer
1. Travis


# 14-October-2019
## Recording
https://youtu.be/4ah2OENYxaQ

## Notes and Minutes
### 1. Che Onboarding Concepts - Intro to User Experience Design (Beau Morley)
- Epic related to this work: https://github.com/eclipse/che/issues/14878
- Sharing some work done on che
- Updated Onboarding Concepts presentation link ?
- Studied the different user experience aspects related to the first time use of Eclipse Che.
  - Beau has been studied the different other projects and developers tools on how they are onboarding new users. 
  - Beau has been interviewing users (during various conference and also with various stakeholders in RedHat). 
- Different concepts have been explored and presented during user interviews
- Concepts can be reviewed at: https://docs.google.com/presentation/d/1QYGq2vV4WS-G5Ft4ANIv_INy3RBJ9zYxIeSVQwrKlMQ/edit?usp=sharing 
- You can take the concept survey at: https://forms.gle/jQNR3LW3eNREwe3V6
- Email bmorley at redhat dot com if you have trouble accessing the concepts or survey 

## Attendees:
1. Beau Morley
1. Carl Anderson
1. Dave Neary
1. Fabrice Flore-Thébault
1. Florent Benoit
1. Ilya Buziuk
1. Radomir Ludva
1. Rick Wagner
1. Sergii Kabashniuk
1. Stevan LeMeur
1. Sun Tan
1. Thomas Maeder


# 30-September-2019
## Recording
https://youtu.be/XCr_6LOR6Rs

## Notes and Minutes

### 1. Triaging issue (Sun)
* Explain the process in the wiki 
* Sun: not clear enough for external people how the triaging is done
* AI: Mario will take the action item

### 2.  Maybe we should have some youtube channel with video tutorials about Eclipse Che (Olexandr)
* Sun: anybody could send videos
* Sun: Channel could be listed somewhere -> to the website and readme: https://www.youtube.com/channel/UChhI38Rvs5q1-JmmULHRiSw 
* Link published on the website ?
* Gorkem: What are the steps to upload content to youtube channel ?
  * Open github issue + add label ‘website’ on this issue

### 3. Definition of Done (Gorkem):
* Definition of done will be done by updating the templates and all reviewers/code owners need to be responsible before merging the PR to ensure that the doc is ready and that QE endorsed enhancements/modifications
  * If you’re reviewing a work, you’re testing it → as responsible as the author.
  * Should be easy to test and review a PR
    * Enhancements to have workspace allowing to test a given PR (not there yet but in **next** plans with a one-click button)
  * Theia community is expecting all reviewers test the PR before giving the approval and not provide a LGTM approval
  * AI to ? : update templates and enforce them

### 4. An Update about Che 7 launch (mario)
* Announced tuesday 17
* Eclipse foundation with press release announcement : good coverage on blog posts, etc.
* Social media activity, twitter, etc.
* Blog post about Che 7: release notes: most read blog post of all time
  * https://che.eclipse.org/eclipse-che-7-is-now-available-40ae07120b38
* New blog posts about discovering Eclipse Che on the way to go by Florent
  * https://che.eclipse.org/discover-eclipse-che-7-7515e74a99ca
* More than welcome to write new blog post and discuss it on che-dev mailing list.
  * Opening a github issue to publish a blog post
  * AI: needs to be documented somewhere

### 5. Demo
Che-ansible

## Attendees
1. Andrew
1. Artem Zatsarynnyi
1. Beau Morley
1. Carl Anderson
1. eyuen
1. Florent Benoit
1. Gorkem Ercan
1. Jag
1. Mario Loriedo
1. Stevan Le Meur
1. Martha Benitez
1. Michal Vala
1. Mykola Morhun
1. Nick Boldt (joining late)
1. Rajiv
1. Oleksii Orel
1. Rick Wagner
1. Sergii Kabashniuk
1. Stevan LeMeur
1. Steven Hung
1. Sun Tan
1. Thomas Mader
1. Viktor Kusnietsov
1. Vitaliy Gulyy
1. Yevhen Vydolob

# 16-September-2019
No topic discussed

# 2-September-2019
## Notes and Minutes:
### Closing 6months old issues (Mario):
* https://github.com/eclipse/che/issues/14401
* Apply to all issues
* Apply a new label if closed by bot
* Apply a new label if pending to be closed
* Let users to comment for one week to avoid deletion
* Sun: Inform the user to close it by himself
* Find a proper message to not be so rude

### Release Che 7.1.0 (Mario)
* New release will be started tomorrow
* Two steps:
   * Day 1:  plugins and devfile registries/ che-theia / machine-exec
   * Day 2 : che-server release + chectl + che operator
* Bugfixes
* End-to-end tests improved with improved PR
* C++ support will be delayed
* Ilya in charge of the release this time: ping him if needed

## Attendees
1. Oleksandr Andriienko
2. Florent Benoit
3. Ilya Buziuk## Recording
4. Mario Loriedo
5. Mykola Morhun
6. Oleksii Orel
7. Sun Tan
8. Vitaliy Gulyy

## Recording
https://youtu.be/IuIkup-ktww

# 19-August-2019
## Agenda:
* Che/Theia community day @ EclipseCon - Martha
* GSoC update - Sun/Rijul
* Che 7.0.0 release - Mario/Stevan
* Status of Happy Path testing - Gorkem (Red Hat)

Agenda and minutes:  [Google Doc](https://docs.google.com/document/d/e/2PACX-1vTFLD0qDuALDIxlMXo6GlXqcy1HIdpeOwuD0vNaP6vneXu1Piv_AWhlGjpD-xAM71oGOKvJwlxwKT_c/pub) / [YouTube video](https://youtu.be/Nz-8ilM3Cw4)



# 5-August-2019
## Agenda:
* Propose and vote for your demo - Sun (Red Hat)
* Open discussion: Questions/Answers about Che7 release - Sun (Red Hat)
* Accepted talks for Eclipse Con Europe - Sun (Red Hat)

Agenda and minutes:  [Google Doc](https://docs.google.com/a/redhat.com/document/d/e/2PACX-1vT1cHRV1NOAjbZ13FwWZpGO38BTeoQ48_q6OqrraHVos6XvTdcXlck48ORgKEQrfLA2xRzoBQTQH3Bv/pub) / [YouTube video](https://youtu.be/sXKYV_wszvk)



# 22-July-2019
## Agenda:
* Che 7.0 GA updates- Mario (Red Hat)
* Multiple Registries- Toby (IBM)
* 7.1 / 7.2 milestone issues - Stevan (Red Hat)

Agenda and minutes:  [Google Doc](https://docs.google.com/document/u/1/d/e/2PACX-1vT2PveEGZ1X9BFsvhiV4g-wDKOIlFkW5itgujNFeC4jY9XSEiPi8Ov0-IxcEVSHUx4T2NzC13LP91HX/pub) / [YouTube video](https://youtu.be/PapBkNZm2j8)


# 8-July-2019
## Agenda:
* Che7.0 GA End Game (Mario / Stevan)
* Sharing your feedback, bugs, feature requests for Che 7 (Stevan)
* Website Repository (Sun)
* EclipseCon 2019 (Stevan / Martha)
* New templates for Github issues #13777 (Florent)
* Workspace Creation/Deletion API (Maysun)

Agenda and minutes:  [Google Doc](https://docs.google.com/a/redhat.com/document/d/e/2PACX-1vRsVTmXUGKGZhSeXFD75ymOk1Vs-bqQdxgX5z9ltrZRtb4-tFbD9tx06PF_vtD93yYCnUkD_DHcmIuH/pub) / [YouTube video](https://youtu.be/uxYklqFx-JM)



# 24-June-2019
The Che Community Call for June 24th has been cancelled.

# 10-June-2019:
## Agenda:

* Presenting Grafana monitoring and dashboard for che.openshift.io (Sergii Kabashniuk)
* Process to add official workspace templates/stacks to Che (John Collier)
* Picking up Theia changes into che-theia: [Theia PR](https://github.com/theia-ide/theia/pull/5310) (Tim Etchells)

Agenda and minutes:  [Google Doc](https://docs.google.com/document/d/1hb7Bu3gCDs_kVc8A2PAvhL2XzLApnkEI2t2MMgVq-8Y/edit?usp=sharing) / [YouTube video](https://youtu.be/DRm-c36Z7UY)

# 27-May-2019:
## Agenda:

* Plan for Operator support (Elson)

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1C-bWzG_8_rSfHsH_F7_8v91LD3Ljy-9MkTHCwkIf00E/edit?usp=sharing)

# 13-MAY-2019
## Agenda

* Devfile application demo (Mongo + Node app) - Serhii L and Angel
* Devfile repos - Tim deBoer
* Eclipse Che presence at KubeCon EU 2019 - Dave Neary

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1BCqOEmtBzMenAQUqFtPBC_aYd3vZI20tng-h-tH2Azg/edit?usp=sharing)

# 29-APR-2019
## Agenda

 - Question aout Kubernetes components in Devfiles (Rajiv)
 - Question about passing OIDC client secrets into Che (John)
 - Community Spotlight: IBM (Tim)

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1qHEPfTP4x0LhpliTcPRWisss4agD7XzgLlA27kXh9YU/edit)

# 15-APR-2019
## Agenda

 - Overview of Che 7 (Stevan)
 - Che 7 demo (Stevan)

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1z8yxhjcrhxqYPupx5-XesfmUMEH4x8Zx3h17KZkOVTo/edit)

# 01-APR-2019
## Agenda

 - Selection of Demo videos from Che 7 beta 2
 - Community Spotlight: TU Delft students on Software Architecture

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1ASkwloswJ_70oc-7MQvt2kIBljWdBoSS_Z72vU9KlxE/edit)

# 18-MAR-2019
## Agenda

 - Improve documentation for Extensions/Plug Ins/General Architecture
 - Future of single user Che under Docker
 - Running Che and Che workspaces as non root

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/12lbNn37Sj1PuW8ioKSnfcy-4nJzqml2sBwJY98mc6OU/edit)

# 4-MAR-2019
## Agenda
 - Community Spotlight: CloudToGo (Hongxi Ma, Di Wu)
 - Questions on the status of Eclipse Che beta and target date for GA (Barry, Jason, Rashmi)

Agenda and minutes: [Google Doc]
(https://docs.google.com/document/d/1rcgy5u9kktHeTECJ2LSPEwf0oJJZh5eBGmRLoB4f9Rw/edit)

# 18-FEB-2019
## Agenda
 - Introduction to chectl (Mario Loriedo)
 - Planning Eclipse Che event participation for 2019 (Dave Neary)

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1Z7guNbcvjrpbJgec1xvUFkzP5IU2gabyDtT_n1LwwZ8/edit#)

# 4-FEB-2019
## Agenda
 - Status of Che tracing and monitoring (Sergii Kabashniuk)
 - Che 7 beta status (Mario Loriedo)
 - Feedback from FOSDEM (Ilya Buziuk)

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1-SVy_fOLtvg2RmzsiXCmwiQPRiu6S0rTpwJlGYEH4IA/edit#)

# 21-JAN-2019
## Agenda
 - Creation of generic presentation materials for Che community
 - Che 7 launch promotion

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1v7hfGTawLgkpsLJOmo1iIrQw7R7RJxh1Ul4NQ7Gn4Ik/edit#)

# 14-JAN-2019
## Agenda
 - Community Spotlight: Software AG

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/16dsjMpeku0eXrjdHw0cHejFCfXGr-LKy40h6_-4JW1w/edit#)

# 10-DEC-2018
## Agenda
 - CORS, Docker, GWT IDE,  Java version
 - Will stacks created in Che 6.x work unchanged in Che 7? 
 - CheConf 2018.2 - Summary
 - Che Incubator repository
 - Introducing new Che CLI

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1W1eoUZl5jR7LpycvutDbcsvZj9MJb97Ft05AdcLrjDo/edit#)


# 26-NOV-2018
## Agenda
 - Eclipse Cloud Development Tools Working Group
 - CheConf18.2
 - Calling for blog post about Che 7

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/1KDdbufXTPelEhTmuWwhgOdUhFOEYD_DR_W2Z213ZCVE/edit)

# 12-NOV-2018
## Agenda
 - Community Spotlight: CA
 - Eclipse Cloud Development Tools Working Group
 - Docker support for Eclipse Che

Agenda and minutes: [Google Doc](https://docs.google.com/document/d/18nHnwL6X6RfV_raC4HEWFAxSqk_nnf8HbfF7axuaY7k/edit#heading=h.o6hsjafth35v)

# 29-OCT-2018
## Agenda
- EclipseCon feedback
- Docker support

Minutes: [Google Doc](https://docs.google.com/document/d/1ir4Fp7_YKHZXWprZUwj3IQU1JhuJu-7Qmh5Xyiyf408/edit)

# 15-OCT-2018
## Agenda
- Community Spotlight: Progress Software
- The current integration topics of Theia and Che (Execution Agent, LSP, WS Master…), and the way forward (roadmap)
- Eclipse Industry Working Groups: https://www.eclipse.org/org/workinggroups - vision, goal, scope, expectation

Minutes: [Google Doc](https://docs.google.com/document/d/1peSkmboH6QLn1_gXIocKXr8Y1N42cSqtmCxSVDqAQ2s/edit)

# 01-OCT-2018
## Agenda
- Introducing Community Spotlight
- MySQL TCK
- Java 11 + ws-master

Minutes are in [Google Doc](https://docs.google.com/document/d/1ZFT0x7N3WXMFHI_CYJtKHMfxdMtEfBRWwgbmeFCucNE/edit#)

# 17-SEP-2018
## Agenda
- Release version vs. Master version (or Che 7 / WS.Next) - QA level, Different Fix policy, Double Maintenance
- Che WS Master bootstrapper, stdout, K8s Pod restart (refer also to WS.Next)

Minutes are in: [Google Doc](https://docs.google.com/document/d/1AJZRnPN0POH23FyKsLm4FA4du1pcuFuibpi1if5eRDI/edit)

# 3-SEP-2018
## Agenda
- Imminent switch to jdt.ls in Che 6 

Minutes are in: [Google Doc](https://docs.google.com/document/d/1DzMQxW9TpPlxs0U_ujjegjXX2BUMd25Pq9q99mfgTIA/edit?usp=sharing)

# 20-AUG-2018
## Agenda
- Che 6.x timeline
- Workspace restart strategy
- Accessibility, Localization, Internationalization

Minutes are in: [Google Doc](https://docs.google.com/document/d/1OODjdZXMM4TKb9-2GCMHBQTs-pYjTkXjJ_TNzUC-PcM/edit)

# 6-AUG-2018
## Agenda
- Security
- Scalability and high availability
Minutes are in: [Google Doc](https://docs.google.com/document/d/1F33n2pQyJHyu9jcVXjXCFqworNg3gpvmhco0ULwloDE/edit#heading=h.2baooh7o19a8)


# 16-JULY-2018
## Agenda
Dedicated session to:
- Log - https://github.com/eclipse/che/issues/10290  
- Trace - https://github.com/eclipse/che/issues/10298  
- Monitor - https://github.com/eclipse/che/issues/10329 

Minutes are in: [Google Doc](https://docs.google.com/document/d/1yF6DjW6chfuit-oHZmrGqvv2-1Y2tSN1j4YLhQPgVCM/edit#)

# 9-JULY-2018
## Agenda

1. Overview of Workspace.next
2. Review of logging, tracing, analytics epics (deferred to next meeting)

Minutes are in: [Google Doc](https://docs.google.com/document/d/19V5l8cVyhfDyhoaATIkLlt7NRbGIMS9dNgvotGMU0ys/edit)


# 25-JUNE-2018
## Agenda


1. Feedbacks from Eclipse Con France
2. Telemetry, Monitoring and Logging in Eclipse Che
3. Conferences for late October: Eclipse Con EU & Che/Theia day

Minutes are in: [Google Doc](https://docs.google.com/document/d/1qrLyknhv9-1J7Oj5ZR74FrBiSWQipNRFayaYOSQ2xxo/edit#heading=h.o6hsjafth35v)

# 11-JUNE-2018
## Agenda

1. Authentication in Next.Gen Che
2. Eclipse Con France
3. Eclipse Con Europe - Che & Theia contributors summit
4. Blog topics
5. Improving our community calls
5. New capabilities (agents) on current Che

Minutes are in: [Google Doc](https://docs.google.com/document/d/1yvpmOHY2j8tw19ol-CgeD-2p7cnzVddqij2Ue92q2ds/edit?usp=sharing)

# 28-MAY-2018
## Agenda
1. Use a single document for the Community Call Agenda
2. PR https://github.com/eclipse/che/pull/9826 
3. Eclipse Con EU
4. Status on Extensibility / Plugin

Minutes are in: [Google Doc](https://docs.google.com/document/d/1kp1F2-hdi-Cm5IrZzNHZE6xENRY0NCS9EnpwvK6zdMU/edit?usp=sharing)

# Minutes 14-MAY-2018
## Agenda

1. Handling of issues with severity/blocker label
2. RedHat Summit + KubeCon read out
3. Release planning and community roadmap

Minutes are in: [Google doc](https://docs.google.com/document/d/13UG7Jiam6fdxduETKv3Rc3iquQhrJq7XKbVA74DTuzY/edit?usp=sharing)

[Recording](TODO)


# Minutes 16-APR-2018
## Agenda

1. Consolidating the stacks
2. Hot Update (#8547)
3. CI for kubernetes infrastructure
4. Branding dashboard question(https://github.com/eclipse/che/issues/8421 )
5. Eclipse Theia proposal
6. Welcome to Guy Daich and introducing Dave Neary
7. Keycloak configurability

Minutes are in: [Google doc](https://docs.google.com/document/d/1p0Li9SeUcowy6AW5aVVpgKh6bRNgHHPuD3CMGJ94Gos/edit#)

[Recording](https://bluejeans.com/s/B_oPF)

# Minutes 02-APR-2018
## Agenda

1. Type A/B - License Compatibility Certification
2. Workspace.Next implementation plan
3. Blogging - open invitation
4. Roadmap
5. Workspace logging

Minutes are in [Google doc](https://docs.google.com/document/d/1w1BWMiHJHa-bSfYnSYcNjCXMl-9IM4EqvmwlnMYu8Jc/edit)

[Recording](https://bluejeans.com/s/F4FVo/)

# Minutes: 19-MAR-2018
## Agenda

1. Kubernetes SPI - Mario
2. Workspace recovering after disasters - Mario

Minutes are in [Google doc](https://docs.google.com/document/d/1xYhF3iiKaboIhHRng-prBuPWJ2HLfqP7MxCrpirMJJ8/edit?usp=sharing).

[Recording](https://bluejeans.com/s/J1KC@)


# Minutes: 05-MAR-2018
## Agenda

1. Explain guides for PR flow - Segii


Minutes are in [Google doc](https://docs.google.com/document/d/1FR5UjquA4dJUjBRK9Ncn5iCgUXGk2R1wlBLWh4ricLA/edit#heading=h.gecm5gxb51ub).

[Recording](https://bluejeans.com/s/8z_zj)


# Minutes: 05-FEB-2018
## Agenda

1. Introductions (if needed) - Gorkem
2. The state of the Che 6 release - Roman
3. Documentation for Che 6 and going forward - Eugene
4. Update on kubernetes SPI implementation - Sergii

Minutes are in [Google Doc](https://docs.google.com/document/d/1bxpBC9ZDg80Sv8XMSJz1pzAmnsAa6pIKzT4mryuAjaE/edit#)


# Minutes: 22-JAN-2018
## Agenda
1. Introduction to CloudToGo - Hongxi (CloudToGo)
2. Reminder on GSoC 2018 - Stevan (Red Hat)
3. Che 6 GA - Stevan (Red Hat)
4. K8s support for Che 6 - Gorkem (Red Hat)

Minutes are in [Google doc](https://docs.google.com/document/d/1KZUuLl7uaa214SN-XiUAXiRp3PXR_if7wWBmhOd3He0/edit#).

[Recording](https://bluejeans.com/s/zExZQ)


# Minutes: 08-JAN-2018
## Agenda
1. Latest update from Che - Gorkem (Red Hat)
2. JS API status - Gorkem (Red Hat)
3. Teletype integration demo - Sun (Red Hat)
4. Performances Improvement and JDT.LS - Stevan (Red Hat)
5. CLANGD Language Server - Hanno (Silexica)
6. Internationalisation - Hongxi (Cloud To Go)
7. Migrating of connector done on Che5 for specific container orchestrator - Hongxi (Cloud To Go)
8. Kubernetes Connector for Che - Guy Daich (SAP)
9. Network isolation - Guy Daich (SAP)
10. Conferences and Meetups - Hongxi (Cloud To Go)

Minutes are in [Google doc](https://docs.google.com/document/d/1I4R9svIt-X2UEPtZq-zxuNamfiJwrh_3d0I3uLJrawg/edit#).

[Recording](https://bluejeans.com/s/V2aLA)

# Minutes: 11-DEC-2017
## Agenda
1. Release documentation and marketing - Gorkem Ercan (Red Hat)
2. Blog post on Docker checkpoint with criu - Florent Benoit (Red Hat)
3. Status on teletype in Che - Sun Tan (Red Hat)
4. CheConf update - now targeted for mid-February 2018 - Brad Micklea (Red Hat)
5. Moving Che6 on master and Che5 on bugfix branch - Gennady Azarenkov (Red Hat)
6. The way how to solve different vision on UX design of Eclipse Che Sergii Kabashniuk (Red Hat)

Minutes are in [Google doc](https://docs.google.com/document/d/1a2L5J1NUWCoE_lPvczqmiFRGYpC2ubTPXDMyCgVA-co/edit).

[Recording](https://bluejeans.com/playback/s/wx7KbGK8xikQl7xCyx0oQmuwbZZbwpc3jhzoAeUBDwOlTYQLPABPVwYjnRZ53BUK)

# Minutes: 27-NOV-2017
## Agenda

1. Update on Che 6 GA plan and release - Stevan LeMeur (Red Hat)
2. C/C++ intellisense / ClangD support for Che - Hanno Kolvenbach (Silexica)
3. Che in Che development - Sergii Kabashniuk (Red Hat)
4. Che IDE extensibility with JS plugins - Evgen Vidolob (Red Hat)

Minutes are in [Google doc](https://docs.google.com/document/d/1X-FgyawYUyiNfFlr9i-9XYh55vOVXp9GVwTujGGaOE4/edit#).

[Recording](https://bluejeans.com/s/Tz68h/)

# Minutes: 13-NOV-2017
## Agenda

1. JS Extension points - Vitalii Parfonov (Red Hat)
2. Sidecars - Sergii Kabashniuk (Red Hat)
3. GWT Improvements - Vitalii Parfonov (Red Hat)
4. CheConf - Pushed to February - Stevan Le Meur (Red Hat)

Minutes are in [Google doc](https://docs.google.com/document/d/1jF38p1KHLVxvOSc1NtyvkBziJrmGegEx9-QBZGRFuMw/edit#).

# Minutes: 30-OCT-2017
## Agenda

1. Update on EclipseCon Europe - Stevan Le Meur (Red Hat)
2. SAP Che use case - Ido Perea (SAP)
3. Software AG use case - Barry Dresdner (Software AG)
4. More communication with the community - Stevan Le Meur (Red Hat)
5. CheConf 2017 - Brad Micklea (Red Hat)

Minutes are in [Google doc](https://docs.google.com/document/d/1SCPQ_070TmQqiaP9NgX415nk96k6jTFvKN4SuVX7ygw/edit?ts=59f731d6#heading=h.ly09ur7fsmgi). The meeting was also [recorded](https://bluejeans.com/s/VTNBJ).

# Minutes: 16-OCT-2017
## Agenda
You can read the notes on the following [Google doc](https://docs.google.com/document/d/1ViUyMbcbOOUPWC2aFCN1mXZPX7B2ux4jwcOnjLSFbOQ/edit). 

# Minutes: 02-OCT-2017

## Agenda

0. bmicklea: Triaging the Che issues and proper labelling.
1. bmicklea: Status of multi-user support in Che and how much of "teams" it brings with it.
4. skabashniuk: Eclipse Che 5.19 and Eclipse Che 6.0-M1 or 6.0-RC1 release plan.
5. skabashniuk: Che 6: single multi-user assembly (Docker + OpenShift) based.
2. bmicklea: JIRA and Jenkins plugins from Codenvy - should we prioritize? 
3. Bmicklea: how do we speed up integration of released Language servers?
7. bmicklea: Where can external contributors / partner companies help us most?  How can we enable them?

Actions:
0. @Brad update pull request template. Add more explanation on the wiki. @mario do a call with Californication team to explain about labels usage in Che
1. Expected to be merge in the current sprint.
4-5. We need additional meetings to provide consolidated vision. @skabashniuk @ivantsov provide some estimation how much memory is used by postgresql and keycloak.
3-7 Not discussed. Moved to the next meeting.
***

# Minutes: 18-SEPT-2017

## Agenda

1. Update on progress toward Che 6 
2. Update on multi-tenant Che running on OpenShift).
3. Changelog structure in PR (Stevan)
4. Critical issue with Che IDE: browser freezes all the time (Sun)
5. Upcoming conferences, events and talks (Stevan)

***

### Multi tenant Che on OpenShift

Auth and permissions are already in the branch. Working on OS tokens and porting resource management from Codenvy. Merge is expected end of next sprint.

### Update on progress toward Che 6 

Work to be done on factories, commands and pull request panel. Setting up tests on Minishift and looking into testing Che 6 on OCP, OpenShift Dedicated.

### Changelog structure in PR
Today, we provide templates for PR with placeholder for docs, related issues that it fixes etc. There's changelog section as well, but it is never used when changelog is generated (only pull request titles are taken into account).

Proposal: Edit PR template with some notes saying that the PR title looks good and is informative. Maybe provide examples of good and bad PR titles. In future, consider adding info on APi changes in changelog (if any).

### Critical issue with Che IDE: browser freezes all the time

Problem: with a few big projects in a workspace, browser tab hangs. It may be related to a lot of pending calls to project API. Needs proper investigations.

Action: Vitaly Parfonov and Eugene Ivantsov will try to reproduce and then prioritize.

### Upcoming conferences, events and talks

There needs to be a page with info on conferences and talks about Che. Also, it will be great to invite community members to Che Conf which is an online Che conference.

# Previous Meetings
- [4-Sept-2017 Minutes](#minutes-4-sept-2017)
- [Older Meetings](#old-meeting-minutes)

***

# Minutes: 4-Sept-2017

## Attendees:

- Stevan Le Meur
- Roman Iuvshyn
- Florent Benoit
- Eugene Ivantsov
- Ann Shumilova
- Gennady Azarenkov
- Sergii Kabashniuk
- Vitaly Parfonov
- Mario Loriedo

## Agenda

1. Define how to communicate about the community call (Stevan)
2. Move community call minutes from CHE wiki ?
3. Put link to che community call inside the CHE product.

## Minutes

### Communicating about the community call
- community meeting runs each second monday
- community meeting should have a permanent link
- we do record each meeting

Proposals:
- we prepare the agenda for the next community call - right after the end of the current one
we post an email + on MM the link to the meeting minutes + the link to the next agenda and invite people to propose their topics to the wiki (or by answering the email + asking in MM)
- Add a link for the call right in IDE which is quite interesting because this way we will cover people that don't know about our twitter or not subscribed to che-dev mail list.
- we will also include a link into the product to the MM channel (action for stevan)


Actions:
- @slemeur create an issue to add links to MM + community call inside the IDE

### Move community call minutes from CHE wiki
Problems:
- We have a lot of wiki pages for the meeting minutes which creates navigation problem, if the reader is just using "Pages" panel

Proposals:
-  archive the old meeting minutes

Also discussed:
- keeping the old meetings can allow people to find interesting information by searching in the wiki
- there is no other place where we could move the meeting minutes

Actions:
- improve the homepage of che's wiki so that it better help the reader to navigate into the content of the wiki. 

***


## Old Meeting Minutes ##
[Minutes: Aug 21, 2017](https://github.com/eclipse/che/wiki/Minutes:-August-21,-2017)  
[Minutes: July 10, 2017](https://github.com/eclipse/che/wiki/Minutes:-July-10,-2017)  
[Minutes: July 3, 2017](https://github.com/eclipse/che/wiki/Minutes:-July-3,-2017)  
[Minutes: May 10, 2017](https://github.com/eclipse/che/wiki/Minutes:-May-10,-2017)  
[Minutes: May 2, 2017](https://github.com/eclipse/che/wiki/Minutes:-May-2,-2017)  
[Minutes: April 11, 2017](https://github.com/eclipse/che/wiki/Minutes:-April-11,-2017)  
[Minutes: April 4, 2017](https://github.com/eclipse/che/wiki/Minutes:-April-4,-2017)  
[Minutes: March 28, 2017](https://github.com/eclipse/che/wiki/Minutes:-March-28,-2017)  
[Minutes: March 14, 2017](https://github.com/eclipse/che/wiki/Minutes:-March-14,-2017)  
[Minutes: March 7, 2017](https://github.com/eclipse/che/wiki/Minutes:-March-7,-2017)  
[Minutes: February 28, 2017](https://github.com/eclipse/che/wiki/Minutes:-February-28,-2017)  
[Minutes: February 21, 2017](https://github.com/eclipse/che/wiki/Minutes:-February-21,-2017)  
[Minutes: February 14, 2017](https://github.com/eclipse/che/wiki/Minutes:-February-14,-2017)  
[Minutes: February 7, 2017](https://github.com/eclipse/che/wiki/Minutes:-February-7,-2017)  
[Minutes: January 31, 2017](https://github.com/eclipse/che/wiki/Minutes:-January-31,-2017)  
[Minutes: January 24, 2017](https://github.com/eclipse/che/wiki/Minutes:-January-24,-2017)  
[Minutes: January 17, 2017](https://github.com/eclipse/che/wiki/Minutes:-January-17,-2017)  
[Minutes: January 10, 2017](https://github.com/eclipse/che/wiki/Minutes:-January-10,-2017)  
[Minutes: January 3, 2017](https://github.com/eclipse/che/wiki/Minutes:-January-3,-2017)  
[Minutes: December 27, 2016](https://github.com/eclipse/che/wiki/Minutes:-December-27,-2016)  
[Minutes: December 20, 2016](https://github.com/eclipse/che/wiki/Minutes:-December-20,-2016)  
[Minutes: December 13, 2016](https://github.com/eclipse/che/wiki/Minutes:-December-13,-2016)  
[Minutes: December 6, 2016](https://github.com/eclipse/che/wiki/Minutes:-December-6,-2016)  
[Minutes: November 29, 2016](https://github.com/eclipse/che/wiki/Minutes:-November-29,-2016)  
[Minutes: November 22, 2016](https://github.com/eclipse/che/wiki/Minutes:-November-22,-2016)  
[Minutes: November 8, 2016](https://github.com/eclipse/che/wiki/Minutes:-November-8,-2016)  
[Minutes: November 1, 2016](https://github.com/eclipse/che/wiki/Minutes:-November-1,-2016)  
[Minutes: October 18, 2016](https://github.com/eclipse/che/wiki/Minutes:-October-18,-2016)  
[Minutes: October 11, 2016](https://github.com/eclipse/che/wiki/Minutes:-October-11,-2016)  
[Minutes: October 4, 2016](https://github.com/eclipse/che/wiki/Minutes:-October-4,-2016)  
[Minutes: September 27, 2016](https://github.com/eclipse/che/wiki/Minutes:-September-27,-2016)  
[Minutes: September 20, 2016](https://github.com/eclipse/che/wiki/Minutes:-September-20,-2016)  
[Minutes: September 13, 2016](https://github.com/eclipse/che/wiki/Minutes:-September-13,-2016)  
[Minutes: July 19, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-07.19.2016)  
[Minutes: July 12, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-07.12.2016)  
[Minutes: July 5, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-07.05.2016)  
[Minutes: June 29, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-06.29.2016)  
[Minutes: June 21, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-06.21.2016)  
[Minutes: June 14, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-06.14.2016)  
[Minutes: June 6, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-06.07.2016)  
[Minutes: May 31, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-05.31.2016)  
[Minutes: May 23, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-05.23.2016)  
[Minutes: May 17, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-05.17.2016)  
[Minutes: May 10, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-05.10.2016)  
[Minutes: April 25, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-04.25.16)  
[Minutes: April 19, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-04.19.16)  
[Minutes: April 12, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes---04.12.16)  
[Minutes: April 5, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-04.05.2016)  
[Minutes: March 29, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes---03.29.2016)  
[Minutes: March 22, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-03.22.2016)  
[Minutes: March 15, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes---03.15.2016)  
[Minutes: March 01, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-03.01.2016)  
[Minutes: February 23, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-02.23.2016)  
[Minutes: February 16, 2016](https://github.com/eclipse/che/wiki/Meeting-Minutes-02.16.2016)  
