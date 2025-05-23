# Bus Reservation System Project in Django with Source Code

**Bus Reservation System Project in Python Django** is a fairly simple system written in Django, SQLLite3, and Python that is intended to automate the purchase of online tickets through an easy online bus booking system.

You can manage/book reservations, client info, and passenger lists with the bus ticket reservation system’s Django admin, and book tickets easily via the Bus reservation Website.

>[!NOTE]
>To start creating a Bus Reservation System Project in Django, make sure that you have PyCharm Professional IDE Installed in your computer.

## Admin Features of Bus Reservation System Project in Django

* **User**

For the user, the admin can add, update, and delete user information and also the admin can change the password of the user.

* **Manage Booking**

For the booking, the admin can add, update, and delete booking information.

* **Manage Bus**

For the bus, the admin can add, update, and delete booking information.

## User Features of Bus Reservation System Project in Django

* **Log in**

For the login, the user will log in first before he/she can use the system.

* **Sign up**

For the sign-up, the user will sign up first before he/she can use it to log in to the system.

* **Homepage**

For the homepage, you will be able to all the basic access in the whole system. Such as home, find the bus, see the booking, and log in.

* **Search Bus**

For the search bus, the user will be able to search the available bus.

* **View Booking**

For the view booking, the user will be able to view the booking details.

* **Cancel Booking**

For the canceled booking, the user will be able to cancel their booking.


## How to Create a Bus Reservation System Project in Django?

Here are the steps on How to create a **Bus Reservation System Project in Django** with Source Code.

1. **Open file**.

First, open “pycharm professional” after that click “file” and click “new project”.

![image](https://github.com/user-attachments/assets/ab20276e-60d1-47e0-b09d-95350583f0b3)

2. **Choose Django**.

Next, after clicking “new project”, choose “Django” and click.

![image](https://github.com/user-attachments/assets/c312a66a-b2ce-42a6-bfc5-ad12abea7d6c)


3. **Select the file location**.

Then, select a file location wherever you want.

![image](https://github.com/user-attachments/assets/c77d2b32-ff5d-483a-8511-dbf25bbc9f6a)

4. **Create an application name**.

After that, name your application.

![image](https://github.com/user-attachments/assets/89b050d8-cc09-4773-b79f-c876b2153662)

5. **Click Create**.

Lastly, finish creating the project by clicking the “create” button.

![image](https://github.com/user-attachments/assets/cc2c5486-937f-435f-b22f-5a0526610128)


6. Start Coding.

Finally, we will now start adding functionality to our Django Framework by adding some functional codes.

### These are the codes to add functionality for the Bus Reservation System Project in Django With Source Code

* Create the template for the homepage in the Bus Reservation System Project in Django With Source Code.

In this section, we will learn how to create templates for the homepage. 

To start with, add the following code in your base.html under the folder of myapp/templates/myapp files.

```
<!doctype html>
<html lang="en">
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css"
          integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">

    <title>Bus Reservation System</title>
</head>
<body>
<nav class="navbar navbar-expand-lg navbar-light bg-success">
    <div class="container">
        <a class="navbar-brand" href="#" style="color: white;">Vallacar Transit Incorporated</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup"
                aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
            <div class="navbar-nav" >
                <a class="nav-item nav-link active" href="{% url 'home' %}" style="color: white;">Home <span class="sr-only">(current)</span></a>
                <a class="nav-item nav-link" href="{% url 'findbus' %}" style="color: white;">Find Bus</a>
                <a class="nav-item nav-link" href="{% url 'seebookings' %}" style="color: white;">See Bookings</a>
                {% if request.user.is_active %}
                <a class="nav-item nav-link " href="{% url 'signout' %}" style="color: white;">Sign out</a>
                {% else %}
                <a class="nav-item nav-link " href="{% url 'signup' %}" style="color: white;">Sign Up</a>
                {% endif %}


            </div>
        </div>
    </div>
</nav>
{% block content %}
{% endblock %}
<!-- Optional JavaScript -->
<!-- jQuery first, then Popper.js, then Bootstrap JS -->
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo"
        crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"
        integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49"
        crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js"
        integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy"
        crossorigin="anonymous"></script>
</body>
</html>
```

* Create a template for the billing in the Bus Reservation System Project in Django With Source Code.

In this section, we will learn how to create templates for billing.

To start with, add the following code in your bookings.html under the folder of myapp/templates/myapp files.

```
{% extends 'myapp/base.html' %}
{% block content %}
<h2>Booking Confirmation</h2>
<form action="{% url 'home' %}" method="post">

    {% csrf_token %}
    <h2>Your booking has been confirmed!</h2>
    <h2>Thank you!</h2>
    <h3>Bill details</h3>
    <!-- Button to Open the Modal -->
    <button type="button" class="btn btn-success" data-toggle="modal" data-target="#myModal">
        Bill details
    </button>

    <!-- The Modal -->
    <div class="modal" id="myModal">
        <div class="modal-dialog">
            <div class="modal-content">

                <!-- Modal Header -->
                <div class="modal-header">
                    <h4 class="modal-title">Modal Heading</h4>
                    <button type="button" class="close" data-dismiss="modal">&times;</button>
                </div>

                <!-- Modal body -->
                <div class="modal-body">
                    <ul class="list-group list-group-flush">
                        <li class="list-group-item"><b>Bus name:</b> {{book.bus_name}}</li>
                        <li class="list-group-item"><b>Starting point:</b> {{book.source}}</li>
                        <li class="list-group-item"><b>Destination point:</b> {{book.dest}}</li>
                        <li class="list-group-item"><b>Number of seats:</b> {{book.nos}}</li>
                        <li class="list-group-item"><b>Price:</b> {{book.price}}</li>
                        <li class="list-group-item"><b>Cost:</b> {{cost}}</li>
                        <li class="list-group-item"><b>Date:</b> {{book.date}}</li>
                        <li class="list-group-item"><b>Time:</b> {{book.time}}</li>
                    </ul>


                </div>

                <!-- Modal footer -->
                <div class="modal-footer">
                    <button type="button" class="btn btn-success" data-dismiss="modal">Close</button>
                </div>

            </div>
        </div>
    </div>

    <div class="pull-right">
        <button type="submit" class="btn btn-primary float-right">OK</button>
    </div>


</form>


{% endblock %}
```

* Create a template for the booking list

In this section, we will learn how to create templates for the booking list. 
To start with, add the following code in your bookinglist.html under the folder of myapp/templates/myapp files.

```
{% extends 'myapp/base.html' %}
{% block content %}
<h3>{{msg}}</h3>
<h2>List of buses</h2>
<table class="table table-striped">
    <thead style="background-color: blue;color: white;">
    <td>BOOKING ID</td>
    <td>USER NAME</td>
    <td>BUS NAME</td>
    <td>SOURCE</td>
    <td>DESTINATION</td>
    <td>NUM OF SEATS</td>
    <td>PRICE</td>
    <td>DATE</td>
    <td>TIME</td>
    <td>STATUS</td>


    </thead>

    {% for row in book_list %}
    <tr>
        <td>{{row.id}}</td>
        <td>{{row.name}}</td>
        <td>{{row.bus_name}}</td>
        <td>{{row.source}}</td>
        <td>{{row.dest}}</td>
        <td>{{row.nos}}</td>
        <td>{{row.price}}</td>
        <td>{{row.date}}</td>
        <td>{{row.time}}</td>
        <td>{{row.status}}</td>


    </tr>
    {% endfor %}
</table>
<form action="{% url 'cancellings' %}" method="post">
    <h3>Choose bus to book</h3>
    {% csrf_token %}
    <div class="col-auto">
        <label for="example-email-input" class="col-2 col-form-label">Bus ID</label>
        <div class="col-5">
            <input name='bus_id' class="form-control" type="number" id="example-email-input">
        </div>
    </div>

    <br>
    <br>
    <div class="pull-right">
        <button type="submit" class="btn btn-danger float-left">Cancel bus</button>
    </div>


    {{error}}

</form>

{% endblock %}
```

### 📌Here's the full documentation for the [Bus Reservation System Project in Django](https://itsourcecode.com/free-projects/python-projects/bus-reservation-system-project-in-django-with-source-code/)
