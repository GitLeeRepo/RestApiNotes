# Overview

Notes on the REST API (often referred to as RESTful APIs)

# Reference

## YouTube Videos

* [REST APIs Explained](https://www.youtube.com/watch?v=Q-BpqyOT3a8) - YouTube video by Traversy Media.  Several of the notes taken from this video
* [REST API concepts and examples](https://www.youtube.com/watch?v=7YcW25PHnAA) - YouTube video
* [Intro to REST](https://www.youtube.com/watch?v=llpr5924N7E) - YouTube video
* [CURL tutorial](https://www.youtube.com/watch?v=7XUibDYw4mc) - YouTube video

## My Other Notes

* [curlNotes](https://github.com/GitLeeRepo/RestApiNotes/blob/master/curlNotes.md#overview)
* [AjaxNotes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/AjaxNotes.md#overview)
* [JavaScriptNotes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/JavaScriptNotes.md#overview)
* [Angular4Notes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/Angular4Notes.md#overview)
* [JsonNotes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/JsonNotes.md#overview)
* [NodejNotes](https://github.com/GitLeeRepo/NodejsNotes/blob/master/NodejNotes.md#overview)
* [PHPNotes](https://github.com/GitLeeRepo/PHPNotes/blob/master/PHPNotes.md#overview)
* [PythonNotes](https://github.com/GitLeeRepo/PythonNotes/blob/master/PythonNotes.md#overview)

# What is REST?

* REST stands for **Representations State Transfer**
* Client Server architecture with caching which improves scalability and performance
* Uses a structured request and a structured response
* Resource based (REST) rather than action based services (SOAP API)
* Resources identified by URIs
* Can have multiple services per URI as long as they are different types (GET, POST, PUT, DELETE)
* Treats server objects as resources that can be created, modified, and removed
* Representation separate from the Resource.  The URI is not necessarily the physical directory location of the resource.
* Also representative  in the sense that you are typically getting a representative 
* Representations are typically in a JSON or XML format
* Uniform interface
  * HTTP Request: GET, POST, PUT, DELETE  
  * URIs for selection  
  * HTTP Response
* Stateless - Each message is self-descriptive.  Server has no client state (the client can manage its own state)
* Code on Demand - capable of transferring app logic to the client, through JavaScript for example

# Request verbs

* GET - retrieve data
* POST - add data to server
* PUT - update data on the server (not available through HTML forms, need AJAX or other methods)
* DELETE - delete data on the server (also not available through standard HTML, use AJAX, etc)
* POST vs PUT - POST should be used for adding new entries, while PUT should be used for updating exiting entities

# Example End Points

```
GET    https://api.example.com/users - for all users or a limited number of users
GET    https://api.example.com/user/1 - return the specific user by identifier (1 in this case)

POST   https://api.example.com/users - to add new user to the server
POST   https://api.example.com/uers/add - another typical URI structure for adding entities

PUT    https://api.example.com/users/1 - to update user with id 1 on the server
PUT    https://api.example.com/user/update/1 - another typical URI structure for updating entities

DELETE https://api.example.com/users/1 - delete user with id 1 on the server
DELETE https://api.example.com/users/delete/1 - another typical URI structure for deleting entities
```
Note another typical way is to use an API directory `https://example.com/api/users` instead of the using the API domain.

Note that several of the above examples use the same URI, which is ok as long as they are different methods (GET, POST, PUT, DELETE)

# Authentication

Sometimes authentication is required

## Examples

* Set an OATH_TOKEN in the header

	```
	curl -H "Authorization: token OATH_TOKEN" https://api.github.com
	```

* Set an OATH_TOKEN in the URI

	```
	curl https://api.github.com/?access_token=OATH_TOKEN
	```

* Use client id and secret

	```
	curl 'https://api.github.com/user/username?client_id=xxxx&client_secret=xxx'
	```
