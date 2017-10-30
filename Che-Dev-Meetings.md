## Purpose and Audience ##
These conference calls are meant for the Che adoptors and contributors to chat about some project development details (can be planning, concerns, or more technical details). The goal is to better synchronize and organize efforts of the various contributors in order to make Che better.

It's open to anyone interested. You don't need to have a long history with Che to attend the talk, listen and ask relevant questions.

## When and Where ##
These meetings take place every second Monday, 8:00 AM PST. You can be part of the meeting (mic + chat + video cam) with [BlueJeans](https://bluejeans.com/478856747/4056). Chat link updated 22-Aug-17.
***

# Minutes: 30-OCT-2017
## Agenda
You can add topics to the agenda in this [Google doc](https://docs.google.com/document/d/1SCPQ_070TmQqiaP9NgX415nk96k6jTFvKN4SuVX7ygw/edit?ts=59f731d6#heading=h.ly09ur7fsmgi). See you all there!

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
