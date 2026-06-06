 **What is Fast API?**

Ans=> **Fast API** is a modern, high-performance web framework for building APIs with  **Python** . It is
designed to create RESTful APIs quickly and efficiently using Python’s standard type hints. So that **Pydantic** (for data validation and serialization).Automatic provides API documentation (Swagger UI)

**Starlette** (for web handling)

**Starlette** is a lightweight **ASGI (Asynchronous Server Gateway
Interface)** framework for building high-performance web
applications and services in Python. Designed with modularity and speed in
mind, it forms the foundation for popular frameworks such as  **FastAPI** . Starlette
emphasizes simplicity, async support, and interoperability within the ASGI
ecosystem.

key features

Automatic API
documentation (Swagger UI)

Pydantic user for  Data validation

High performance

Type hint-based development

## 2. What is REST API?

ans=>
A REST API (Representational State Transfer API)
enables communication between client and server over the internet using  **HTTP requests** .

    Uses JSON format data..

It allows a **frontend
(React, mobile app)** to talk to a **backend (FastAPI, Django, etc.)** and exchange data.

Key Features of REST API

    .Stateless (server does
not remember previous request)

    .Uses JSON format (mostly)

    .Works over HTTP

    .Easy to use and scalable

REST API uses standard HTTP methods:

GET → Get data

POST → Create new data

PUT → Update full data

PATCH → Update partial data

DELETE → Delete data

from fastapi import FastAPI

app = FastAPI()

## # GET API

   @app.get("/users")

  def get_users():

  return {"users":
["Vinod", "Rahul"]}

# POST API

  @app.post("/users")

  def create_user(name: str):

  return {"message":

f"{name} created"}

3. **What is ASGI?**

ASGI (Asynchronous Server Gateway Interface) is a standard interface between
web servers and Python applications.

ASGI → asynchronous (Fast API, Sta2rlette)

ASGI allows handling:

=>Web Sockets

=>Background tasks

=>.Concurrent requests

4 What is Pydantic?

Pydantic is a data validation and parsing library used in FastAPI.

 It uses Python type hints to:

* Validate request/response
  data
* Convert data types
  automatically
* Provide error messages

from pydantic import BaseModel

class User(BaseModel):

    name: str

    age: int

5. What is Dependency Injection in
   Fast API?

**Ans=> Dependency Injection is a
design pattern in which a class or function receives it is dependencies from an
external source, and FastAPI automatically provides required resources (such as
database connections, authentication, or configurations) and dependency use
`Depends` to efficient, reusable, and, clean code.**

## from fastapi import Depends

def get_db():

   return "DB"

**@app.get("/users")

def get_users(db = Depends(get_db)):

   return {"db": db}

**6 .Path
Parameters ?

**Path Parameters** ** are variables included in the URL path that are used to identify and
access a specific resource. They are required parts of the URL and are commonly
used to fetch a particular item, such as getting a user by ID, product details,
or an order by its ID.

** `<span>/users/{id}</span>` → Get user by ID

`<span>/products/{id}</span>` → Get product details

`<span>/orders/{order_id}</span>` → Fetch order by order ID**

@app.get("/user/{id}")

def get_user(id: int):

 return id**

7.Query Parameters ?

**Query Parameters** are variables passed after the URL  that are used to filter, search, sort, or
modify , Pagination the response from the server. They are optional and help
customize the data returned without changing the endpoint.

/users?name=vinod → Search
users by name

/products?category=electronics → Filter
products by category

/items?page=1&limit=10 →
Pagination

from **fastapi** **import** **FastAPI**

**app** **=** **FastAPI**()

**@**app**.**get(**"/items/"**)

**def** **get_items**(**name**:
**str**, **age**: **int**):

**return** {

**"name"**: **name**,

**"age"**: **age**

}

8.What is
Request Body?

Request Body is the JSON
data sent from the client  to the server
inside an HTTP request to create, update, or process information. It is mainly
used in POST, PUT, and PATCH requests. It is automatically  validates
and  converted into JSON  data
to Python object using
Pydantic  models.

from fastapi import FastAPi

from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):

name: str

age: int

@app.post("/users/")

def create_user(user: User)

    return {"message":
"User created", "data": user}
