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

## Description
1.) **Farm Details Service**: This service will be responsible for the maintenance of all the data related to farms and it's enclosures. It will be using a RDBMS DB(SQL Lite). Since the data volumes is less, we do not need mucch scalability here.

2.) **Water Monitoring Service**: This service gets feed from the water monitoring IOT placed in the facality. Since this data does not change very frequently (assumption), this data will be cached to allow for the services dependent on data from water monitoring services to retrive data faster from a cache instead of hitting this service. Also, as such this service does not need super avalability.
The refresh of cache will be dependent on the timer set at Configuration Service.

3.) **Weather Service**: Weather service will get feeds form a external weather service. This data will be cached just like water monitoring service using timers set at configuration service. However, if this service finds any data that falls within the danger zone or start approaching the danger zone (The threshold for danger zone will  be defined in the Configuration Service), it will directly call the alert service to send out necessary alerts to users.

4.) **A Mongo DB storing ideal data for each fish species**: This will gets it's data from an external service of directly from the configuration set by Admins to determine the ideal data for each fish species. Like Water monitoring service it's data will be cacahed.

5.) **Visual Monitoring Service**: This service will get description of images capture in form of a meta data that contains the recognized object. the object's image coordinates and the amount of confidence in the recognition of the object. This will also store a thumbnail of the images. This will use a Mongo DB to effective store images thumbnails and the json  metadata.

6.) **Rule Engine**: Data form all the above services is feed into the rule engine, which take all these different data and evaluate various conditions defined in the configuration service. If the evaluation comes under a condition where notifications needs to be sent out, the Rule Engine will call the Alerts Service. (The conditions will again be defined in the configuration service)

7.) **Alerts Service**: This will be responsible for sending out alerts to users. It will direct alerts to a message queue where notifications are saved until those gets sent out to users

8.) Configuration Service: This service is Admin User defined data, that determine various things such as:
   - The frequency of collecting feeds from water monitoring IOT.
   - The frequency of collecting feeds form external weather service
   - The duration of various data that needs to made available, the timing for archival and deleteion (we will move data to cold 
       storage and later delete)
   - The cache refresh times

## Network Design Architecture

   The architecture enables extending the on-premise data center to connect seamlessly with Azure services ensuring data security and availability , The IOT devices installed at the sites will use MQTT to send data to local 
   on premise data center with is integrated with Azure cloud using VPN gateway to ensure data security and realibility .

   ![image](https://github.com/mu2712/archkatas/assets/69727351/3146b48b-1730-4d68-8d2f-e613c80d22f3)


