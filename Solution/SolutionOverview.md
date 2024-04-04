# Solution overview

## Principles

1. We should be able to scale indiviual components separately.
2. Extensibility and modifiability preferred in case of trade-offs  
3. Minimize loss of feeds coming from IOT devices.
4. Cache data coming from extremal system like weather data and the ideal data based on fish species, this will enable us to make less api calls to external system and these data are assumed to change very infrequently.

## Style

Based on provided principles, and current [businesss goals](https://github.com/mu2712/archkatas/blob/development/Requirements/Functional.md) (number of users, functionality current and desired) and constraints the primary implementation style of architecture is **event-driven microservices**.

The high level design is as follow:

![image](https://github.com/mu2712/archkatas/assets/57832454/a5082b07-9294-4708-ba2a-489c821a5558)

