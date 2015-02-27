---
---
You are developing a server-side enterprise application.
It must support a variety of different clients including desktop browsers, mobile browsers and native mobile applications.
The application might also expose an API for 3rd parties to consume.
It might also integrate with other applications via either web services or a message broker.
The application handles requests (HTTP requests and messages) by executing business logic; accessing a database; exchanging messages with other systems; and returning a HTML/JSON/XML response.

The application has either a layered or [hexagonal](http://alistair.cockburn.us/Hexagonal+architecture) architecture and consists of different types of components:

* Presentation components - responsible for handling HTTP requests and responding with either HTML or JSON/XML (for web services APIS)
* Business logic - the application's business logic
* Database access logic - data access objects responsible for access the database
* Application integration logic - messaging layer, e.g. based on Spring integration.

There are logical components corresponding to different functional areas of the application.
