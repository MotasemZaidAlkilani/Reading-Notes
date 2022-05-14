# Spring Authorization
Each app can be imported into an IDE. You can run the main method in SocialApplication to start an app.
They all come up with a home page on http://localhost:8080

You can also run all the apps on the command line using mvn spring-boot:run or 
by building the jar file and running it with mvn package and java -jar target/*.jar


>The apps all work on localhost:8080 because they’ll use OAuth 2.0 clients registered with GitHub and Google for that address.
To run them on a different host or port, you need to register your apps that way. There is no danger of leaking your credentials beyond localhost
if you use the default values. But, be careful what you expose on the Internet, and don’t put your own app registrations in public source control.

- how to make spring application with Authorization?

**1-Creating a New Project**

**2-Add a Home Page**

create index.html ,and do some styling using css nad js .

**3-Securing the Application with GitHub and Spring Security**

add Spring Security as a dependency. Since you’re wanting to do a "social" login

By adding that, it will secure your app with OAuth 2.0 by default.

**4-Add a New GitHub App**

lect "New OAuth App" and then the "Register a new OAuth application" page is presented. Enter an app name and description.
Then, enter your app’s home page, which should be http://localhost:8080, in this case. Finally,
indicate the Authorization callback URL as http://localhost:8080/login/oauth2/code/github and click Register Application

**5-Boot Up the Application**

With that change, you can run your app again and visit the home page at http://localhost:8080. Now,
instead of the home page, you should be redirected to login with GitHub. If you do that, 
and accept any authorizations you are asked to make, you will be redirected back to the local app, and the home page will be visible.

**6-The /user Endpoint**

Now, you’ll add the server-side endpoint just mentioned, calling it /user. It will send back the currently logged-in user,

**7-Making the Home Page Public**

witch off the security on the home page by extending WebSecurityConfigurerAdapter

**8-Add a Logout Button**

this section, we modify the click app we built by adding a button that allows the user to log out of the app. This seems like a simple feature,
but it requires a bit of care to implement


**9-Adding a Logout Endpoint**

Spring Security has built in support for a /logout endpoint which will do the right thing for us

**10-Login with GitHub**

-Initial setup

-Setting the redirect URI

-Adding the Client Registration

-Adding the Login Link

**11-Adding an Error Page for Unauthenticated Users**

-Adding an Error Message
