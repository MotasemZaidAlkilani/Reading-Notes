# espresso 

## AWS Amplify
is a powerful toolkit developers use to build full stack applications that directly integrate with the cloud. Using it, developers can rapidly setup, test, launch, and scale production ready applications with minimal time spent focusing on the details.

-note :use AWS Amplify as a Command Line Interface or CLI tool

-note (one of feature):CloudFormation is an Infrastructure as Code service that allows you to define template files that instruct AWS which components you need for your application, and let AWS do the heavy lifting of provisioning those services.

_______________

##  An Example Of Amplify Features :

1- Authentication (Amazon Cognatio)  

2-DataStore(Amazon DynamoDB)          

3-Functions(Aws Lambda)

4-Storage(Amazon Simple Storage)

5-Custom Domainess(Amazon Route)

6-PobSub(Amazon Simple Notification)

7-analytics(amazon pinpoint)

_______________
## there is two way to interact with Amplify?

### 1-Command Line Interface (CLI)

-note :A critical component for almost any application is a api. To add one, we use the command amplify add api to provision our new api
our API including technology (graphql or REST/HTTP), name, API keys.


### 2-Admin UI

-note : he Admin UI does have some neat features such as the Data Model Studio. Using it, you can easily add Data Models including their fields and types

-note :you can add relationships between them similar to building out an ER diagram for a database schema

-note :The cool part is that Amplify will generate model files that you can use in your application code

-note :defining relationships between models, Amplify will automatically generate the correct database indexes to support relationship style lookup patterns.

____________
## Pros Amplify

Pro # 1 – Getting Started Quickly

Pro # 2 – Fast Development Cycles
Since Amplify is CLI based, it allows for some very fast development cycles. Developers can take advantage of the toolkit to rapidly experiment with new changes and deploy them out to the cloud

Pro # 3 – Shielding From the Complexity of AWS
Amplify flips this problem on its head. Instead of starting with a problem, and trying to figure out which service(s) to solve that problem, Amplify offers a solution oriented mindset

__________
## Cons Amplify

Con # 1 – You Don’t ‘Really’ Learn AWS
you’re probably not gonna learn how to use AWS, you’re just going to learn how to use amplify.

Con # 2 – Collaboration Can Be Frustrating

Con # 3 – Stepping Outside The Box
One of the problems with Amplify is that you’re kind of at the mercy of the product features offered through AWS Amplify. If theres a particular AWS service that you’re interested in using in your Amplify project and its not supported, you may need to manage it separately

Con #4 – Potential For Surprise Bills

_________
