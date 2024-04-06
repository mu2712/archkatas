1. Introduction
The application "Fishy Watch" is built for Livestock Insights incorporated which is a company having headquater in Scotland, but operating globally.

    1.1 Purpose
        The main purpose of "Fish watch" application is to provide fish farm operators with real-time information about health of the fish,  fish species,              and environmental conditions to promote sustainable fish farming. It is able to collect              information about individual fish, water quality, and weather
        information. Fish farmers can use this information to understand the health of their livestock, check
        for signs of parasites and disease, and work out the best time to harvest. 

   1.2 Scope
        The application will offer detailed species and farm information via dashboard. The dashboard data will be gathered          from various service like location-based services, Alerting services, Visuals monitoring services,Image Recognition          Service, Farm detail service, Weather Monitoring service and Water monitoring service.

2. Overall Description
   
    2.1 User Needs are defined below:-
   
        a)Farmers needs to be able to see the collected information in customizable dashboard.

        b)Farmers needs threshold values at which alerts can be triggered. This includes water PH level going out of bounds and advance warning of adverse weather events which are expected. Most of these data are configured by Admin Users at this point.

        c)Farmers should be able to predict good harvest conditions by using a model created with the help of track information about the fish harvested from each farm alongwith the raw data collected.

        d)Each farm may have a variety of different fish species.

        e)For large customers, they will want to be able to drive insights across a number of farms.

        f)Alert should be generated for degradation in water quality or adverse weather event.

        g)Fish Watch needs to be accessible from a number of devices, including rugged industrial devices used on the sea   during harvest.

        h)Fish farms are often in remote locations, where cellular signal may be poor.

        i)Flexibility of adding similar capabilities to cattle, and also allowing aquariums to use the system to look after fish health.

3. System Features and Requirements
   
    3.1 Species Identification

        Functionality: Users can capture or upload images of fish to identify species using image recognition.
        User Interface: Camera integration; upload from gallery option.

    3.2 Regulations and Compliance  (Future consideration)

        Functionality: Provides legal information related to fishing activities like size limits, season dates, and bag limits.
        Data Management: Regular updates from authoritative sources.
   
    3.3 Location Services  (Future consideration)

        Functionality: Map integration showing fishing spots, restricted areas, and user location.
        User Interaction: Searchable map with filter options for types of fish, facilities, and accessibility.

    3.4 Environmental Conditions

        Functionality: Real-time data on weather, water temperature, and tide schedules.

        Integration: APIs from weather services.

    3.5 Notifications and Alerts

        Functionality: Customizable notifications for changes in environmental conditions, water PH levels and species health. 
        Settings: Users can set preferences for frequency and types of alerts.

  5. Data Management
     
    4.1 Data Sources
        Official government databases for regulations (Future consideration)
        Partnered databases for species information  (Future consideration, currently we will rely on info by fish farmers)
        Tide data files from vendors
    4.2 Data Update and Synchronization
        Regular updates to ensure accuracy of information.
