# Understanding GraphQL

When we are designing or implementing APIs, we can encounter with many flavors
such as SOAP, REST, WebSub, gRPC, etc. Today, I want to present you my favorite one
including a little bit of history, the reasons to exist, and the basic concepts. 

## A little bit of GraphQL pre-history

To generate some context, I think I have to talk about the software development industry in the 2011-2012 period.

These years we were enjoying a great number of web applications, but at the same time we were witnesses the shifting
process of the software development industry to mobile application development. 

The Facebook(creators of **GraphQL**) web application had a huge success, so people started using mobile browsers to enter into the application. The problem was the mobile browsers were being buggy and slower, so the user experience was really bad. The solution? Start with the development of a mobile application using native technologies.

This solution proposed by Facebook was a great idea at the comercial level, but what about the technical sight?

#### The chaos started!

The API made by facebook was built thinking about the existent web technologies in 2011. These times, when we pressed a button
in the web application the browser had to fetch one or two resources from the API, but when the native development started for
the mobile application they figured that they needed more than one or two resources because a bunch of logic had to be made in
the client layer to resolve connectivity and speed problems inherited from the connection quality of these years. For this reason,
the traditional API exposed by Facebook wasn't supporting the new mobile application.

#### SuperGraph to the rescue!
To solve this problem, **Nick Schrock** started a prototype named *SuperGraph*.

*SuperGraph* was thought of as a new engine that maps directly to entities and entity queries. In this way, the client(mobile application) 
could create queries and get the needed entities efficiently. To help with the development process of *SuperGraph*, Lee Byron, Dan Schafer, and
others started a team and finally renamed *SuperGraph* to **GraphQL**.

## GraphQL - Concepts
At this point, I think we are clear about the beginnings and the reason to exist to GraphQL, so let start with some important concepts.

#### GraphQL
**GraphQL** is a query language with a type system to define our entities and it provides a server runtime for executing queries over these entities. 
In this way, the entities are backed by the application needs and they are not tied with any source of data.

#### How to create types in GraphQL?
In the hearth of GraphQL, we can create types, these types represent objects that live inside your services and the description of their fields. 
Let see something to be expressed as a type:

```graphql
type Car {
  model: String!
  manufacturer: String!
  features: [Feature!]!
}
```

Easy right? I know, it's pretty obvious to read and interpret but let's create a formal language to improve our communication:
- ```Car```: a GraphQL Object Type, in simple language this is a name associated to a set of fields. 
- ```model```, ```manufacturer``` and ```features```: these are fields that belong to the Car Type.
- ```String```: This is a built-in type or scalar type in GraphQL world.
- ```String!``` or ```<general_type>!```: the exclamation mark here represent a non-nullable field.
- ```[Feature!]!```: This one is a combination of all properties mentioned until now. The brackets represent an array of Feature
objects. This field is non-nullable as well and it will contain non-nullable feature objects.

#### Arguments
At the moment we know the basic structure of GraphQL types, but there is a particular feature named arguments that we need to 
understand to enrich our types. Let's see an example:

```graphql
enum VelocityUnit {
	MILE_PER_HOUR,
	KM_PER_HOUR
}

type Car {
  model: String!
  manufacturer: String!
  features: [Feature!]!
  maximumVelocity(unit: VelocityUnit = MILE_PER_HOUR): Float
}
```

First of all, we have to keep in mind that every field in GraphQL can have zero or more arguments. In this case our field ```maximumVelocity```
has an argument **named** unit and it has to be passed by name. The unit argument can be required or optional using the **!** indicator and
we can define a default value for it, in this case, the default value of unit is the ```VelocityUnit``` enum value ```MILE```. 
(We will talk about enum values in the next section of this post). 

Arguments can be used to enrich the behavior of our application using their values. For example, the type ```Car``` mentioned before, can be
presented in a query depending on the unit presented in the query so, if we use a value different to MILE_PER_HOUR(ex. KM_PER_HOUR) the
maximumVelocity field will be presented differently.

#### Enum types
In the ```Car``` type we introduced a new type named ```VelocityUnit```, which assigns a set of values to a type name. Let's review again the
```VelocityUnit type```:


```graphql
enum VelocityUnit {
	MILE_PER_HOUR,
	KM_PER_HOUR
}
```

The set of values are **MILE_PER_HOUR**, **KM_PER_HOUR**, so this means that we have to use exactly one of these two values. We will cover these
enum types in practice in the next post, where we will be building some queries over types with enumerations.

## Summary
We talked about the pre-history of GraphQL to understand the implications of this technology in the industry and we studied a little part of its
type system evaluating basic concepts. For the next part of this post, we will put our hands-on practice to take these basic concepts to action.
We will learn how to create a GraphQL API(Using Python, Flask, and Ariadne), we will create types to apply the concepts we already learned and concepts 
and definitions that we will clarify in practice.

I hope you enjoyed the reading and please contact me for any comment.

Happy hacking!















