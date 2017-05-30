# Chapter 3 - Embracing Risk

## Availability
Measure by request success. Time up or down is ok to have too.

Availability = Successful requests / total requests
Works well for non user facing systems too. THings like batch, pipeline or storage systems
Not all requests are equal

## Target level of availability
PLanned downtime vs unplanned downtime
Planned is still very bad
What do users expect? 

Need an accurate internal number

Provide different external and internal targets. Make internal higher
Google Apps for Work = 99.9% external, internal is higher
YouTube = lower

What is worse, low level of failures or one big outage

It's all about cost
AdWards has to be extremely fast. As fast as Google search
AsSense has to be only as fast as the page it is rendering on. Much cheaper.

### Background errors
Your availability can't be better than the level of background errors
ISP, DNS
Google found rates between .01% and 1%

## Risk tolerance of infrastructure services
Some clients want fast, reliable storage.
Others want cheap, durable storage.
The goals of one are opposite to the other. Expose the costs so services can pass them on to users

## Motivation for errors budgets
Software fault tolerance
Testing
Push frequency
Canary size and duration
"Hope is not a strategy"

## Forming an error budget
Quarterly
Service Level Objective = SLO
Product Management chosses the number - that way there are no politics
Using an error budget should lead to the product development team becoming self policing
SRE team needs authority to slow or stop releases when the SLO is broken