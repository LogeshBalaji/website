# Ex.07 Restaurant Website
# Date: 26.11.2024
# AIM:
To develop a static Restaurant website to display the food items and services provided by them.

# DESIGN STEPS:
## Step 1:
Requirement collection.

## Step 2:
Creating the layout using HTML and CSS.

## Step 3:
Updating the sample content.

## Step 4:
Choose the appropriate style and color scheme.

## Step 5:
Validate the layout in various browsers.

## Step 6:
Validate the HTML code.

## Step 7:
Publish the website in the given URL.

# PROGRAM:
## urls.py(server1) 
~~~
from django.urls import path  

from.import views  

urlpatterns=[  
    path('',views.home,name='home')  
]
~~~ 
## views.py(server1)  
~~~
from django.shortcuts import render    
from django.http import HttpResponse  
#Create your views here.  

def home(request):  
    return render(request, 'home.html') 
content="""
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Restaurant Website</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            background-color: #f4f4f4;
            color: #333;
        }
        header {
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }

        header h1 {
            margin-bottom: 10px;
        }

        nav {
            display: flex;
            justify-content: center;
            margin-top: 10px;
        }

        nav a {
            color: white;
            text-decoration: none;
            padding: 10px 20px;
            margin: 0 15px;
            font-size: 18px;
        }

        nav a:hover {
            background-color: #575757;
            border-radius: 5px;
        }
        section {
            padding: 40px 20px;
            text-align: center;
        }

        section h2 {
            margin-bottom: 20px;
            font-size: 2em;
        }

        .menu-item {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
        }

        .menu-item div {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 250px;
        }

        .menu-item img {
            width: 100%;
            border-radius: 5px;
        }

        .menu-item h3 {
            margin-top: 15px;
            font-size: 1.5em;
        }

        .menu-item p {
            color: #777;
            font-size: 1em;
        }
        .about {
            background-color: #333;
            color: white;
            padding: 40px 20px;
        }

        .about p {
            font-size: 1.2em;
            line-height: 1.6;
            max-width: 800px;
            margin: 0 auto;
        }
        .contact {
            padding: 40px 20px;
            background-color: #fff;
        }

        .contact h2 {
            margin-bottom: 20px;
        }

        .contact form {
            display: flex;
            flex-direction: column;
            max-width: 500px;
            margin: 0 auto;
        }

        .contact input, .contact textarea {
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }

        .contact button {
            background-color: #333;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1em;
            cursor: pointer;
            border-radius: 5px;
        }

        .contact button:hover {
            background-color: #575757;
        }
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px;
        }
    </style>
</head>
<body>
    <header>
        <h1>TAJ Restaurant</h1>
        <nav>
            <a href="#menu">Menu</a>
            <a href="#about">About Us</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>
    <section id="menu">
        <h2>Our Menu</h2>
        <div class="menu-item">
            <div>
                <img src="sagati.jpg" alt="Dish 1">
                <h3>Pasta Alfredo</h3>
                <p>Delicious creamy pasta with parmesan cheese.</p>
            </div>
            <div>
                <img src="gill.jpg" alt="Dish 2">
                <h3>Grilled Steak</h3>
                <p>Juicy grilled steak served with a side of vegetables.</p>
            </div>
            <div>
                <img src="magarith.jpg" alt="Dish 3">
                <h3>Margherita Pizza</h3>
                <p>Classic pizza with mozzarella, basil, and tomato.</p>
            </div>
        </div>
    </section>
    <section id="about" class="about">
        <h2>About Us</h2>
            <h2>Gallery</h2>
            <img src="image1.jpg" width="475px" alt="Gallery image 1" />
            <img src="image2.jpg" width="500px" alt="Gallery image 2" />
            <img src="image3.jpg" width="500px" alt="Gallery image 3" />
        <p>At TAJ Restaurant, we serve a variety of mouth-watering dishes, crafted with the freshest ingredients. Our chefs are passionate about creating exceptional culinary experiences, and we are committed to providing top-notch service in a comfortable and welcoming environment. Whether you're here for a casual meal with friends or celebrating a special occasion, we strive to make every visit memorable.</p>
    </section>
    <section id="contact" class="contact">
        <h2>Contact Us</h2>
        <form action="#">
            <input type="text" placeholder="Your Name" required>
            <input type="email" placeholder="Your Email" required>
            <textarea rows="5" placeholder="Your Message" required></textarea>
            <button type="submit">Send Message</button>
        </form>
    </section>
    <footer>
        <p>&copy; 2024 TAJ Restaurant | All Rights Reserved</p>
        <p><a href="policy/privacy-policy.html">Privacy Policy</a> | <a href="t&c.html">Terms of Service</a></p>
    </footer>

</body>
</html>
    """
 class Myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode())
print("This is my webserver")
server_address =('',8000)
Httpd = HTTPServer(server_address,Myserver)
Httpd.serve_forever()
~~~   
## urls.py(server)
~~~
from django.contrib import admin  
from django.urls import path,include  

urlpatterns = [  
    path('', include('server1.urls')),  
    path('admin/', admin.site.urls),  
]
~~~
# OUTPUT:
![Screenshot 2024-12-06 111757](https://github.com/user-attachments/assets/c68b108d-a69b-40c8-8e7b-a64606101312)


## WEBSITE 

![Screenshot 2024-12-06 105702](https://github.com/user-attachments/assets/4b9b442c-6722-4dc5-bffc-7e17d94ad7df)

![Screenshot 2024-12-06 105651](https://github.com/user-attachments/assets/76bf69e0-2e94-47fa-83f0-9499026dbc95)

![Screenshot 2024-12-06 105634](https://github.com/user-attachments/assets/cfaf76c6-346c-4164-908d-4af84996127a)

# RESULT:
The program for designing software company website using HTML and CSS is completed successfully.
