## Che Roadmap Meeting
### 7-Aug-2017

### Attendees
* Brad Micklea
* Anatolii Bazko
* Anna Shumilova
* Florent Benoit
* Ranjith Varakantam
* Roman Iuvshyn
* Sergii Kabashniuk
* Tyler Jewell
* Gennady Azarenkov  (moderator)
* Gorkem Ercan
* Stevan Le Meur

### Topics 
* Face to face agenda: are you ok with current agenda? Is there something you think you should talk about that is not in the agenda yet?
* Next Codenvy.io = Che?+Keycloak+Permissions+Docker Swarm

### Notes
### F2F 
RV: F2F Agenda will be reviewed

### Next Codenvy.io
* SK: Let’s discuss what version for CIO 5 vs 6 and what infrastructure OS vs Swarm
* BM: why Swarm?
* SK: not all the stacks/components/workspaces from CIO can be reused for the time
* GE: It’s mostly because of security limitation, dedicated OS will help, including removing limitations for installers (a k a “sudo problem”)
* TJ: Does it make sense to have 2 systems in parallel (OS and Swarm)? 
* GE: But so far we do not have dedicated OS and it is difficult to estimate
* TJ: Lets be focused on customers needs which is on-prem based on OS, including  Run Book. We need to know  of how long time to support CIO by RH.
* GE: AFAIK we can talk about a budget for about 1 year
* SK: It could be really easy to support CIO with Swarm, for OS is unpredictable, can not estimate it right now.
* RI: We might not be able to support OS infra well too since we are not experts
* TJ: Let’s be focused on business needs
* GA: We consider CIO on Swarm as a preliminary step, just to test Keycloack, assembly. Main goal is OS 
* TJ: OK with 2 steps tactic - Swarm then OS 
* BM: Business needs onprem on OS, we need to have estimation ASAP
* GE: let’s go to the next Sprint and estimate, Roman contact KB. Minishift is OK for start then we need to realize difference, to do the trials.
 
### Actions
* Dedicated meeting about f2f schedule - Ranjith
* CIO on Swarm as a preliminary step to test assembly with Keycloack - Sergey
* Estimation after this Sprint - Mario and Sergey
* OSIO assembly on Minishift for dev stage, then try on OS, contact KB for help - Roman



