# Understanding and using GraphQL

When we are designing or implementing APIs, we can encounter with many flavours
such as SOAP, REST, WebSub, gRPC, etc. Today, I want to present you my favorite one
including a little bit of history, the reasons to exist, basic concepts 
and a practical demo about GraphQL.

### A little bit of GraphQL pre-history

In order to generate some context, I think I have to talk about the software development industry at 2011-2012 period.

These years we were enjoying a great number of web applications, but at the same time we were witnesses of the shifting
process of the software development industry to mobile application development. 

The facebook(creators of **GraphQL**) web application had a huge success, so people started using mobile browsers to enter 
into the application. The problem was the mobile browsers were being buggy and slower, so the user experience was 
really bad. The solution? Start with the development of a mobile application using native technologies.

This solution proposed by facebook was a great idea at comercial level, but what about the technical sight?

##### The chaos started!

The api made by facebook was built thinking about the existent web technologies at 2011. These times, when we pressed a button
in the web application the browser had to fetch one or two resources from the api, but when the native development started for
mobile application they figured that they needed more than one or two resources, because a bunch of logic had to be made in
the client layer to resolve connectivity and speed problems inherited from the connection quality of these years. For this reason,
the traditional api exposed by facebook  wasn't supporting the new mobile application.

##### SuperGraph to the rescue!

In order to solve this problem, **Nick Schrock** started a prototype named *SuperGraph*.

*SuperGraph* was thought as a new engine that maps directly to entities and entity queries. In this way, the client(mobile application) 
could create queries and get the needed entities efficiently. To help with the development process of *SuperGraph*, Lee Byron, Dan Schafer and
other started a team and finally renamed *SuperGraph* to **GraphQL**.

### GraphQL - Format concepts

At this point, I think we are clear about the beginings and the reason to exist to GraphQL, so let start with some important concepts.

##### GraphQL
**GraphQL** is a query language with a type system to define our entities and it provides a server runtime for executing queries over these 
entities. In this way, the entities are backed by the application needs and they are not tied with any source of data.


