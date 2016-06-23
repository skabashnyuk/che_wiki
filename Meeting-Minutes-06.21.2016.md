Here are the notes of product meeting June 21th, 2016.

######TOPICS DISCUSSED:

1. Scope for 4.4
2. Scope for 4.5 / Scope for 4.6
3. Review Q3 Goals

######ACTION ITEMS:
- 
- 

######IMPORTANT POINTS ON TOPICS DISCUSSED:

**1. Scope for 4.4**

Shipping Date: 30th June
Start Release Process: 24th June

Are the dates still accurate and possible?

The scope is limited to:
- Support for private docker registry
- New UD/IDE Navigation Experience

What about JGit Status? Has it been heavily tested by QA, before enabling it?

CHE-1296: in code review and will be finished this week
CHE-1134: Oleksii finishing it today
CODENVY-614: not yet started, planned for next sprint
CODENVY-644: planned for next sprint. Seems "easy"
others are in progress

Bugs
CODENVY-677: linked to new navbar navigation
CHE-1338: take into next sprint, moved to 4.5.0
CODENVY-672: root cause identified, looking at the best solution
CHE-1276: next sprint, hard to reproduce it every times, moved 4.5.0
CHE-1354: next sprint
CHE-1335: in progress
CODENVY-606: next sprint, moved to 4.5.0
CODENVY-670: keep 4.4.0
CHE-1342: almost done by Oleksii
CHE-1345: closed as project view will be removed (keep only workspace view)
CHE-1346: next sprint, 4.4.0
CHE-167: need merge
CHE-1357: commands are not updated in the IDE if commands are created with REST

Issues about exporting a workspace will be created.


After friday, no new features, only blocker bugfixes. If features are not ready by friday, it will shift the release date and the shipping date. 


We also discussed about the signing process for binaries. We had a long living issues with that topic and Guice 4.1 has just been released. We agreed to study the impacts and try to upgrade with Che 4.4. This way we will be able to provide signed binaries for Che to the community and avoid more than 1200 downloads a week going to the old version available on Eclipse's Servers. 


**2. Scope for 4.5 / Scope for 4.6**

Scope for 4.5 has been discussed. We would reduce the scope to the following items:
JGit + new URL pattern 
Depending on the state we might be able to take the unification of databases. Status on JPA: for now support of MySQL and H2 database

New page for migration/upgrade=
Roman: get previous stuff done work that in 3.x and check with Stevan for UI, etc.


This WOULD GO TO 4.6
Focus would be given to the following items: 
- Ability to add / remove / update stacks + templates from within UD
- Ability for user to change RAM for workspace within UD
- Usability cleanup of the tables in UD 
- (maybe) simple UI improvements to the IDE to soften some of the colors and reduce the black lines

We'll continue to include any critical or blocker bugs that can be resolved in a short order.


**3. Q3 Goals**

We reviewed goals discussed by emails.
We'll need to split those goals and assign a PO per topic. PO will be responsible for owning the spec and the feature. Specifications will on the Che public wiki and be open to community




