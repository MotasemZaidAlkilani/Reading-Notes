# AUTHENTICATION
the amplify auth category provides an interface for authenticating a user. The Amplify CLI helps you to create and configure the auth category with an authentication provider .

## Prerequisites 
android application with aleast android sdk api level 16

_____

## Configure Auth Category 
go to the project directory , write this command :

```
amplify add auth

```
then enter the following :

```
Q1:

'Default configuration'

Q2:

'Username'

Q3:

'No,I am done.'

```

and to push it , write this one:

```
amplify push

```
_____

## Install Amplify Libraries 
In build gradle add the following :

```
dependencies {
    implementation 'com.amplifyframework:aws-auth-cognito:1.35.4'
    }
```
## Initialize Amplify Auth
```
Amplify.addPlugin(new AWSCognitoAuthPlugin());
Amplify.configure(getApplicationContext());

```

## Check the current auth session 
run this in the mainActivity :

```
Amplify.Auth.fetchAuthSession(
      result -> Log.i("AmplifyQuickstart",result.toString()),
      error -> Log.e("AmplifyQuickstart",error.toString());
 ```
 
 _________________
 
# Sign in 
The auth category can be used to register a user , confirm attributes like email/phone , sign in with optional multi0factor authentication.

## Register a user 
The default CLI flow requires a username , password and valid email id as parameters to register a user :

```
AuthSignUpOPtions options=AuthSignUpOptions.builder()
           .userAttribute(AuthUserAttributeKey.email,"my@gmail.com").build();
           
Amplify.Auth.signUp("username","Password123",options ,
           result -> Log.i("AuthQuickStart","Result :"+result.toString()),
           error -> Log.e("AuthQuickStart","sign up failed ",error)
 ```
 
next step in the sign up flow is to confirm the user. A confirmation code will be sent to the email id provided during sign up. Enter the confirmation code received via email in the confirmSignUp call.

```
Amplify.Auth.confirmSignup(
     "username" ,
     "the code you received via email",
     result -> Log.i("AuthQuickstart",result.isSignUpComplete() ? "confirm signup succeeded" : "Confirm sign up not complete"),
     error -> Log.e("AuthQuickStart",error.toString()));
     
 ```
 
 ## Sign in a user 
 
 ```
 Amplify.Auth.signIn(
   "username",
    "password",
    result -> Log.i("AuthQuickstart",result.isSignInComplete() ? "sign in succeeded" : "sign in not complete"),
    error -> Log.e("AuthQuickdstart",error.toString()));
    
 ```
 __________
           


 
 
      


