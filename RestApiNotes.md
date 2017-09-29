# Overview

Notes on the REST API (often refered to as RESTful APIs)

# Reference

* [REST APIs Explained](https://www.youtube.com/watch?v=Q-BpqyOT3a8) - YouTube video

* [REST API concepts and examples](https://www.youtube.com/watch?v=7YcW25PHnAA) - YouTube video

* [Intro to REST](https://www.youtube.com/watch?v=llpr5924N7E) - YouTube video

* [CURL tutorial](https://www.youtube.com/watch?v=7XUibDYw4mc) - YouTube video

# What is REST?

* REST stands for **Representations State Transfer**

* Client Server architecture with caching which improves scalability and performance

* Resource based (REST) rather than action based services (SOAP API)

* Resources identified by URIs

* Can have multiple services per URI as long as they are different types (GET, POST, PUT, DELETE)

* Representation separate from the Resource.  The URI is not necessarily the physical directory location of the resource.

* Also representative  in the sense that you are typically getting a representative 

* Representations are typically in a JSON or XML format

* Uniform interface

  * HTTP Request: GET, POST, PUT, DELETE
  
  * URIs for selection
  
  * HTTP Response

* Stateless - Each message is self-descriptive.  Server has no client state (the client can manage its own state)


