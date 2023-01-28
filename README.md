# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Create a new django project and app.
### Step 2:
Make on changes in settings and create templates folder.


### Step 3:
Create a code for frontend of calculation using HTML and CSS and save it in templates

### Step 4:
Give an url mapping and write a python code for calculation in views.


### Step 5:
Take a screenshotof the site and upload it.


## PROGRAM :
### HTML:
```<!DOCTYPE html>
<html>
    <head>
        
        <Title>Calculate area of rectangle</Title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <style>
        body{background-color: cyan;
        }
        .edge{
            width:1080px;
            margin-left:auto;
            margin-right: auto;
            padding-top: 200px;
            padding-left: 300px;
        }
        .box{
            display: block;
            border: thick red;
            width:500px;
            min-height: 300px;
            font-size: 20px;
            background-color: purple;
            text-align:center;
            margin-left:auto;
            margin-right: auto;
        }
        .formelt{
            color:red;
            text-align: center;
            margin-top: 5px;
            margin-bottom: 5px;
        }
        .h1{
            color:red;
            text-align: center;
            padding-top: 20px;
        }

        </style>

    </head>
    <body>
        <div class="edge">
            <div class="box">
                <h1>Area of Rectangle</h1>
                <form method="POST">
                {% csrf_token%}
                <div class="formelt">
                    Length: <input type="text" name="length" value="{{1}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    Breadth: <input type="text" name="breadth" value="{{1}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br/>
                </div>
                <div class="formelt">
                    Area: <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
                </div>
                </form>
            </div>

        </div>

    </body>
</html>
```
### Views:
```
from django.shortcuts import render

# Create your views here.
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area= int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=', area)
    return render(request,"serversideprocess.html",context)
```
### urls:
```
from django.contrib import admin
from django.urls import path
from mathcalc import views


urlpatterns = [
    path('admin/', admin.site.urls),
    path('area/',views.rectarea),
]
```


## OUTPUT:
![rect](https://user-images.githubusercontent.com/118707051/215271809-138e6640-4aae-47f7-bd26-610031503812.jpg)


## Result:
Thus a website to perform mathematical calculations in server side is developed.
