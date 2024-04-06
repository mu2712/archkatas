# Solution overview

## Principles

1. We should be able to scale indiviual components separately.
2. Extensibility and modifiability preferred in case of trade-offs  
3. Minimize loss of feeds coming from IOT devices.
4. Cache data coming from extremal system like weather data and the ideal data based on fish species, this will enable us to make less api calls to external system and these data are assumed to change very infrequently.

## Overall Solution Summary
**Problems**

We have Farms and Enclousres situated at far-flung areas with below assumped obstacles:
  - Frequent network outages which can last multiple days.
  - Connecting from these farm sites to a remote datacenter can be affected in wake of these freqent network outages.
  - The images captured are to be recognized properly by AI models.
  - Data from images and other external system devices like Water Monitor IOT,  Weather Data have to be made available to a common point      to allow us to run rules defined by System Admins.
  - As the customers span multiple geographies, we have to take into consideration of various locales that comes into play, things such 
    as units of measurement like temperature etc.
  - A lot of system rules are to be governed by the system admins to let them choose what actions that want on what conditions.

**Solution**

 After taking into consideration all the above points, we are planning to create a system comprising of on premises and cloud components.
   - We will put a set of prem systems capable of capturing data from various IOT devices and External Systems (weather data).
   - The data will be sent to Cloud based system capable of running analytic on the data collected to give proper guidance to users about 
     best times to harvest.
   - The data stored at cloud based system will be replicated to on-prem set up (as and when these systems could connect, also          
     considering the defined time set).
   - We assume the fish-ual recognition system is already in place, so we will use the confidence the AI model has in recognitions and          store them along with an image thumbnail (to allows users to manually look at the images if they want)
   - We can plan for customizing the AI recognition model ourselves as we gather more imformation and as our system matures. (Future 
     Consideration)
   - We will archive older data and possibly delete much older data (The number of days will be set by Admin users). This will let us          save a lot of cost associated with managing a large data set (of images etc).
     
   **Alerting and Monitoring**
   
   We would have our notication / alert service always up to allows us to send important notifications all the time. We would have 
   multiple alerts such as:    
   - "Approaching adverse situation" (possible due to multiple parasite located, the threshold defined by Admins).
   - Not receiving feeds from last <user defined> duration.
   - Any adverse weather forecast received.
   Besides this, we would have a lot of system admin monitoring in place and various analytics running on them to give proper feedback to    site admins about health of various services.

  

## Style

Based on provided principles, and current [businesss goals](https://github.com/mu2712/archkatas/blob/development/Requirements/Functional.md) (number of users, functionality current and desired) and constraints the primary implementation style of architecture is **event-driven microservices**.

The high level design is as follow:

![image](https://github.com/mu2712/archkatas/assets/57832454/0cc2fa8b-718d-4f32-b9da-0ed9c69fe886)

## Description
1.) **Farm Details Service**: This service will be responsible for the maintenance of all the data related to farms and it's enclosures. It will be using a RDBMS DB(SQL Lite). Since the data volumes is less, we do not need mucch scalability here.

2.) **Water Monitoring Service**: This service gets feed from the water monitoring IOT placed in the facality. Since this data does not change very frequently (assumption), this data will be cached to allow for the services dependent on data from water monitoring services to retrive data faster from a cache instead of hitting this service. Also, as such this service does not need super avalability.
The refresh of cache will be dependent on the timer set at Configuration Service.

3.) **Weather Service**: Weather service will get feeds form a external weather service. This data will be cached just like water monitoring service using timers set at configuration service. However, if this service finds any data that falls within the danger zone or start approaching the danger zone (The threshold for danger zone will  be defined in the Configuration Service), it will directly call the alert service to send out necessary alerts to users.

4.) **A Mongo DB storing ideal data for each fish species**: This will gets it's data from an external service of directly from the configuration set by Admins to determine the ideal data for each fish species. Like Water monitoring service it's data will be cacahed.

5.) **Visual Monitoring Service**: This service will get description of images capture in form of a meta data that contains the recognized object. the object's image coordinates and the amount of confidence in the recognition of the object. This will also store a thumbnail of the images. This will use a Mongo DB to effective store images thumbnails and the json  metadata.

6.) **Rule Engine**: Data form all the above services is feed into the rule engine, which take all these different data and evaluate various conditions defined in the configuration service. If the evaluation comes under a condition where notifications needs to be sent out, the Rule Engine will call the Alerts Service. (The conditions will again be defined in the configuration service)

7.) **Alerts Service**: This will be responsible for sending out alerts to users. It will direct alerts to a message queue where notifications are saved until those gets sent out to users

8.) **Configuration Service**: This service is Admin User defined data, that determine various things such as:
   - The frequency of collecting feeds from water monitoring IOT.
   - The frequency of collecting feeds form external weather service
   - The duration of various data that needs to made available, the timing for archival and deleteion (we will move data to cold 
       storage and later delete)
   - The cache refresh times

## Network Design Architecture

   The architecture enables extending the on-premise data center to connect seamlessly with Azure services ensuring data security and availability , The IOT devices installed at the sites will use MQTT to send data to local 
   on premise data center with is integrated with Azure cloud using VPN gateway to ensure data security and realibility .

   ![image](https://github.com/mu2712/archkatas/assets/69727351/3146b48b-1730-4d68-8d2f-e613c80d22f3)

## Analytics Architecture
The analytics architecture considers multiple data sources, including streaming IoT devices, Camaera feed and external data sets.
![image](https://github.com/mu2712/archkatas/assets/16031924/0544c397-9864-4ce3-a81e-bc37446712ed)

