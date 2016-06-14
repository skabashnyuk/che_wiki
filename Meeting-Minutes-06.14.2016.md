Here are the notes of product meeting June 14th, 2016.

######TOPICS DISCUSSED:

1. Status on 4.3 release
2. Scope for 4.4
3. Scope for 4.5
4. Having all issues public

######ACTION ITEMS PREVIOUS WEEK:
- Gennady + Stevan: plan meeting to do release retrospective on 4.3
- Florent: plan meeting to share feedback about tools identified to handle Agile flows with GitHub.


######IMPORTANT POINTS ON TOPICS DISCUSSED:


**1. Status on 4.3 release**

- project-type estimation on import is not behaving exactly as expecting. We have some situations where the estimation is not correct and those situations where not handle in UD. 

- snapshots from version 4.2.x will need to be converted to 4.3.x. Migration script has been written and ready.

- release binaries would be prepared tomorrow and ready for ship events.

- release review started from Eclipse side. We will not have signed binaries for this release as we are still waiting a fix in Guice. https://github.com/google/guice/issues/1006 We had discussed with Sam and he hope to provide a fix for middle of next week.

- few parts of the documentation needs to be refined with the new features added.

**2. Scope for 4.4**

The scope will be limited to:
- Support for private docker registry
- New UD/IDE Navigation Experience

We discussed and emphased all sort of silky smooth transition that we must think about for this release.

Shipping date for 4.4 would be the Thursday 30th June. It has been agreed that we will start release process by June, 24th - which means that we will be feature complete by this date. 

We might enable JGit implementation. We will have the mandatory scope merged and once this scope will be completed, we will enable and validate on separate branch JGit implementation. If QA give the GO, it might be taken as part of 4.4.


**4. Scope for 4.5**

Scope for 4.5 has been discussed.

- URL Schema - would be done into a separate branch - tested, validated and only if QA give the go, it'll be merged.

Focus would be given to the following items: 
- Ability to add / remove / update stacks + templates from within UD
- Ability for user to change RAM for workspace within UD
- Usability cleanup of the tables in UD 
- (maybe) simple UI improvements to the IDE to soften some of the colors and reduce the black lines

We'll continue to include any critical or blocker bugs that can be resolved in a short order.

Setting a release date:


**5. Discuss management of public issues**

Florent has some progress and will share that during the week. He'll create a separate and dedicated meeting with R&D.
