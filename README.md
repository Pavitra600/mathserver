# Ex.05 Design a Website for Server Side Processing
# Date: 6/12/2024
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
---
math.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Calculator</title>
    <style>
        
        body {
            background-color: salmon;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        
        .container {
            max-width: 400px;
            margin: 50px auto;
            text-align: center;
            background-color: beige;
            color: saddlebrown);
            padding: 20px;
            border: 3px dashed blue;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

       
        input[type="text"] {
            width: 90%;
            padding: 8px;
            margin: 10px 0;
            border: 1px solid rgb(60, 19, 222);
            border-radius: 5px;
            box-sizing: border-box;
        }

        
        button {
            padding: 10px 15px;
            background-color: red;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            text-transform: uppercase;
        }

        button:hover {
            background-color: darkred;
        }

        
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
        }

        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        form {
            margin: 0 auto;
        }

        
        h2 {
            margin-top: 20px;
            color: darkgreen;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Power Calculator</h1>
        <form method="POST">
            {% csrf_token %}
            
            <label for="intensity">Intensity (I in Amps):</label>
            <input type="text" name="intensity" id="intensity" required>

            <label for="resistance">Resistance (R in Ohms):</label>
            <input type="text" name="resistance" id="resistance" required>

           
            <button type="submit">Calculate</button>
        </form>

        
        {% if power is not None %}
        <h2>Calculated Power: {{ power }} Watts</h2>
        {% endif %}
    </div>
</body>
</html>

views.py

from django.shortcuts import render

def power_calculator(request):
    power = None  

    if request.method == 'POST':
        
        intensity = request.POST.get('intensity')
        resistance = request.POST.get('resistance')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'mathapp/math.html', {'power': power})

    urls.py
                

            from django.contrib import admin
            from django.urls import path
            from mathapp import views

            urlpatterns = [
                path('admin/', admin.site.urls),
                path('', views.power_calculator, name='power_calculator'), 
            ]



---
# SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/d2ec01ae-c965-41fa-b157-4d8aaecdfa9f)


# HOMEPAGE:
![image](https://github.com/user-attachments/assets/454fec82-297b-4231-9448-5feed7fe4db8)

# RESULT:
The program for performing server side processing is completed successfully.
