# booking-and-reservation-engine-web-application

### What is it
The project is a web application that facilitates hotel reservation management.

### 1. Analyze Requirements
My client is a global provider that aims to generate efficient and innovative booking solutions. As the size of the application grew and the number of users increased, different teams were required to constantly modify the code, maintaining the modular structure became difficult and the cost of code modification and maintenance slowly increased. 

Our team was responsible for migrating the booking and reservation engine web application to microservices, dividing the existing functionality into different microservices modules to facilitate subsequent independent development, monitoring and extension to improve the efficiency of booking transactions.

#### Features
   -  Benefits
      - WebView doesn't change depending on version
      - Capabilities: such as Booking, Register/Login, Promo Code, Check-in Service
      - Performance improvements (compared to older system webviews)
   - Drawbacks
     - No new features added.

### 2. Idea & Design 

### 3. Implementation
Developed with microservices architecture Hotel Booking Interface and several new REST APIs, including booking service, Register/Login security service, Promo Code Verification  and customer check-in service by using Spring cloud, Spring Security and Spring MVC.
#### Front-End
Angular 8 along with HTML5, CSS3 and Bootstrap 4 to develop static and dynamic UI web pages. 
#### Back-End
##### Spring Security 5  
JWT authentication, authorization and access-control features for customers registering and login. It enables the transfer of authenticated user identity information between identity providers and service providers to obtain resources from resource servers. 

After customer login and want to search and book a room, the controller will process the request to model, the model will interact with DynamoDB database and show the information of current chosen room.

##### Order - booking
Kafka to establish an appropriate communication protocol between the service peer and the service management system, so that when a customer makes a booking or reservation using our system, the producers will post a message with an order id onto JMS and the other part, consumer will listen to the message queue and responds to events by connecting the Kafka client, next it will give the response by taking the order id, looking up the order in the database, and then putting that order into the service management system and updating the status of this order at the same time.

##### Order - Prome code 
Start the zookeeper and Kafka server and create a new Kafka client with topics and separate partitions, the Kafka client is already configured in server properties, I write the producer to public a message onto JMS with the order id when user place a booking or reservation with promo code. In the other part of application, I write the consumer that listen to the message queue by connecting the Kafka client with consumer from the predefined Kafka topic, the it will respond to the event by taking the order id, looking the order up in the database and then place that order with service management system.

##### Version control
Used Git for version control and Eclipse STS 4.0 for development of the application.

##### Unit Testing
Tested application API implementation using Junit 5 and Spring Boot Testing Starter.
##### Integration Testing
Deployed the above application API as a Docker image on AWS EC2 for integration testing.

Kafka to establish a communication protocol between service and system and AWS SDK to connect to Amazon S3 buckets, which is provides us an end-to-end approach which secures and hardens your infrastructure. It give us with the security we need at a lower cost than in an on-premises environment. The security are provided protects the privacy as it is stored in AWS data centers of our project. The application is hosted on EC2 instances and load is balanced by a Load Balancer and Auto Scaling Groups (ASG).
### Create a Minimum Viable Product
### Demo to Client & Get Feedback
### Design a Roadmap

### Install

The following directions are for cordova-cli (most people).  Alternatively you can use the [Android platform scripts workflow](PlatformScriptsWorkflow.md).

* Open an existing cordova project, with cordova-android 4.0.0+, and using the latest CLI. Crosswalk variables can be configured as an option when installing the plugin
* Add this plugin 
