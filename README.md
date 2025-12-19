# Ex.05 Design a Website for Server Side Processing
# Date:17/12/25
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
math.html
```
    <head>
        <title>Calculate Power of a lamp</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                background-color: #8566b0;
                margin: 0;
                padding: 0;
            }
    
            h1 {
                text-align: center;
                color: #0a0909;
                margin-top: 40px;
            }
    
            form {
                background-color: rgb(177, 104, 174);
                max-width: 400px;
                margin: 30px auto;
                padding: 30px;
                border-radius: 10px;
                box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            }
            label {
                display: block;
                margin-bottom: 8px;
                font-weight: bold;
            }
    
            input[type="number"] {
                width: 100%;
                padding: 8px;
                margin-bottom: 20px;
                border: 1px solid #ccc;
                border-radius: 6px;
            }
    
            button {
                background-color: #d915a1;
                color: white;
                padding: 10px 20px;
                border: none;
                border-radius: 6px;
                cursor: pointer;
                font-size: 16px;
                width: 100%;
            }
            button:hover {
                background-color: #d6131a;
            }
    
            p {
                margin-top: 20px;
                text-align: center;
                font-size: 18px;
                color: #222;
            }
        </style>
    </head>
    <body>
        <h1 align="center">Calculate Power of a Lamp</h1>
    <form action="{%url 'home'%}" method="post">
        {% csrf_token %}
    Intensity:
    <input type="text" name="intensity-input"> in m<br><br>
    Resistance:
    <input type="text" name="resistance-input">in ohms <br><br>
    <button type="submit">Calculate</button>
    <p align="center">The power of the lamp is:{{output}} watt </p>
    </form>
    </body>
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.power,name='home'),

]
```
views.py
```
from django.shortcuts import render

def power(request):
    output = None  
    if request.method == 'POST':
      
            intensity = int(request.POST.get('intensity-input'))
            resistance = int(request.POST.get('resistance-input'))
            output = (intensity ** 2) * resistance
        
    return render(request, 'mathapp/math.html', {'output': output})
```


# SERVER SIDE PROCESSING:<img width="1038" height="268" alt="Screenshot 2025-12-19 104235" src="https://github.com/user-attachments/assets/91800a7f-eb14-4ce9-a03e-1a34d72641b6" />

# HOMEPAGE:<img width="1038" height="591" alt="Screenshot 2025-12-19 104252" src="https://github.com/user-attachments/assets/d6d57772-335c-44c5-9d0d-fbf9c896548b" />

# RESULT:
The program for performing server side processing is completed successfully.
