## Purpose and Audience ##
These conference calls are meant for the Che adopters and contributors to chat about some project development details (can be planning, concerns, or more technical details). The goal is to better synchronize and organize efforts of the various contributors in order to make Che better.

It's open to anyone interested. You don't need to have a long history with Che to attend the talk, listen and ask relevant questions.

## When and Where ##
These meetings take place every second Monday, 8:00 AM PST. You can be part of the meeting (mic + chat + video cam) with [BlueJeans](https://bluejeans.com/2488406763). Chat link updated 18-Mar-19. Calendar [link](https://calendar.google.com/event?action=TEMPLATE&tmeid=NzBzajBjOWtjNG82Y2I5azYwcjMwYjlrNnNxMzhiYjFjY3A2OGI5bzc1Z21jcGhwY2NyamlkcjNjOF8yMDE5MDcwOFQxNTAwMDBaIHN1dGFuQHJlZGhhdC5jb20&tmsrc=sutan%40redhat.com).

# Next meeting 23-December-2019
The next Che dev meeting will take place on Monday December 23th 2019. You are welcome to add the topics you would like to discuss or propose a demo during the call: [Google Doc](https://docs.google.com/document/d/1duuavOXVAJNbzU8nIltraDKx5YH2Z34Qwx7AeLnhhzU/edit?usp=sharing)

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
