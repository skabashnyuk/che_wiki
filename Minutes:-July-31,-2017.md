# PARTICIPANTS

* Brad Micklea (moderator)
* Anatolii Bazko
* Anna Shumilova
* Florent Benoit
* Mario Laredo
* Oleksandr Garagatyi
* Ranjith Varakantam
* Roman Iuvshyn
* Sergii Kabashniuk
* Vitalii Parfonov
* Tyler Jewell
* Gennady Azarenkov
* Gorkem Ercan
* Eugene Ivantsov
* Martha Benitez

# TOPICS

1. Che 6: scope, implementation strategy and what happens to codenvy.io - stay on Codenvy 5 or move to Che 6?
1. New IDE panels were merged into SPI branch. Can it be merged into Che 5.x branch?
1. "OpenShift Enterprise Workspaces" - implementation strategy, assembly, team.
1. Face to face meeting - if you have agenda items to add contact @l0rd

# MEETING NOTES

### Che 6
* Sergii Kabashniuk: Concerned about removing SPI from Che 6. 
* SK: Adding keycloak and multi-tenancy may require SPI.
* Gokem Ercan: We aren’t abandoning SPI, just prioritizing multi-tenant and OS connector because it’s faster to market and we have long pole (12 weeks) around productization to get RH support for Che
* Tyler Jewell: If productization starts with Che 6.0, what happens if a new upstream version (Che 6.1, 6.2) is released during the productization cycle? Will the product release be 6.0, 6.1, or 6.2?
* GE: Product will be on 6.0. RH release team takes a fork of the repo and works with that. Bug fixes are deployed to that fork.
* Brad Micklea: will new releases take as long as initial productization?
* GE: No.
* TJ: Can we start productization with Che 5.15?
* GE: Yes, but the release can’t go out on with 5.15. They need to build everything from source, even dependencies, but some of those are probably built already as part of other products in RH. But stacks scare me - those may need to go into OBSS. If the release is going to be on Che 6 then the productization tasks and timeline are reset when upstream Che 6 version is released.
* TJ: What’s the cost of productizing an incremental release?
* GE: Once we know how to do a Che product release, future releases will be easier. But I don’t know how much paperwork is required per release (esp. Legal checks like export compliance) - technical time isn’t bad, business time is harder.
* TJ: Keycloak will change all the export compliance items. But let’s assume the bottleneck will be productization team, not tech team.
* Gennady Azarenkov: Suggest we take one person from Mario’s team to have them work with Sergii Leschenko on SK’s team to work on OS on SPI. Simultaneously Roman works with RH release team on builds.
* TJ: +1 and in 3-4 weeks we’d have enough data to give reasonable estimates on delivery of Che 6 with OS on SPI.
* AZ: Yes
* Mario Loriedo: I agree with the approach, but we will need to be aware of the SPI risk.
* SK: we have two options: (a) Che 5.x with added multi-tenancy plus OS connector and keycloak; (b) Che 6 with SPI.
* TJ: If we chose (a) how long to get a standalone release?
* SK: Can’t say - but we should push whatever version we will productize to codenvy.io to test.
* TJ: So for us to be confident with the upstream release we’d have to finish POCs on codenvy.io and OSIO
* SK: Ideally, yes
* GE: My guess is that by the end of next sprint we can do deployments to openshift.io
* TJ: Sergii is your plan to move codenvy.io to Che on OpenShift and then sunset Codenvy?
* SK: Yes - replace codenvy with MT Che on OS.
* TJ: We will need a runbook and we can only get that from codenvy.io, I agree.
* BM: +1
* TJ: Next sprint is really focused on whether downstreams (OSIO and codenvy.io) accept the assumptions made by SPI and OS connector

### New IDE Panels 
* New IDE panels can’t be moved into Che 6 without risking disruption.

### Keycloak
* 3.2.x is the right version to use
* Have to use Keycloak rather than OCP if we want the same tech for upstream and downstream
* We will use Keycloak


