**Performance** - The Fish Watch application landing page supporting large set of users per hour must provide 6 seconds or less response time in a browser, including rendering text and images, over an network connection. 
For the remote WebApp
- 500 simultaneous users
- 10000 users
- 6 second response time for page data load and render
- Search results should be displayed within 10 seconds
- Dashboard response time within 10 seconds
- Historical dashboard time within 15 seconds
- Peiodic auto refresh - 15 seconds

**Scalability**
The Fish Watch system should be capable of scaling data processing and storage capabilities as the company grows, potentially handling a tenfold increase in transaction volumes over five years. Minimum 35% increase year on year. This includesbut is not limited to  following components
- IOT devices
- Data Lake
- Analytics infrastrucrure
- Web App
- Services

**Internationalization and Localization** - Fish Watch application is accessible globally for different customers so here major focus on countries, time-zones, currencies and language will be catered as temperature can be measured as per respective country standard accordingly and the fish species info which will be provided as per language selection into more understandable and readable mode.
- Support English as the default language
- Additionally support German, French, Spanish, Portugese, Japanese and Chinese
- Unit conversion between different systems, e.g. SI, metrics
- Colour scheme should be customizable based on the fish farm company brand colours

**Portability** - The Fish Watch app should be operable and maintain a consistent user experience across various mobile devices, including different screen sizes and resolutions.
The web application should work on the following browsers
- Chrome (versions...)
- Edge (versions...)
- Opera (versions...)
- Safari (versions...)
- Firefox (versions...)

**Reliability** - The Fish Watch system must perform without failure in 98 percent of use cases during a month. OR a uptime of 98%
All real time data which includes captured images etc should be processed with 80% accuracy. Where the probability level is low, the system must indicate the low confidence in data quality
The system should be able to handle and recover from errors gracefully without processing invalid data.
The system should be able to handle malfunctioning sensors and videos gracefully

**Maintainability** - The mean time to restore the system (MTTRS) following a system failure must not be greater than 30 minutes. MTTRS includes all corrective maintenance time and delay time.
The rendering image service which captures and provide more useful data should automatically adjust the quality based on the user's internet speed to avoid image data breakdown and other useful information to get the desired results for the user.

**Security** - The Fish Watch appliaction should follow specific standards and encryption methods since most of the data will be pulled from external sources so here after authenticating and authorizing the user then successfully access of application provided as required.
Here will identify how well a system protects against unauthorized access and data breaches.
- Applicability of data protection standards is low. GDPR or similar standards, as required locally should be applied for operator information, e.g. mail ids, etc if any
- Outdated TLS versions and other protocols should not be supported 
- Networks should be firewalled, including the farm controls (devices) network
