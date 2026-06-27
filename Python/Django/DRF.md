## 1. What is Django REST Framework (DRF)?
Answer:
Django REST Framework (DRF) is a powerful and flexible toolkit for building RESTful APIs in Django. It provides features like serializers, authentication, permissions, viewsets, pagination, and a browsable API, making API development faster and more secure.

## Why use DRF?
- Serialization – Converts Python objects/models into JSON and vice versa.
- Authentication & Authorization – Supports Token Authentication, JWT, Session Authentication, etc.
- Class-Based Views & ViewSets – Helps write reusable and organized API logic.
- Browsable API – Provides a web interface to test APIs directly in the browser.
- Permissions & Throttling – Controls user access and API request limits.
- Filtering, Pagination, and Validation – Built-in support for common API features.\

## Key Components of DRF:
- Serializer – Converts data between Python objects and JSON.
- APIView – Base class for creating API views.
- Generic Views – Provides common CRUD operations.
- ViewSets – Combines related views into a single class.
- Routers – Automatically generates API URLs.
- Authentication & Permissions – Secures APIs.

## what is Serializer ??

A Serializer in DRF is a component that converts python (Django) model objects into JSON format and validates incoming JSON data before saving it to the database.

## Why do we use Serializers?

- Convert Python/Django objects to JSON (Serialization).
- Convert JSON data to Python objects (Deserialization).
- Validate input data.
- Create and update database records.

## Model

from django.db import models

class Student(models.Model):

    name = models.CharField(max_length=100)

    age = models.IntegerField()

## Serializer

from rest_framework import serializers

from .models import Student

class StudentSerializer(serializers.ModelSerializer):

    class Meta:

        model = Student

        fields = '__all__'

## Types of Serializers:

## there are two type of Serializer

# 1. Serializer
# 2. ModelSerializer

# 1. Serializer

it is Manually define fields.

class StudentSerializer(serializers.Serializer):

    name = serializers.CharField()

    age = serializers.IntegerField()

# 2. ModelSerializer

it is Automatically creates fields based on the Django model.

class StudentSerializer(serializers.ModelSerializer):

    class Meta:

        model = Student

        fields = '__all__'

## What is the difference between Serializer and ModelSerializer?

| Serializer                  | ModelSerializer                    |
| --------------------------- | ---------------------------------- |
| Fields are defined manually | Fields are generated automatically |
| More customization          | Less code                          |
| Not tied to models          | Works directly with models         |

## What is APIView in DRF?

APIView is a class-based view in DRF used to build REST APIs. It extends Django's View class and provides features such as request parsing, authentication, permissions, and response handling while supporting HTTP methods like GET, POST, PUT, PATCH, and DELETE.

## Example with Database:

from rest_framework.views import APIView

from rest_framework.response import Response

from .models import Student

from .serializers import StudentSerializer

class StudentAPIView(APIView):

    def get(self, request):

        students = Student.objects.all()

        serializer = StudentSerializer(students, many=True)

        return Response(serializer.data)


## URL Configuration

from django.urls import path

from .views import StudentAPIView

urlpatterns = [

    path('students/', StudentAPIView.as_view()),
]

## Difference between Django View and APIView:

| Django View              | DRF APIView                                         |
| ------------------------ | --------------------------------------------------- |
| Returns `HttpResponse`   | Returns `Response`                                  |
| No built-in API features | Supports authentication, permissions, serialization |
| Manual JSON handling     | Automatic JSON parsing/rendering                    |

## What is a ViewSet?
A ViewSet is a DRF class that combines multiple CRUD operations into a single class, allowing automatic URL routing and reducing boilerplate code.

Example:
from rest_framework import viewsets

from .models import Student

from .serializers import StudentSerializer

class StudentViewSet(viewsets.ModelViewSet):

    queryset = Student.objects.all()

    serializer_class = StudentSerializer

## URL Configuration:

from rest_framework.routers import DefaultRouter

from .views import StudentViewSet

router = DefaultRouter()

router.register('students', StudentViewSet)

urlpatterns = router.urls


## Types of ViewSets:
- ViewSet – Basic viewset with manual action definitions.
- GenericViewSet – Combines generic views with viewset functionality.
- ModelViewSet – Provides complete CRUD operations.
- ReadOnlyModelViewSet – Provides only list() and retrieve() methods.
## Advantages of ViewSet:
- Reduces repetitive code.
- Automatically generates URLs using routers.
- Groups related API logic in one class.
- Provides built-in CRUD operations with ModelViewSet.

## What is the difference between APIView and ViewSet?

| APIView                 | ViewSet                  |
| ----------------------- | ------------------------ |
| Manual URL mapping      | Automatic URL routing    |
| More control            | Less code                |
| Define methods manually | CRUD operations built-in |


## What is ModelViewSet?
ModelViewSet provides all CRUD operations automatically.

It includes:

- list()
- create()
- retrieve()
- update()
- partial_update()
- destroy()

## What is GenericAPIView?
Answer:
GenericAPIView provides common behavior and can be combined with mixins.

from rest_framework.generics import ListAPIView

class EmployeeList(ListAPIView):

    queryset = Employee.objects.all()

    serializer_class = EmployeeSerializer


## 10. What are Mixins in DRF?
Answer:
Mixins provide reusable CRUD functionality.

*Common Mixins:*

- CreateModelMixin
- ListModelMixin
- RetrieveModelMixin
- UpdateModelMixin
- DestroyModelMixin

from rest_framework import mixins, generics

class EmployeeAPI(mixins.ListModelMixin,

                  generics.GenericAPIView):

    queryset = Employee.objects.all()

    serializer_class = EmployeeSerializer

    def get(self, request):

        return self.list(request)

## What is Authentication in DRF?

Authentication in DRF is the process of identifying and verifying a user's identity before granting access to API endpoints.

## Why is Authentication used?
- To secure API endpoints.
- To identify the user making the request.
- To restrict access to authorized users only.
## Types of Authentication in DRF:

# 1. Session Authentication
- Uses Django's session framework.
- Commonly used for web applications.
# 2. Basic Authentication
- Uses username and password encoded in the request header.
## 3. Token Authentication
- Uses a unique token assigned to each user.
- Suitable for mobile and API clients.
# 4. JWT (JSON Web Token) Authentication
- Uses access and refresh tokens.
- Widely used in modern applications.

Example:

REST_FRAMEWORK = {

    'DEFAULT_AUTHENTICATION_CLASSES': [

        'rest_framework.authentication.TokenAuthentication',
    ]
}

## What is Permission in DRF?

Permissions in DRF are used to control access to API endpoints by determining whether a user has the right to perform a specific action.

## Common Permissions:

- AllowAny
- IsAuthenticated
- IsAdminUser
- IsAuthenticatedOrReadOnly

Example:

from rest_framework.permissions import IsAuthenticated

class EmployeeAPI(APIView):

    permission_classes = [IsAuthenticated]


## What is Token Authentication in DRF?

Token Authentication is a mechanism in DRF that uses a unique token to authenticate users instead of sending the username and password with every request.

## How Token Authentication Works:
- The user logs in with a username and password.
- The server generates a unique token for the user.
- The client stores this token.
- The client sends the token in the Authorization header with each request.
- DRF validates the token and grants access if it is valid.


## Example Request Header:

Authorization: Token 123abc456def789xyz

## Enable Token Authentication:
Install and add to settings.py

INSTALLED_APPS = [
    ...
    'rest_framework',

    'rest_framework.authtoken',
]

## Run migrations:
python manage.py migrate

## Configure DRF:

REST_FRAMEWORK = {

    'DEFAULT_AUTHENTICATION_CLASSES': [

        'rest_framework.authentication.TokenAuthentication',
    ],
}

# Generate Token:

python manage.py drf_create_token username


from rest_framework.authentication import TokenAuthentication

from rest_framework.permissions import IsAuthenticated

from rest_framework.views import APIView

from rest_framework.response import Response

class ProfileView(APIView):

    authentication_classes = [TokenAuthentication]

    permission_classes = [IsAuthenticated]

    def get(self, request):

        return Response({"message": "Authenticated User"})


## What is JWT Authentication?

Answer:
JWT (JSON Web Token) is a stateless authentication method.

## Structure:

Header.Payload.Signature

 ## Example:

Authorization: Bearer eyJhbGc...

##  What is Pagination in DRF?

Answer:
Pagination divides large datasets into smaller pages.

REST_FRAMEWORK = {

    'DEFAULT_PAGINATION_CLASS':

    'rest_framework.pagination.PageNumberPagination',

    'PAGE_SIZE': 10
}

## Types of Pagination in DRF
- PageNumberPagination
- LimitOffsetPagination
- CursorPagination

Filtering==> Filtering in DRF is the process of restricting API results based on user-specified criteria, such as query parameters.


## What is Throttling in DRF?

Throttling in Django REST Framework (DRF) is a mechanism used to control the number of API requests a client can make within a specific period of time.

## Why use Throttling?
- Prevent API abuse and spam.
= Protect server resources.
= Control API usage.
- Implement rate limiting for users and clients.
  
## Example:

Suppose the limit is 100 requests per day:

- A user can make up to 100 requests in 24 hours.
- After exceeding the limit, the API returns:

## Types of Throttling in DRF:
# 1 AnonRateThrottle
Limits requests for anonymous users.
# 2 UserRateThrottle
Limits requests for authenticated users.
# 3 ScopedRateThrottle
Applies different limits to different API endpoints.


# Configuration Example:
# settings.py

REST_FRAMEWORK = {

    'DEFAULT_THROTTLE_CLASSES': [

        'rest_framework.throttling.AnonRateThrottle',

        'rest_framework.throttling.UserRateThrottle',
    ],
    'DEFAULT_THROTTLE_RATES': {

        'anon': '100/day',

        'user': '1000/day',
    }
}

## What is Parser ??

A Parser in DRF is a component that converts incoming request data (such as JSON, form data, or XML) into Python objects accessible through request.data.

## How Parser Works:
- The client sends data to the API.
- DRF uses a parser based on the Content-Type header.
- The parser converts the data into Python objects.
- The parsed data becomes available through request.data.

POST /students/

Content-Type: application/json

{
    "name": "Vinod",

    "age": 25
}

## Built-in Parsers in DRF:

| Parser             | Description                                                          |
| ------------------ | -------------------------------------------------------------------- |
| `JSONParser`       | Parses JSON data (`application/json`).                               |
| `FormParser`       | Parses HTML form data (`application/x-www-form-urlencoded`).         |
| `MultiPartParser`  | Parses multipart form data and file uploads (`multipart/form-data`). |
| `FileUploadParser` | Parses raw file uploads.                                             |

## What is Renderer in DRF?

A Renderer in DRF is used to convert Python objects into a format such as JSON, HTML, or XML before sending the response to the client. DRF automatically selects the appropriate renderer based on the client's Accept header.


## Types:

- JSONRenderer
- BrowsableAPIRenderer

## How Renderer Works:
- The view returns Python data using Response().
- DRF selects a renderer based on the client's Accept header.
- The renderer converts the Python data into the required format (JSON, HTML, etc.).
- The formatted response is sent to the client.

from rest_framework.views import APIView

from rest_framework.response import Response

class StudentAPIView(APIView):

    def get(self, request):

        data = {

            "name": "Vinod",

            "age": 25
        }
        return Response(data)

##  Built-in Renderers in DRF:

        | Renderer               | Description                               |
| ---------------------- | ----------------------------------------- |
| `JSONRenderer`         | Renders data as JSON.                     |
| `BrowsableAPIRenderer` | Provides the DRF browsable API interface. |
| `TemplateHTMLRenderer` | Renders HTML templates.                   |
| `StaticHTMLRenderer`   | Returns raw HTML content.                 |


## 5. What is serializer.is_valid()?

It validates incoming data.

serializer = EmployeeSerializer(data=request.data)

if serializer.is_valid():

    serializer.save()

## What is validated_data?

After validation:

serializer.validated_data

*contains cleaned and validated data.*

## What is serializer.save()?

It calls:

- create() for POST
- update() for PUT/PATCH
  
 ##  What is perform_create()?

Used to customize save operations.

def perform_create(self, serializer):

    serializer.save(created_by=self.request.user)


## . What is get_queryset()?

Returns dynamic queryset.

def get_queryset(self):

    return Employee.objects.filter(

        department='IT'
    )


##   . What is get_queryset()?

Returns dynamic queryset.

def get_queryset(self):

    return Employee.objects.filter(

        department='IT'
    )

## What is get_serializer_class()?

Used to return different serializers.

def get_serializer_class(self):

    if self.action == 'list':

        return EmployeeListSerializer

    return EmployeeSerializer


  ##  What is Nested Serializer?
class DepartmentSerializer(serializers.ModelSerializer):
    class Meta:
        model = Department
        fields = '__all__'

class EmployeeSerializer(serializers.ModelSerializer):
    department = DepartmentSerializer()

    class Meta:
        model = Employee
        fields = '__all__'


##  What is Nested Serializer?

class DepartmentSerializer(serializers.ModelSerializer):
    class Meta:
        model = Department
        fields = '__all__'

class EmployeeSerializer(serializers.ModelSerializer):
    department = DepartmentSerializer()

    class Meta:
        model = Employee
        fields = '__all__'

# What is select_related() and prefetch_related() in DRF?


# select_related()

Used for ForeignKey and OneToOne.

Employee.objects.select_related('department')

prefetch_related()

# Used for ManyToMany.

Employee.objects.prefetch_related('skills')


## What is HyperlinkedModelSerializer?

HyperlinkedModelSerializer is a serializer that automatically generates fields based on a Django model and represents relationships using URLs instead of primary key IDs.


# Example using ModelSerializer:

from rest_framework import serializers

from .models import Student

class StudentSerializer(serializers.ModelSerializer):

    class Meta:

        model = Student

        fields = ['id', 'name', 'age']


# Example using HyperlinkedModelSerializer:

from rest_framework import serializers

from .models import Student

class StudentSerializer(serializers.HyperlinkedModelSerializer):

    class Meta:

        model = Student

        fields = ['url', 'name', 'age']


# Difference between ModelSerializer and HyperlinkedModelSerializer:

| ModelSerializer                | HyperlinkedModelSerializer      |
| ------------------------------ | ------------------------------- |
| Uses primary keys (`id`)       | Uses hyperlinks (`url`)         |
| Simple representation          | RESTful URL representation      |
| Includes `id` field by default | Includes `url` field by default |

## 40. What is the difference between Django and DRF?
| Django                  | DRF                    |
| ----------------------- | ---------------------- |
| Builds web applications | Builds REST APIs       |
| Returns HTML            | Returns JSON           |
| Uses Templates          | Uses Serializers       |
| Uses Views              | Uses APIViews/ViewSets |

## In Django ORM, relationships define how models are connected to each other. There are three main types of relationships:

# 1. One-to-One Relationship (OneToOneField)

A one-to-one relationship means one record is related to exactly one record.

Example:

A user has only one profile.

from django.db import models
from django.contrib.auth.models import User

class Profile(models.Model):
    user = models.OneToOneField(
        User,
        on_delete=models.CASCADE
    )
    address = models.CharField(max_length=100)

## Access:
profile = Profile.objects.get(id=1)
print(profile.user.username)

user = User.objects.get(id=1)
print(user.profile.address)

## 2. One-to-Many Relationship (ForeignKey)

A one-to-many relationship means one record can have multiple related records.

Example:

One department has many employees.

class Department(models.Model):
    name = models.CharField(max_length=100)

class Employee(models.Model):
    name = models.CharField(max_length=100)
    department = models.ForeignKey(
        Department,
        on_delete=models.CASCADE
    )

# Access:

    dept = Department.objects.get(id=1)
employees = dept.employee_set.all()

employee = Employee.objects.get(id=1)
print(employee.department.name)

## 3. Many-to-Many Relationship (ManyToManyField)

A many-to-many relationship means multiple records can be related to multiple records.

Example:

Students can enroll in many courses, and courses can have many students.


class Course(models.Model):
    name = models.CharField(max_length=100)

class Student(models.Model):
    name = models.CharField(max_length=100)
    courses = models.ManyToManyField(Course)

## Access:

student = Student.objects.get(id=1)
student.courses.all()

course = Course.objects.get(id=1)
course.student_set.all()



# Django REST Framework (DRF) Installation Process
# Step 1: Create a Virtual Environment
python -m venv venv

Activate the virtual environment:

Windows
venv\Scripts\activate

## Step 2: Install Django
pip install django

## Check the version:

python -m django --version

# Step 3: Create a Django Project
django-admin startproject myproject

cd myproject

## Step 4: Install Django REST Framework
pip install djangorestframework

Verify installation:

pip show djangorestframework


## Step 5: Add DRF to INSTALLED_APPS

Open settings.py:


INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'rest_framework',
]


## Step 6: Create an App
python manage.py startapp api

Add the app to INSTALLED_APPS:

INSTALLED_APPS = [
    ...
    'rest_framework',
    'api',
]


## Step 7: Run Database Migrations
python manage.py migrate



## Step 8: Create a Superuser (Optional)
python manage.py createsuperuser

Enter:

Username:
Email:
Password:


## Step 9: Create Your First API View
api/views.py
from rest_framework.views import APIView
from rest_framework.response import Response

class HelloAPIView(APIView):
    def get(self, request):
        return Response({"message": "Hello DRF"})


## Step 10: Create URL Configuration
api/urls.py

from django.urls import path
from .views import HelloAPIView

urlpatterns = [
    path('hello/', HelloAPIView.as_view()),
]

## project/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('api.urls')),
]

## Step 11: Run the Server
python manage.py runserver


## DRF Installation for Authentication (Optional)
Token Authentication
pip install djangorestframework

Add to INSTALLED_APPS:

INSTALLED_APPS = [
    ...
    'rest_framework',
    'rest_framework.authtoken',
]

Run migrations:

python manage.py migrate

## JWT Authentication

Install:

pip install djangorestframework-simplejwt

Add to settings.py:

REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': (
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ),
}