# Serverless and Amplify

-Serverless is a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers. A serverless application runs in stateless compute containers that are event-triggered, ephemeral (may last for one invocation), and fully managed by the cloud provider.


-Pricing is based on the number of executions rather than pre-purchased compute capacity, isn’t it the ideal framework for that project you have been planning since a long time? Well, go ahead do it.

-AWS offers technologies for running code, managing data, and integrating applications, all without managing servers. Serverless technologies feature automatic scaling, built-in high availability, and a pay-for-use billing model to increase agility and optimize costs. 

-These technologies also eliminate infrastructure management tasks like capacity provisioning and patching, so you can focus on writing code that serves your customers. Serverless applications start with AWS Lambda, an event-driven compute service natively integrated with over 200 AWS services and software as a service (SaaS) applications.

-note :Serverless applications are event-driven cloud-based systems where application development rely solely on a combination of third-party services, client-side logic and cloud-hosted remote procedure calls (Functions as a Service)

- the advantages of Serverless Architecture are the price ,3rd Party Dependencies,Environments,Timeout,Scale.

-note :The downside is that Serverless functions are accessed only as private APIs. To access these you must set up an API Gateway. This doesn’t have an impact on your pricing or process

___________
## Functions as a Service (FaaS)
an implementation of Serverless architectures where engineers can deploy an individual function or a piece of business logic. They start within milliseconds (~100ms for AWS Lambda) and process individual requests within a 300-second timeout imposed by most cloud vendors.

-Principles of FaaS:

1-Complete management of servers

2-Invocation based billing

3-Event-driven and instantaneously scalable

### Key properties of FaaS:

1-Independent, server-side, logical functions

2-Stateless

3-Ephemeral

4-Event-triggered

5-Scalable by default

6-Fully managed by a Cloud vendor

___________
### Benefits of Serverless Architecture:
1-Reduced liability, no backend infrastructure to be responsible for.

2-Zero system administration.

3-Easier operational management.

4-Fosters adoption of Nanoservices, Microservices, SOA Principles.

5-Faster set up.

6-Scalable, no need to worry about the number of concurrent requests.

7-Monitoring out of the box.

8-Fosters innovation.

_______________________
### Benefits of Serverless Architecture:

1-Immature technology results in component fragmentation, unclear best-practices.

2-Architectural complexity.

3-The discipline required against function sprawl.

4-Multi-tenancy means it’s technically possible that neighbour functions could hog the system resources behind the scenes.

5-Testing locally becomes tricky.

6-Significant restrictions on the local state.

7-Execution duration is capped.

8-Lack of operational tools

________________
