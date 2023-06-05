# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Clone the repository from github

### Step 2:
Create Django Admin project

### Step 3:
Create a new App

### Step 4:
Create python programs for views and urls

### Step 5:
Create a HTML file of forms

### Step 6:
Publish the website in the given URL.

## PROGRAM :
#### math.html:
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Area of Rectangle</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    body {
  background-color: #41436A;
}
    .container{
    width: 1080px;
    height: 440px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-width: 2px 2px 2px 2px;
    border-style: solid;
    box-shadow: 15px 15px 8px #41436A;
    
}
    .heading{
        text-align: center;
    }
    .element{
        padding-top: 20px;
        padding-bottom: 20px;
        padding-left: 20px;
        padding-right:20px;
        text-align: center;
        font-size: 20px;
        background-color:#984063;
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }
    .footer{
        display: block;
        width: 100%;
        height: 40px;
        background-color:#fe9667;
        color: black;
        text-align: center;
        padding-top: 7px;
        font-size: large;
        font-family: sans-serif;
        font-style: italic;
        
        }
</style>

<body>
     
    <div class="container">
        <div class="element", backgroung color="white">
        <h1  class="heading">AREA OF RECTANGLE</h1>
        </div>
        <form method="POST">
            {% csrf_token %}
            <div class="element"> 
                Length=<input type="text" name="length" value={{length}}></input><br/>
            </div>
            <div class="element">
                Breadth=<input type="text" name="breadth" value={{breath}}></input><br/>
            </div>
            <div class="element">
                <input type="submit" value="CALCULATE"></input><br/>
            </div>
            <div class="element">
                Area=<input type="text" name="area" value={{area}}></input>
            </div>
            <div class="footer">
                    Developed by Prajeeth K T
            </div>
        </form>
    </div>
    
</body>
</html>
```
#### views.py:
```py
from django.shortcuts import render
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
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'myapp/math.html',context)
```
#### urls.py:
```py
from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```
## SERVER OUTPUT:
![Screenshot 2023-06-05 113436](https://github.com/Gokul0117/serversideprocessing/assets/121165938/d66edbd7-74da-4743-8aed-3b3da8ce5c2c)



## CLIENT OUTPUT:
![Screenshot 2023-06-05 113638](https://github.com/Gokul0117/serversideprocessing/assets/121165938/985b95fe-7869-478c-b89a-7a83edb3269b)

## Result:
Thus a program to design a website to perform mathematical calculations in server side has been created and executed successfully.
