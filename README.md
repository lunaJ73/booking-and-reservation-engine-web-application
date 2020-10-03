# booking-and-reservation-engine-web-application

### What is it
The project is a web application that facilitates hotel reservation management.

#### Aim
The use of the system to fully manage hotel information for users to save time and manpower, more comprehensive and effective grasp of the basic situation of the hotel, timely access to the latest accurate data and information. The software can systematically manage hotel information, functions and implementation of the pertinence and practicality of considerable. 

#### Main function
The system's main functions are hotel information management, room type management, order information management, business staff editing and system user management.

### 1. Analyze Requirements
#### The client
My client is a global provider that aims to generate efficient and innovative booking solutions. As the size of the application grew and the number of users increased, different teams were required to constantly modify the code, maintaining the modular structure became difficult and the cost of code modification and maintenance slowly increased. 

#### System user analysis  
The new system is primarily an application developed for hotel reservation work. There are usually three types of users: system administrators, hotel reservation administrators and hotel customers, who have the following access rights.  
- System administrator: Maintain the system and database, mainly giving different permissions to different personnel. 
- Hotel reservation administrator: the update of hotel information and the specific operation of reservation business management. 
- Booking customers: general operation level, able to query personal information and booking information in this system.

#### Our goal
Our team was responsible for migrating the booking and reservation engine web application to microservices, dividing the existing functionality into different microservices modules to facilitate subsequent independent development, monitoring and extension to improve the efficiency of booking transactions.

#### Features
   -  Benefits
      - WebView doesn't change depending on version
      - Capabilities: such as Booking, Register/Login, Promo Code, Check-in Service
      - Performance improvements (compared to older system webviews)
   - Drawbacks
     - No more new features added.

### 2. Idea & Design 
The old system is based on Spring Boot 2.0 and Spring Data. The whole idea is to reorganization of the system structure while retaining the original functionality.

#### 2.1 User segment functions. 
(1) Client registration. 
- User Registration: Check the information provided by the user and register the user. 
- User Login: verify the identity of the logged in user by username and password. 
- User information record: personal registration information and long-term housing information. 

(2) Hotel Reservation: 
- Querying room information: Listing the query results according to the conditions proposed by the user.
- Room reservation: to reserve a room at a certain time.
- Additional features: when entering the order payment page, the customer can enter a discount code to enjoy the benefits of holiday offers and other activities.

(3) Order Management.
- Query Reservation Information: Query this user's reservation information.
- Modify reservation information: Modify reservation information, room information, etc.
- Cancellation of a reservation: Cancellation of a valid reservation that is due and unpaid.

(4) Other management.
- Hotel scoring: free discussion group message
- Logging out of users: Ending user sessions and ensuring security

#### 2.2 Hotel Reservation Administrator.
(1) Order management.
- Check order information and print orders
- Delete unwanted or incorrect reservation information
- Room reservation statistics and user statistics
- Confirmation of a paid user's reservation: When a user makes a payment, the reservation is designated and marked.

(2) Hotel room information management
- Adding rooms: Adding new rooms
- Delete the room: if the room does not exist, delete the entry
- Modify room information: Modify and update the information of an existing room.

(3) Customer relationship management
- Retrieval of customer personal information
- Analysis of customer information

(4) Coupon Code Management
- Enter the coupon code to match the activity and adjust the order price to match the conditions.

(5) Evaluation Management
- Browse user messages: Call the message and display it, and reply to it.
- Deleting useless messages: delete messages that need to be dealt with

#### 2.3 System Functional Requirements
(1) Reservation functional requirements: its main purpose is to improve the hotel's room availability, reserve rooms for guests, and provide good reservation service. Its functional requirements include reservation inquiry, room availability confirmation, reservation record creation, reservation confirmation, discount code use, reservation record maintenance and so on.

(2) Reception functional requirements: its main purpose is to open rooms for guests in the fastest possible time. Its functional requirements include guest registration, confirmation of available rooms, modification of guest information, deletion of guest information, and querying guest information.

(3) Checkout Function Requirements: the function requirements include guest checkout, report printing and guest bill posting.

(4) Room change functional requirements: Its main purpose is to meet the needs of guests to change rooms. The main function is to check the rooms, register the rooms, confirm the rooms and so on.

(5) Room management functional requirements.
The main purpose is to improve the accuracy and precision of room management and reduce the workload of the staff in the hotel room center, thus improving the efficiency of room management and service quality. Its main functions are room state maintenance, expense record and guest inquiry. 

In summary, we divide the system's functions into three modules.
- Permissions management: including user and administrator registration, login, permission modification and so on.
- Front desk management: including customer information inputting, customer booking, check-in registration and payment management, etc.
- Backstage management: room information management, user information management, etc.


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
### Demo to Client & Get Feedback
