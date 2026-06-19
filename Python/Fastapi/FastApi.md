##### 1. What is Fast API?

Ans=> Fast API is a modern, high-performance web framework for building APIs with Python. It is
designed to create RESTful APIs quickly and efficiently using Python’s standard type hints. So that Pydantic (for data validation and serialization).Automatic provides API documentation (Swagger UI)

## Starlette (for web handling)

Starlette is a lightweight ASGI (Asynchronous Server Gateway
Interface)\*\* framework for building high-performance web
applications and services in Python. Designed with modularity and speed in
mind, it forms the foundation for popular frameworks such as FastAPI. Starlette
emphasizes simplicity, async support, and interoperability within the ASGI
ecosystem.

##### **key features**

1. Automatic API documentation (Swagger UI)
2. Pydantic user for Data validation
3. High performance
4. Type hint-based development


## 3. What are the advantages of FastAPI?
Answer:

Automatic API documentation

Data validation

Async programming support

Easy integration with databases

High performance


##### 2. What is REST API?

ans=> A REST API (Representational State Transfer API) enables communication between client and server over the internet using HTTP requests .

Uses JSON format data..

It allows a frontend (React, mobile app) to talk to a backend (FastAPI, Django, etc.) and exchange data.

##### Key Features of REST API

1. Stateless (server does not remember previous request)
2. Uses JSON format (mostly)
3. Works over HTTP
4. Easy to use and scalable

##### REST API uses standard HTTP methods:

GET → Get data

POST → Create new data

PUT → Update full data

PATCH → Update partial data

DELETE → Delete data

from fastapi import FastAPI

app = FastAPI()

##### GET API

@app.get("/users")

def get_users():

return {"users":
["Vinod", "Rahul"]}

##### POST API

@app.post("/users")

def create_user(name: str):

return {"message":

f"{name} created"}

##### **3 What is ASGI?**

ASGI (Asynchronous Server Gateway Interface) is a standard interface between web servers and Python applications.

ASGI → asynchronous (Fast API, Sta2rlette)

ASGI allows handling:

=>Web Sockets

=>Background tasks

=>.Concurrent requests

##### 4 What is Pydantic?

Pydantic is a data validation and parsing library used in FastAPI.

It uses Python type hints to:

- Validate request/response data
- Convert data types automatically
- Provide error messages

from pydantic import BaseModel

class User(BaseModel):

name: str

age: int

##### 5 What is Dependency Injection in Fast API?

Ans=> Dependency Injection is a design pattern in which a class or function receives it is dependencies from an external source, and FastAPI automatically provides required resources (such as database connections, authentication, or configurations) and dependency use Depends to efficient, reusable, and, clean code.

from fastapi import Depends

def get_db():

return "DB"

@app.get("/users")

def get_users(db = Depends(get_db)):

return {"db": db}

##### 6 Path Parameters ?

Path Parameters are variables included in the URL path that are used to identify and
access a specific resource. They are required parts of the URL and are commonly
used to fetch a particular item, such as getting a user by ID, product details,
or an order by its ID.

/users/{id} → Get user by ID

/products/{id}→ Get product details

/orders/{order_id} → Fetch order by order ID

@app.get("/user/{id}")
def get_user(id: int):

return id

##### 7.Query Parameters ?

Query Parameters are variables passed after the URL that are used to filter, search, sort, or
modify , Pagination the response from the server. They are optional and help
customize the data returned without changing the endpoint.

/users?name=vinod → Search users by name

/products?category=electronics → Filter products by category

/items?page=1&limit=10 → Pagination
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/")

def get_items(name: str, age: int):

return {

"name": name,

"age": age

}

### Difference Between Path and Query Parameters

| Path Parameter      | Query Parameter  |
| ------------------- | ---------------- |
| Required            | Optional         |
| Part of URL path    | After `?`        |
| Identifies resource | Filters/Searches |

##### 8.What is Request Body?

Request Body is the JSON data sent from the client to the server inside an HTTP request to create, update, or process information. It is mainly used in POST, PUT, and PATCH requests. It is automatically validates and converted into JSON data
to Python object using Pydantic models.

from fastapi import FastAPi

from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):

name: str

age: int

@app.post("/users/")

def create_user(user: User)

return {"message": "User created", "data": user}

#### 9. What is BaseModel?// Pydantic?

ans -> BaseModel is the main class or (parent class, core class) provided by the Pydantic library that is used to define, data validation, parsing, and serialization in Python applications. FastAPI, it is commonly used to create request and response schemas.

- When a class inherits from BaseModel, Pydantic automatically validates incoming data, converts data types
- when possible, and generates useful error messages if the data is invalid.

FastAPI. BaseModel also supports optional fields, default values, nested models, custom validators, and automatic JSON serialization, which makes API development easier, safer, and more maintainable.

#### 10 Why is BaseModel Used?

Before Pydantic, developers had to manually validate data:

Ex--
from pydantic import BaseModel

class User(BaseModel):
name: str

age: int

email: str

### BaseModel in FastAPI Request Body

from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):

name: str

age: int

@app.post("/users")

def create_user(user: User):

return user

#### Optional Fields

from typing import Optional
from pydantic import BaseModel

class User(BaseModel):

name: str

age: int

phone: Optional[str] = None //Optional Fields

### Default Values

class User(BaseModel):

name: str

age: int

is_active: bool = True ///Default Values

### Nested Models

from pydantic import BaseModel

class _Address_(BaseModel):

city: str

state: str

class User(BaseModel):

name: str

address: _Address_

## List Fields

from typing import List
from pydantic import BaseModel

class User(BaseModel):

name: str

skills: List[str]

### Model Serialization

Ans Convert model object into dictionary:

user = User(
name="Vinod",
age=25
)
print(user.model_dump())

## Convert to JSON:

print(user.model_dump_json())

### Field Constraints

from pydantic import BaseModel, Field

class User(BaseModel):

name: str = Field(min_length=3, max_length=50)

age: int = Field(gt=0, lt=100)

### Custom Validators

from pydantic import BaseModel, field_validator

class User(BaseModel):
name: str

    @field_validator("name")
    @classmethod
    def validate_name(cls, value):
        if len(value) < 3:
            raise ValueError("Name too short")
        return value

## What is Response Model in FastAPI?

Ans-> A Response Model in FastAPI is used to define the structure, type, and validation of the data returned by an API endpoint. It ensures that the response sent to the client follows a specific schema.

- FastAPI uses Pydantic BaseModel classes as response models.

It is specified using the response_model parameter and is usually a Pydantic BaseModel. FastAPI automatically validates the response, filters out unwanted fields, serializes the data into JSON, and generates API documentation in Swagger UI.

Response Models improve consistency, security, and maintainability by ensuring that only the intended data is sent back to the client.

## Why Use Response Models?

1. Validates response data
2. Filters unwanted fields
3. Provides automatic API documentation
4. Ensures consistent API responses
5. Improves security by hiding sensitive data

## Example

from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):
id: int

name: str

email: str

@app.get("/user", response_model=User)

def get_user():

return {

"id": 1,

"name": "Vinod",

"email": "vinod@gmail.com"
}

## How Response Model Works

@app.get("/user", response_model=User)

## Filtering Extra Fields

class User(BaseModel):
id: int

name: str

@app.get("/user", response_model=User)

def get_user():

return {

"id": 1,

"name": "Vinod",

"email": "vinod@gmail.com",

"password": "123456"
}

output
Response:
{
"id": 1,
"name": "Vinod"
}
Response Model with Nested Objects
Response Model with List

### Response Model vs Request Model

| Feature  | Request Model          | Response Model         |
| -------- | ---------------------- | ---------------------- |
| Purpose  | Validate incoming data | Validate outgoing data |
| Used In  | Request Body           | API Response           |
| Based On | BaseModel              | BaseModel              |
| Security | Input Validation       | Output Filtering       |
| Example  | POST/PUT               | GET/POST Response      |

## 10 What is ORM?

Ans-> ORM (Object Relational Mapping) is a technique that maps database tables to Python classes.

### 11. What is SQLAlchemy?

Ans :-> SQLAlchemy is a Python ORM library used for database operations. It provides an ORM (Object Relational Mapping) that allows developers to interact with databases using Python classes and objects instead of writing raw SQL queries.

In FastAPI, SQLAlchemy is commonly used to connect and communicate with databases such as MySQL, PostgreSQL, SQLite, Oracle, and SQL Server.

SQLAlchemy provides features like CRUD operations, relationships, session management, transaction handling, and database abstraction. In FastAPI, SQLAlchemy is commonly used to perform database operations efficiently and securely.

### SQLAlchemy Model

class User(Base):

tablename= "users"

    id = Column(Integer, primary_key=True)

    name = Column(String)

## here

Table → users

Row → Object

Column → Class Attribute

## 12 Why Use SQLAlchemy?

ans-> Database Abstraction (Works with multiple databases: like MySQL, PostgreSQL, SQLite, Oracle ,SQL Server)

1. Less SQL Code

2. Easy CRUD Operations

3. Relationship Management like
   One-to-One
   One-to-Many
   Many-to-Many

## Installing SQLAlchemy

pip install sqlalchemy

pip install pymysql

## Creating Database Connection

DATABASE_URL = "mysql+pymysql://root:password@localhost/testdb"

engine = create_engine(DATABASE_URL)

## Creating Base Class

_All models inherit from Base._

from sqlalchemy.orm import declarative_base

Base = declarative_base()

Creating Model

from sqlalchemy import Column, Integer, String

class User(_Base_): // _inherit from Base._

tablename = "users"

    id = Column(Integer, primary_key=True)

    name = Column(String)
    
    email = Column(String)

## Mapping

| Database Column | Python Attribute |

| --------------- | ---------------- |

| id              | id |

| name            | name |

| email           | email |

### Creating Table

- This creates tables in the database.

_Base.metadata.create_all(bind=engine)_

## Session Management

Session is used to communicate with the database.

from sqlalchemy.orm import sessionmaker

SessionLocal = sessionmaker(

autocommit=False,

autoflush=False,

bind=engine
)

## Create session:

db = SessionLocal()

## 1 Create Record

user = User(

name="Vinod",

email="vinod@gmail.com"
)

db.add(user)

db.commit()

db.refresh(user)

## 2 Read Data

Get All Users

users = db.query(User).all()

## 3 Get Single User

user = db.query(User).filter(User.id == 1).first()

## Update Data

user = db.query(User).filter(User.id == 1).first()

user.name = "Updated Name"

db.commit()

## 4. Delete Data

user = db.query(User).filter(User.id == 1).first()

db.delete(user)

db.commit()

## 13. What is Middleware in FastAPI?

Ans-> Middleware in FastAPI is a function that is executes before and after every HTTP request in a FastAPI application.

It acts as a bridge between the client request and the server response, allowing developers to process requests globally.

Middleware is commonly used for logging, authentication, authorization, request timing, adding custom headers, rate limiting, and CORS handling. The call_next() function passes the request to the next middleware or endpoint and returns the response, which can then be modified before being sent back to the client.

Client Request
↓
Middleware (Before Request)
↓
API Endpoint
↓
Middleware (After Response)
↓
Client Response

from fastapi import FastAPI, Request

app = FastAPI()

@app.middleware("http")

async def log_requests(request: Request, call_next):

print("Request Started")

    response = await call_next(request)

    print("Request Completed")

    return response

_For every request, middleware executes automatically._

## Understanding the Parameters

async def log_requests(request, call_next):

request
Contains information about the incoming request:

request.method

request.url

request.headers

request.client

## Measure Request Processing Time

A very common interview example.

import time

from fastapi import FastAPI, Request

app = FastAPI()

@app.middleware("http")

async def add_process_time(request: Request, call_next):

start_time = time.time()

    response = await call_next(request)

    process_time = time.time() - start_time

    response.headers["X-Process-Time"] = str(process_time)

    return response

### Common Uses of Middleware

1. Logging
   print(request.url)
   Track incoming requests.

2. Authentication
   Check JWT tokens or API keys.

3. Authorization
   Verify user permissions.

4. Rate Limiting
   Limit number of requests.

5. Performance Monitoring
   Track response time.

6. CORS Handling
   Allow requests from specific domains.

7. Security Headers
   Add security-related headers.

## Built-in Middleware Example (CORS)

from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(

CORSMiddleware,

allow_origins=["*"],

allow_credentials=True,

allow_methods=["*"],

allow_headers=["*"]
)

## Middleware vs Dependency

This allows cross-origin requests.

| Middleware                   | Dependency                           |
| ---------------------------- | ------------------------------------ |
| Runs for every request       | Runs only on selected routes         |
| Global processing            | Route-specific processing            |
| Executes before endpoint     | Executes during endpoint execution   |
| Used for logging, CORS, auth | Used for DB session, user validation |

## What is CORS in FastAPI?

Ans ->
CORS (Cross-Origin Resource Sharing) is a security mechanism implemented by web browsers that controls how resources on a web server can be requested from a different domain, origin, or port.

CORS allows a frontend application (React, Angular, Vue, etc.) hosted on one origin to communicate with a backend API hosted on another origin.

CORS is configured using the CORSMiddleware. It is commonly required when a frontend application like React runs on one port or domain and the FastAPI backend runs on another. By configuring allow_origins, allow_methods, allow_headers, and allow_credentials, we can control which clients are permitted to access our API.

_Example_
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware

app = FastAPI()

app.add_middleware(

CORSMiddleware,  

 allow_origins=["*"], // url

allow_credentials=True,//Allows cookies and authentication credentials. JWT Tokens, Session Cookie,Authentication  

 allow_methods=["*"], // http mathod like GET POST, PUT, DELETE, PATCH, OPTIONS allow_methods=["GET", "POST"]

allow_headers=["*"] // Authorization, Content-Type, Accept
)

_How CORS Works_
Browser
↓
Checks Origin
↓
Server Response
↓
Access-Control-Allow-Origin
↓
Allowed or Blocked

## What is an Origin?

_3 ke combination hai_
An Origin consists of (Protocol + Domain + Port)

Protocol → http (http://localhost:3000)

Domain → localhost

Port → 3000

## What is CORSMiddleware?

CORSMiddleware is a FastAPI middleware used to enable Cross-Origin Resource Sharing (CORS). It allows frontend applications running on different domains, ports, or origins to communicate with the FastAPI backend by adding the required CORS headers to HTTP responses. It is commonly used when a React, Angular, or Vue frontend and a FastAPI backend run on different ports or domains.

## Why Do We Need CORS? // Why Do We Need CORSMiddleware?

Frontend (React) url -> http://localhost:3000

Backend (FastAPI) url -> http://localhost:8000

React makes an API call: fetch("http://localhost:8000/users")
_Without CORS enabled, the browser blocks the request. Because the request is coming from a different origin._

_Without CORSMiddleware, the browser blocks the request and shows:_
_To allow the request, add CORSMiddleware._

## CORS vs Authentication

| CORS                       | Authentication               |
| -------------------------- | ---------------------------- |
| Controls browser access    | Verifies user identity       |
| Browser security feature   | Application security feature |
| Checks origin              | Checks user credentials      |
| Not a replacement for auth | Protects resources           |

## 12. What is JWT

JWT (JSON Web Token) is a token-based authentication mechanism used to securely transmit user information between a client and a server.
A JWT consists of three parts: Header, Payload, and Signature. After a user successfully logs in, the server generates a JWT and sends it to the client. The client stores the token and sends it in the Authorization header with subsequent requests. The server verifies the token before granting access to protected resources. JWT is stateless, scalable, secure, and widely used in FastAPI applications for authentication and authorization.

Example
from jos

e import jwt

token = jwt.encode(

{"sub": "vinod"},

"secret_key",

algorithm="HS256"
)

This generates a JWT token that can be used for secure user authentication. 15. What is JWT?

Answer:
JWT (JSON Web Token) is used for authentication.

After login, the server generates a token and sends it to the client.

The client sends the token with every request.

## Why Use JWT?

1. Authenticate users after login.
2. Authorize access to protected resources.
3. Enable stateless authentication.
4. Secure API communication between client and server.

## JWT vs Session Authentication

| JWT              | Session                       |
| ---------------- | ----------------------------- |
| Stateless        | Stateful                      |
| Stored on Client | Stored on Server              |
| Scalable         | Less Scalable                 |
| Good for APIs    | Good for Traditional Web Apps |
| Uses Tokens      | Uses Session IDs              |

**Session Authentication:** Authentication information is stored on the server, and the client only stores a session ID.

### 19. What are JWT Components?

Answer: there are components

1. Header
2. Payload
3. Signature

### Authentication vs Authorization

| Authentication  | Authorization                |
| --------------- | ---------------------------- |
| Verify identity | Verify permissions           |
| Login process   | Access control               |
| Happens first   | Happens after authentication |
| Example: Login  | Example: Admin access        |

### 22. What is Async in FastAPI?

Answer: Async allows handling multiple requests simultaneously without blocking.

@app.get("/")

async def home():

return {"message":"Hello"}

## Difference Between Sync and Async

    | Sync                 | Async                 |

| -------------------- | --------------------- |

| Executes one by one | Executes concurrently |

| Slower for I/O tasks | Faster for I/O tasks |

| Uses `def` | Uses `async def` |

### 21. What is a 422 Unprocessable Entity Error?

Answer: This error occurs when request data does not match the Pydantic schema.

## What is Swagger UI?

Answer: Swagger UI is automatically generated API documentation.

## What is OAuth2?

OAuth2 is an authorization framework that allows users to grant limited access to applications without sharing their passwords. It works using access tokens and is commonly used for API security and social logins such as Google and GitHub login. In FastAPI, OAuth2 is often implemented with JWT tokens, where the user authenticates, receives an access token, and includes that token in the Authorization header for accessing protected resources.

## Why Use OAuth2?

Secure API access

Login with Google, GitHub, Facebook, etc.

Avoid sharing user passwords

Provide token-based authentication

Support third-party integrations

## OAuth2 vs JWT

OAuth2 JWT
Authorization Framework Token Format
Defines How Access is Granted Stores User Information
Can Use JWT Tokens JWT Can Be Used Inside OAuth2
Handles Authentication Flow Handles Data Transmission
More Comprehensive Just a Token Standard

## 8. Difference Between PUT and PATCH

| PUT                   | PATCH                   |
| --------------------- | ----------------------- |
| Updates full resource | Updates specific fields |
| Replaces old data     | Partial modification    |

## 6. What is an API?

Answer: API (Application Programming Interface) allows communication between different applications.

Example:

Frontend sends request

Backend processes request

Backend returns response

## 26. What is APIRouter in FastAPI?

APIRouter helps organize routes into separate files/modules.
Benefits:
Better code organization

Reusable routes

Easy maintenance

## . Difference Between File and UploadFile

| File                        | UploadFile     |
| --------------------------- | -------------- |
| Loads entire file in memory | Streams file   |
| Less efficient              | More efficient |
| Small files                 | Large files    |

## What is HTTPException?

Answer:
Used to return custom error responses.

## 5. What is Alembic?
 
Answer: Alembic is a database migration tool for SQLAlchemy.

Used for:

Create tables, 
Modify columns, 
Database version control

Commands:

alembic revision --autogenerate -m "create users table"

alembic upgrade head 

## 36. What is Database Migration?

Answer: Migration means applying database schema changes without manually writing SQL.

Examples:

Create table, 
Add column, 
Remove column, 
Modify datatype

## Create a Virtual Environment (Recommended)

python -m venv 

venv\Scripts\activate 

2. Install FastAPI and Uvicorn

pip install fastapi uvicorn

. Run the Application

uvicorn main:app --reload

## Q: Why is Uvicorn used with FastAPI?

Answer: Uvicorn is an ASGI server used to run FastAPI applications. It handles incoming HTTP requests and serves the FastAPI app efficiently with asynchronous support


## What is HTTPException in FastAPI?
Answer:

HTTPException is used in FastAPI to return custom HTTP error responses to the client. It allows you to send an error status code along with a descriptive message.

from fastapi import HTTPException

raise HTTPException(
    status_code=404,
    detail="User not found"
)


or  

from fastapi import FastAPI, HTTPException

app = FastAPI()

@app.get("/users/{user_id}")
def get_user(user_id: int):
    if user_id != 1:
        raise HTTPException(
            status_code=404,
            detail="User not found"
        )
    return {"user_id": user_id}


| Status Code | Meaning               |
| ----------- | --------------------- |
| 200         | success               |
| 201         | create                |
| 400         | Bad Request           |
| 401         | Unauthorized          |
| 403         | Forbidden             |
| 404         | Not Found             |
| 500         | Internal Server Error |
