# Record architecture decisions

Date: 2024-04-03

## Title

System design

## Status

Superceded

## Context

We created a totaly cloud based system design with focussing scability of Visual Monitoring service while other services had scope of little less availabity as per assumption where those data are not changing as frequently as images being captured at the faclities.

## Decision

We decided to go for an event driven microservice architecture.

## Consequences

**Positive:** The different services can be scaled differently and we can upgrade one service without affecting others

**Negative:** The ability of service interacting with each other is limited by various IOT been able to send feed to us in regular time.

**Risks:** Loss of network connectivity from farms to our cloud could mean users not able to reach to our websites and important notifications been missed out.

**Tradeoffs:** If any
