# booking-and-reservation-engine-web-application

### What is it
The project is a web application that facilitates hotel reservation management.

### Demand analysis
My client is a global provider that aims to generate efficient and innovative booking solutions. As the size of the application grew and the number of users increased, different teams were required to constantly modify the code, maintaining the modular structure became difficult and the cost of code modification and maintenance slowly increased. Our team was responsible for migrating the booking and reservation engine web application to microservices, dividing the existing functionality into different microservices modules to facilitate subsequent independent development, monitoring and extension to improve the efficiency of booking transactions.

### Map Main Points to Solutions & Get Feedback

#### Benefits

* WebView doesn't change depending on Android version
* Capabilities: such as WebRTC, WebAudio, Web Components
* Performance improvements (compared to older system webviews)


#### Drawbacks

* Increased memory footprint
  * An overhead of ~30MB (as reported by the RSS column of ps)
* Increased APK size (about 17MB)
* Increased size on disk when installed (about 50MB)
* Crosswalk WebView stores data (IndexedDB, LocalStorage, etc) separately from System WebView
  * You'll need to manually migrate local data when switching between the two (note: this is fixed in Crosswalk 15)


### Prototype your Solution & Test
#### 3.1 Analyze Requirements
#### 3.2 Design
#### 3.3 Coding / Implementation
#### 3.4 Unit Testing
#### 3.5 Integration Testing
### Create a Minimum Viable Product
### Demo to Client & Get Feedback
### Design a Roadmap




### Install

The following directions are for cordova-cli (most people).  Alternatively you can use the [Android platform scripts workflow](PlatformScriptsWorkflow.md).

* Open an existing cordova project, with cordova-android 4.0.0+, and using the latest CLI. Crosswalk variables can be configured as an option when installing the plugin
* Add this plugin
