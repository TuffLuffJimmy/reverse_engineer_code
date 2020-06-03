# reverse_engineer_code

# WHAT IS HAPPENING

## SERVER
upon reaching the website user is greeted with a login page sent by the server.

### HOW
server.js is connected on the backend to a database through a file called models. Packages called "passport" are used for authentication and bring in backend functionality. Express is brought in for initializing middleware. And sequelize is used to simplify requests to the sql database.

## LOGIN
user is taken to a login page with two text fields for email address and password for authentication. User can also sign up if they do not have an account.

### HOW
when login button is pressed event listener requests inputs for email and password and checks if data is input, if not return is called. If there is input the data is sent to a loginUser function and reset the two input fields. loginUser fires a post request sending an object with email and password, then opens the /members page.

## SIGNUP
sign up page is very similar to the login page, users can use the two text fields to sign up for a new account, or click the link to take them back to the login page.

### HOW
Very simiar to LOGIN page however the post request is actually sent to a signup route.

## MEMBERS
returns member page that includes email.

### HOW
a get request is sent to the user_data route which presumably returns the email from the database.
---
---
---

server.js - dependant on express, express-session, the local file passport. Initializes server using express. Creates public static folder. Initializes all middleware.

# config folder
config.json - connection details for three different databases: development, testing, production.
passport.js - dependant on passport and passport-local modules. creates a constructor including functions to test email and password veracity. and exports constructor.

# middlware folder
---
inside config folder
---
isAuthenticated.js - restricts access to users if they are not logged in. Users are only allowed on the login page at /

# models folder
index.js - brings in many modules. exports db
user.js - requires bcryptjs and uses this to hash passwords so they are not stored in plain text. prototypes this.

# public folder
login.html, members.html, signup.html - html for login, members, and signup
---
inside js folder
---
login.js, members.js, signup.js - uses forms to receive user input, the actual shape of the page the user sees.

# stylesheets folder
style.css - formatting for all pages

# routes folder
api-routes.js - dependant on models folder and passort constructor with functions. takes in an app as argument. passes password and email requests through route to passport functiosn and returns status or redirects.
html-routes.js - paths that determine url requests and what is served to user.
