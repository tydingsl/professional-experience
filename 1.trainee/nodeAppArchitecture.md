# The Architecture of Our node.js Applications

The systems that we currently operate and are developing share a similar application architecture.

Each system runs as a node.js application. As you have learned, node is a Web application server that supports JavaScript on the server.

Node is very low level, allowing software to listen on specified network ports. Like many organizations, we use an application framework to put a higher level of abstraction on top of node.js. Our choice for this is express.js. It gives us the ability to write code that listens for particular HTTP requests. These requests have two parts: an HTTP method (like GET or POST) and a target URL. We write the code to control what happens when a particular HTTP request comes in from a Web client (usually a browser).

Each application is logically divided into "services". A service is roughly an analog to an "object" in object-oriented terms. For example, the NLC attendance app has three main services: staff, student, and visit. These are the central concepts that the app is dealing with 

The code for a typical service is separated into four pieces. The first three are the service's model, view, and controller, following the well-known [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) design pattern. The fourth is the test code for the service; this is subdivided into tests for the model, view, and controller.

A service's model is similar to the intro programming concept of objects that model things in the world as software. Since JavaScript is an object-oriented language, each model is a class, where each object of that class represents a real-world object. Sometimes the real-world objects are abstract, like a "visit" to the NLC. The model class defines all the data that a visit "knows" about itself (date, purpose, etc.), and all of the behavior (methods or functions) that it is responsible for. This includes knowledge of how the data is stored and retrieved. Currently, our applications use MySQL, the open-source relational database, to store and retrieve data, but only model classes connect to the database and interact with it.

A service can have many views. Think of a view as a particular user interface. In a Web setting, this means HTML pages, often containing forms for user input. Like many organizations, we use a "templating" tool to make HTML more dynamically "programmable" on the server-side. Our choice for this is EJS. It is short for Embedded JavaScript, and avoids introducing another language for templating like Handlebars, etc. It is important to understand that the embedded JavaScript is different from the "normal" client-side JavaScript that you learned about at w3schools.com. Normal client-side JavaScript is sent to the client (browser) as part of the HTML page, and the client runs that code. (It runs in the browser on the user's computer.) EJS is server-side code, which means that the code runs on our node Web server. The output from the code is inserted into the HTML that is sent to the client, but the EJS source code is not sent to the client. (This is a good spot to remind you that security and data integrity logic **must** be implemented with server-side code. It is easy for a user to disable or work around client-side code.)

Finally, a service has one controller. This is where our apps make use of express.js to handle incoming HTTP requests and determine the correct response. For most incoming requests, the controller will call some of the model's public functions in order to get JavaScript objects with the appropriate data. The controller will then pass necessary data to the appropriate view, which generates the response and its HTML content. 

## The template/example application

[The template repo](https://github.com/dewv/webapp-template) contains a simple "do nothing" application built on this architecture. It implements one service that is given the generic placeholder name "item". 

One purpose of the repo is to act as a template or starting point for new applications. Rather than start from scratch, we would typically create a new copy of the repo, copy the generic "item" service's code for each service that is needed, and modify and expand the code for the needs of our new app.

This implies that the template contains our current "best practices" for app design. From time to time the template will be improved, and those improvements must be manually incorporated into already existing apps as needed. (There is an opportunity for improvement here with a higher level of packaging components, but that is for the future.)

The other purpose of the repo is training and learning. Without worrying about specific application details (Do we store the student's minor?), you can concentrate on how the code is organized to handle requestions, manipulate data, and generate responses.

To complete your training and earn your promotion to IS Specialist, you and your teammates must apply your training to implement a new feature in the template app. Management will provide you with specific details.
