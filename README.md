# Ex.05esign a Website for Server Side Processing
## Date:08.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
math.html:
```
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of prism</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body 
{
background-color:#000001;
}
.edge {
width: 1440px;
margin-left: auto;
margin-right: auto;
padding-top: 250px;
padding-left: 300px;
}
.box {
display:block;
border: Thick dashed rgb(8, 190, 190);
width: 500px;
min-height: 300px;
font-size: 20px;
background-color:#101820;
}
.formelt{
color:#ecdb41;
text-align: center;
margin-top: 7px;
margin-bottom: 6px;
}
h1
{
color:#FEE715;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h2 align="center"> <font color="yellow"> Surface Area of Right Cylinder </font> </h2>
<center><font color="orange"> KAVI M S <font></center>
<center>(212223220044) </center>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Radius : <input type="text" name="radius" value="{{r}}"></input>(in m)<br/>
</div>
<div class="formelt">
Height : <input type="text" name="height" value="{{h}}"></input>(in m)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Area : <input type="text" name="surf_area" value="{{surf_area}}"></input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>
```
views.py:
```
from django.shortcuts import render
def surf_area(request):
    context={}
    context['surf_area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('radius','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('Radius=',r)
        print('Height=',h)
        surf_area = (2*3.14*int(r)*int(h)) + (2*3.14*int(r)*int(r))
        context['surf_area'] = surf_area
        context['r'] = r
        context['h'] = h
        print('Surface Area=',surf_area)
    return render(request,'mathapp/math.html',context)
```
urls.py:
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfaceareaofrightcylinder/',views.surf_area,name="surfaceareaofrightcylinder"),
    path('',views.surf_area,name="surfaceareaofrightcylinderroot")
]
```

## SERVER SIDE PROCESSING:
![WhatsApp Image 2024-04-08 at 13 23 27_f785e302](https://github.com/Kavi45-msk/MathServer/assets/147457752/a4d7dd74-c2a0-4521-8bd4-7a039fa7d4ac)


## HOMEPAGE:
![WhatsApp Image 2024-04-08 at 13 23 27_29723452](https://github.com/Kavi45-msk/MathServer/assets/147457752/01f90c3e-5650-4559-ab43-719aeefec809)


## RESULT:
The program for performing server side processing is completed successfully.
