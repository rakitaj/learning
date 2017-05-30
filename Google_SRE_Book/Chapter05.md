# Chapter 5 - Eliminating Toil

> If a human operator needs to touch your system during normal operation you have a bug. The definition of *normal* changes as your system grows.

## Toil Defined
Toil is not just work you do not want to do.
Also not administrative work or grungy chores.
There is overhead to running a service.

Toil **is** work tied to running a production service that tends to be
* manual
* repetative
* tactical = interrupt driven instead of strategic
* automatable
* devoid of long term value = is your service in the same state as before aka no permanent improvement
* **scales linearly as a service grows** aka **O(n)** with service growth

## Why less toil is better
Operation work ie. toil below 50% for each SRE
There is a promise to new hire SREs that this is not a typical Ops organization. They keep that promise with the 50% rule. 
It keeps an SRE team from devolving into an Ops organization.
If not held fast this 50% can easily expand to fill 100% of a team's time.

### Calculating toil
An on-call shift counts as 100% toil so that is a floor on the number. Both the primary and secondary on-call engineers are counted as 100%
Leading sources of toil according to Google SREs
1. Non urgent requests
2. On-call (urgent) response
3. Deployments and pushes

Releases and pushes have a lot of automation around them. The teams are always looking to do better
Quarterly surveys show the average toil level @ 33% with a range of 0% to 80%

## What qualifies as engineering
The work provides a permanent improvement in your service.
Is guided by a strategy

Different types
* Software engineering - writing and modifying code along with its documentation
* Systems engineering - produce a listing effort on systems with a one time effort
1. Deploying monitoring
2. Tuning OS parameters
