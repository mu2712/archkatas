# Record architecture decisions

Date: 2024-04-04

## Title

Sytem Approach

## Status

Accepted

## Context

On further discussions and giving thoughts and knowing that farms exists in far flunged areas, we tweaked our design a bit.
Also, importance to be given on various locales as we farms are located at various geographies.

## Decision

We are bifurcating the system to move some components to On-Prem and others on Cloud, to mitigate the risks of lossing critical data in events of outages.

## Consequences

**Positive:** The risk of lossing feeds is mitigated to a certain level.

**Negative:** We have a complex set-up with system present both on On-Premises and Cloud, which increases the cost.
