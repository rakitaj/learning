# Chapter 4 - Service Level Objectives
Service level
SLI - indicator
SLO - objective
SLA - agreement

## Service Level Indicator
SLI - quantitative measure

Example SLIs
* latency
* error rate
* throughput - measured as number of requests a second
* availability - measured as well formed requests
* for storage systems - durability

## Service Level Objective
SLO - target value or range of values for SLI
We can't always choose! Ror example HTTP requests our queries per second are determined by the users
On that example we CAN set latency per request as a SLO

Read about the global chubby outage!!

## Indicators
Be careful about aggregating indicators, that can hide spikes from 0 to 200 and show an average of 100.
**Always use percentiles if you can** this will expose the "long tail" of problems.
Knowing this your team can choose to focus on all values or even only the 99.9% ones because if that
works well then almost everyone will have a goood experience.

**They say** user studies show people prefer a slower system on average vs one that has a lot of variance

## Standardize indicators
People need a common vocabulary
Standard aggregation intervals *eg* 1 minute
Standard aggregation regions *eg* per cluster
Data access latency - time to last byte

## Choosing SLOs
Not a purely technical activity
Need to be clear

Defend the SLOs you pick: if you can't even win w conversation about priorities by quoting a particular SLO it's probably 
not worth having that SLO.