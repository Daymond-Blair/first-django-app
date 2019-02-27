# first-django-app
Simple "Hello World" app for learning Django URL Mapping. Utilized direct mapping as well as indirect mapping via the include() function.

## Direct Mapping
This provides direct access to a view through its URL. It links the views.py file from the app straight to the urls.py file in the project.

### Direct Mapping Syntax

from django.shortcuts import render
from django.http import HttpResponse

def index(request):
        return HttpResponse("Hello World!")
        
from django.contrib import admin
from django.conf.urls import url
from django.urls import path
from django.conf.urls import include
from AppTwo import views

urlpatterns = [
    #url('', views.index, name='index'),
    url(r'^AppTwo/', include('AppTwo.urls')),
    path('admin/', admin.site.urls),
]

## Include() Function
This allowewd me to look for a match with regex and link to an app's urls.py file. 

### Include() Syntax
from django.conf.urls import include

urlpatterns = [
        url(r'^app_name/', include('app_name.urls')),
]

The above code allows us to look for any match and find its urls.py file in the matching app. This is useful because instead of adding every app url to our project's urls.py file, we can make each app's urls.py file searchable independantly based off its unique regex pattern.
