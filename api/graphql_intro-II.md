# Understanding GraphQL - Part II

In our last article, we talked about the origins of GraphQL and basic concepts 
related to it.

Today we will refresh the last content and we will learn a few new things putting 
hand on practice through a project built using Python 3, Ariadne, Flask, SQLAlchemy
and MySQL.

## The project
The source code for this project can be found [here](https://github.com/kno3comma14/graphql_tutorial) 
and you are free to clone, fork and share the project for any purpose. 

This is a project thought as a guide to understand a little bit of GraphQL, so we will need
a few requisites listed below:
- **Python 3.8.6** or superior: Our programming language.
- **Pip**: We need this to install Pipenv.
- **Pipenv**: Using Pipenv we will install all the required dependencies for the project.
- **MySQL**: We will need to create a MySQL schema and optionally use any MySQL client to interact with this RDBMS.

The dependencies required for this project include:
- **Ariadne**: Library used to implement GraphQL APIs
- **SQLAlchemy**: This is an easy to use but powerful ORM.
- **Flask**: We are using it to deal with our request - response life-cycle.

#### Structure
Our [graphql_tutorial](https://github.com/kno3comma14/graphql_tutorial) project has the structure shown
in the image below:
![Project Structure](../resources/project_structure.png)

Let's talk about the most relevant components included in this structure:

- Pipfile: This is used by Pipenv to manage the dependencies included in the project.
- main.py: The entrypoint of the project
- schema.graphql: This file contains the definitions of all the types used in our GraphQL API. We will
learn more about the structure of this file in future sections of this post. 
- api/models.py: In this module we have the classes that describe the data to be mapped between our code and 
our database.
- api/queries.py: This module contains the query operations from our graphql api.
- api/mutations.py: mutations module contains the query operations from our GraphQL API.
- api/__init__.py: Contains the base configuration needed by out project.


## Going back to the concepts
In the last section of this posts, we read about two new concepts from GraphQL, queries and mutations. Let's define
these concepts so we can improve the understanding of the project.

#### Queries
At GraphQL queries are the way that we use to collect data from our API. This is one of the most important feature of
GraphQL so we really need to understand it. In this post, we will try to explain queries using the schema.graphql as support.

First, we need to define the queries using the type syntax we saw in the last post:

```graphql
type Query {
  wallets: WalletsResult!
  wallet(walletId: ID!): WalletResult!
}
```

In this code we are creating a Query type with ```type Query``` notation, so GraphQL will know where to find our query operations. Inside
this type we have two fields: ```wallets``` and ```wallet```. These fields are the name of our query operations. 

As we can see, ```wallets``` operation will return a ```WalletsResult``` type and ```wallet``` will return a ```WalletResult```, let's
look at the definition of these two types:

```graphql
type WalletResult {
  success: Boolean!
  errors: [String]
  wallet: Wallet
}

type WalletsResult {
  success: Boolean!
  errors: [String]
  wallets: [Wallet]
}
```

These two types are similar but ```WalletResult``` will receive only one ```Wallet``` object and ```WalletsResult``` will receive an array of ```Wallet```
as base type. Now, we are talking about the ```Wallet``` type, so let's take a look:

```graphql
type Wallet {
  id: ID!
  name: String!
  currency(currency: CurrencyUnit = USD): String!
  coins: [Coin]
}
```

To wrap all this explanation, we have to see this like a design process defined as: 
```create "domain" types``` => ```create "result" types``` => ```create "representation"types```

This process is pretty similar to the process used to develop our applications.

To end this section, please remember that query types are used to fetch some data, filter it, etc. For other operations such as create, modify 
or destroy data we will use **Mutations**. 

#### Mutations
TODO
