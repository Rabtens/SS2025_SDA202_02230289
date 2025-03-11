# Architecture Characteristic Worksheet
![alt text](Architecture_worksheet.png)

## 1. Responsiveness  
*(The amount of time it takes to deliver a response to the user.)*  

Reason  
With reference to the requirement stating that the system must provide the "richest user interface possible across all deployment platforms", responsiveness ensures users can interact with the system seamlessly (e.g., loading trips, sharing to social media). Server-side processing of 10,000+ concurrent requests would degrade latency, especially for global users.  

Use Case  
- Scenario: A user searches for nearby hotels or car rentals during busy travel times.  
- Problem: The server can’t handle all the location requests quickly, causing slow results.  
- Solution: The app uses the phone’s GPS to find the user’s location and sends it directly to hotel/car rental services.  
- Outcome: Results appear in under 1 second, avoiding delays from the overloaded server.  

Tradeoff & Mitigation  
- Tradeoff: Client-side processing increases mobile app complexity.  
- Mitigation: Use cross-platform frameworks (e.g., React Native) to maintain code simplicity.  


## 2. Interoperability  
*(The ability of the system to integrate and exchange data with heterogeneous third-party services.)*  

Reason  
With reference to the requirement stating that the system must interface with the agency’s existing airline, hotel, and car rental interface systems and support "favored vendor" partnerships, the system must seamlessly integrate diverse APIs. This means the system normalizes data formats (e.g., SOAP/XML for legacy airline systems, REST/JSON for hotels) to ensure consistency. Users expect reservations—automatically loaded via frequent flier accounts, hotel memberships, or car rental rewards programs—to appear in a unified dashboard without fragmentation.  

Use Case  
- Scenario: A user connects their airline rewards account (older system) and hotel rewards account (newer system) to see all bookings in one trip.  
- Problem: The system can’t combine old airline data with modern hotel data, causing errors like wrong dates or missing bookings.  
- Solution: A tool (API gateway) converts the different data formats into one standard format (like JSON).  
- Outcome: The user sees their flights, hotels, and rentals neatly organized in one trip view, with no errors or manual fixes needed.  

Tradeoff & Mitigation  
- Tradeoff: Supporting old and new systems (like SOAP and REST) makes the system harder to build and maintain.  
- Mitigation: Use a tool like AWS API Gateway to manage differences between systems and make everything use the same format (e.g., JSON).