# PARTICIPANTS:

- Gorkem Erkan
- Roman Iuvshyn
- Eugene Ivantsov
- Oleksander Garagatyi
- Tyler Jewell
- Sergii Kabashniuk
- Viktor Kuznietsov
- Mario Loriedo
- Brad Micklea
- Vitalii Parfonov
- Anna Shumilova

# TOPICS DISCUSSED:

1. Che 6 Priority Shift.
2. Finalize the definition of development process.
3. Nightly testing the CHE6 (branch [SPI](https://github.com/eclipse/che/tree/spi)).
4. SSH agent strategy when running inside a container with no sudo rights.
5. Adapt docker images structure to several packagings of CHE https://github.com/eclipse/che/issues/5402.


# DETAILED MINUTE:

### Che 6 Priority Shift
- The scope of work needed to finalize productization of CHE was discussed and the main goal is to reduce the number of features, that are not connected to multi-tenant and multi-user in OpenShift.
- Introduce the work on SPI is considered to be risky, because:
  * it touches more components, has to be properly reviewed and tested
  * existing OpenShift Connector is build on older API.
- As far as workspace loading depends on SPI work - it will not be included in CHE 6.
- CHE 6 scope consists of Kubernetes integration, multi-users, permissions, multi-tenant.
- The amount of work needed for Keycloack can be tracked [here](https://github.com/eclipse/che/issues/5362).
- The dashboard amount of work consists of [workspace redesign](https://github.com/eclipse/che/issues/4359), [revising profile interaction](https://github.com/eclipse/che/issues/5788) and [moving needed codenvy stuff to che](https://github.com/eclipse/che/issues/5802)
- Git panel and command palette should be postponed.
- Gorkem will contact Roman and Eugene to start work on project productization - organizing builds, needed registries for images, defining YAML objects. Also Ansible was proposed to be considered as on option for automating the following process.

### Finalize the definition of development process
- The details on defining development process is closed out and Tyler has updated [wiki](https://github.com/eclipse/che/wiki/Development-Process).

### Nightly testing the CHE6 (branch [SPI](https://github.com/eclipse/che/tree/spi))
- Vitalii and Viktor dealt to start work on preparing selenium tests for SPI branch. Production team has the plan to do investigation and provide the estimations for the needed amount of work at the end of the current sprint.

### SSH agent strategy when running inside a container with no sudo rights
- Mario raised the problem with workspace bootstrapping in case the SSH agent is running inside a container with no sudo rights. The proposed options to solve the problem are:
  * disable ssh agents by default in stacks.json
  * try to start SSH agent, but on fail - still continue workspace bootstrapping.

The first option was considered to have more impact on the end user (those who got used to have SSH agent by default), so decided to start with the second one.

### Adapt docker images structure to several packagings of CHE
- Discussed issue is https://github.com/eclipse/che/issues/5402.
- Gorkem proposed to have 3 types of assemblies: 
  * CHE without Keycloak, multi-users, permissions, etc
  * CHE with Keycloack enabled
  * CHE with Keycloack inside but disabled
- Mario proposed to have flag for enabling/disabling Keycloack.
- Sergii proposed to provide some sort of solution, try to use it and then get feedbacks for improvements.


