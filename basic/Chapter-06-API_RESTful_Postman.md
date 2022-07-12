# Chapter 06: Restful API and Postman

Mục tiêu:<br>
_Nắm được cơ bản về API và tiêu chuẩn restful.<br>
_Nắm được cách sử dụng Postman. Kết hợp với bài trước để test bộ API bằng Postman<br>

## Restful API

###1. What is API
As per [Wikipedia's Definition of API](https://en.wikipedia.org/wiki/API): In computer programming, an application programming interface (API) is a set of subroutine definitions, protocols, and tools for building software and applications.

###2. What is Web API
**To put it in simple terms, API is some kind of interface which has a set of functions that allow programmers to access specific features or data of an application, operating system or other services.**

**Web API as the name suggests, is an API over the web which can be accessed using HTTP protocol.**

###3. What is REST

REST, or REpresentational State Transfer, is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other. REST-compliant systems, often called RESTful systems, are characterized by how they are stateless and separate the concerns of client and server

###4. What is API RESTful
**A RESTful API is an architectural style for an application program interface (API) that uses HTTP requests to access and use data. That data can be used to GET, PUT, POST and DELETE data types, which refers to the reading, updating, creating and deleting of operations concerning resources.**

A RESTful API uses commands to obtain resources. The state of a resource at any given timestamp is called a resource representation. A RESTful API uses existing HTTP methodologies defined by the RFC 2616 protocol, such as:

- GET to retrieve a resource;
- PUT to change the state of or update a resource, which can be an object, file or block;
- POST to create that resource; and
- DELETE to remove it.

Data formats the REST API supports include:
- application/json
- application/xml
- application/x-wbe+xml
- application/x-www-form-urlencoded
- multipart/form-data

###5. Guiding Principles of REST
- **Client–server** – By separating the user interface concerns from the data storage concerns, we improve the portability of the user interface across multiple platforms and improve scalability by simplifying the server components.
- **Stateless** – Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client.
- **Cacheable** – Cache constraints require that the data within a response to a request be implicitly or explicitly labeled as cacheable or non-cacheable. If a response is cacheable, then a client cache is given the right to reuse that response data for later, equivalent requests.
- **Uniform** interface – By applying the software engineering principle of generality to the component interface, the overall system architecture is simplified and the visibility of interactions is improved. In order to obtain a uniform interface, multiple architectural constraints are needed to guide the behavior of components. REST is defined by four interface constraints: identification of resources; manipulation of resources through representations; self-descriptive messages; and, hypermedia as the engine of application state.
- **Layered system** – The layered system style allows an architecture to be composed of hierarchical layers by constraining component behavior such that each component cannot “see” beyond the immediate layer with which they are interacting.
- **Code on demand** (optional) – REST allows client functionality to be extended by downloading and executing code in the form of applets or scripts. This simplifies clients by reducing the number of features required to be pre-implemented.

Keyword: web api restful

###6. HTTP code response status code
- 200 OK
- 400 Bad Request
- 401 Unauthorized (Similar to 403 Forbidden, but specifically for use when authentication is required and has failed or has not yet been provided)
- 403 Forbidden (The request contained valid data and was understood by the server, but the server is refusing action.)
- 404 Not Found (The requested resource could not be found but may be available in the future. Subsequent requests by the client are permissible.)
- 405 Method Not Allowed
- 500 Internal Server Error 

## Postman
- Postman là phần mềm miễn phí để test API, app cài đặt được trên cả Window, MacOS và Ubuntu.
- Truy cập trang chủ https://www.postman.com để cài đặt.
- Có thể tham khảo cách sử dụng postman cơ bản trên trang: https://viblo.asia/p/huong-dan-su-dung-postman-cho-test-api-aWj53Lb1K6m