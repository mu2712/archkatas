# Trade-offs

1. We have made small sacrifices to the Water monitoring Service, Weather Service and Ideal Data per species for saving cost of processing frequent feeds form IOTs and other external system. This was made by the assumption that the data from the aformentioned services uses does not change very frequently. This led us to put data from the services to a cache to be readily available for us to process. This saved us both from network outages, the ability for these servies to be able to withstand some downtime. We also gain from performance by using cache.

2. The Visual Monitoring Service has a huge data set that gets fed into  very frequently as the camera feed their data to it along with the AI model that does fish-ual recognition. We choose to make this highly available and redundant. This increases the maintenance of the service and overall cost.

3. We choose to archive and deleted image data(or just move to cold storages) based on set number of days (We let Admin Users to decide the days threhold). This will help our system to just work with less data, which means faster performance and lesser cost. This cost us from not having quickly available historic records (as we archive them and possibly delete).

4. We have decided to use Message Queues in every place where data is sent form one service to another to safeguard data againt service not up losses. This comes with a cost.

5. Setting up an On-Prem set-up is a huge trade off that ensures we work with less to no network, but comes with a considerable cost.
