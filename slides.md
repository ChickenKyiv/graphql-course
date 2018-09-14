
---




Hi,

Here are the notes I have been taking for the different chapters in the basic lesson. I learned a lot about GraphQL. Specifically, what GraphQL is, the types of operations (queries, mutations, and subscriptions) that are used, how the schema is structured, and the processes that occur in the background to properly process client requests to the server and GraphQL.

GraphQL Chapters:










---




---



Advanced Tutorial - Clients
This chapter discusses the infrastructure features as well as the client benefits for using GraphQL. It discusses two specific clients - Apollo Client and Relay which are the current GraphQL mainstays. Utilizing these with GraphQL leads to a variety of benefits such as fetching and updating data in a more declarative manner, normalizing data as it caches it and allows UI code and data requirements to work side by side are a few of these benefits.



Advanced Tutorial - Servers
The use of servers "enables server developer to focus on describing data available rather than implementing and optimizing specific endpoints." This is part of the efficiency of GraphQL. The ability to use the Execution Algorithm is key to this that and the resolvers utilized. In addition, the batched resolving method makes this the most efficient way to send for queries and obtain data to date.



More GraphQL Concepts
The chapter helped define areas that will be utilized throughout GraphQL. Some of the areas highlighted were those concerning fragments, arguments, aliases, object and scaler types, and enums. Each of these areas are present and useful in the finding the most efficient ways to use GraphQL. In addition, there are ways to use these so errors do not occur. I believe the most important aspect of this chapter, besides finding ways to avoid errors, was to understand that in each schema you develop you will need to define scaler and object types. This will be imperative to the GraphQL working as necessary.



Tooling & Ecosystem
I found the information in this chapter to be light but imperative for the overall success of using GraphQL. Introspection is the foundation of this chapter as well as that of utilizing GraphQL to it's greatest capabilities. The other aspect that is introduced and should be looked at more closely is GraphQL Playground which seems to be vital to the success of any project using GraphQL.



Security
Sadly none of the security measures are foolproof but by understanding them it is much easier to identify where you could use them and how they can help protect the server. The client is able to access the schema which is also a hindrance to the security of the API. But by understanding this it is easier to help protect your servers in the long run. After looking at timeout, max query depth, query complexity and throttling it seems that utilizing a variety of these techniques may be the most beneficial.



Common Questions & Pick a Tutorial
This section just reviewed some areas that most people had questions on, such as is GraphQL a database technology (it's not) and the discussion on server-side caching. All of these were quite reasonable and helped to tie up loose ends.
I do plan on moving on to the Apollo & React Tutorial which works on building a GraphQL as well.




---

Chapter 1: Intro (https://graphql.org/learn/)
"This chapter talks about how GraphQL service is created. Basically we first define types and then fields on those types. Also the datatype on each field is specified here. We also provide functions for each field on each type so that we can retrieve that data(, or do something with it). It also describes how to send a query to receive data, which is very simple and flexible way to do so."
s




Chapter 2: Queries and Mutation (https://graphql.org/learn/queries/)
1. Query: Learnt how to structure query in GraphQL. In a query we can traverse our data and specify the field whose data we need, and the response is very similar to our query(, it is the query with the required data). We can ask for any field types, including Objects too, and we can go inside them by using brackets{ } and specify the required fields.
2. Arguments: We can also pass arguments in the query for a field, to declaratively fetch data that is required.
3. Aliases: Used for querying the same field with different arguments. Quite clear with the example there.
4. Fragments: Cool feature, for modularising the query. Construct a set of fields, and then you can pass them into your query by ...fragmentName.
5. Operation types: Any action is an operation. Operation can be of types query, mutation and subscription. Operations have types and name.
6. Variables: variables can be also defined, for passing dynamic arguments in an operation. Variables can also be assigned default values.
7. Directives: Used for dynamically manipulating the structure of the query. Like you can include or exclude some field by adding conditional statement on variables.
8. Mutation: This is operation type for modifying data on the server. Cool thing is that you can query from the same data that you mutated. One thing is not clear however, in the example:
9. mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) { createReview(episode: $ep, review: $review) { stars commentary } }
10. Shouldn't it be something like:
11. mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) { createReview(episode: $ep, review: $review) { review { stars commentary } } }
12. Anyways I think things will get clear as I move on with it.
13. Inline Fragments: Useful for querying when we do not know the type that is going to return. We can ask for specific fields based on the types of the returned data.
14. Meta Fields: __typename can be used to determine to the type of the returned data, which can then be used to select what we want from the data.




Chapter 3: Schemas and Types (https://graphql.org/learn/schema/)
1. Type System: GraphQL has a strongly typed system, and we explicitly define types on each fieldof the objectin the schema definition. Types can be defined as in Object types using the typekeyword, or they can be built-in scalar types. By this, we can have an idea of what to expect when a query is made. Types are also needed for validation of the query.
2. Type Language: GraphQL has a uniques SDL(Schema Description Language) for describing schema of the GraphQL service.
3. Object types and fields: An object type can have fields inside it, where each field can have a scalar type as it's type or another object type as it's type. Basically this is the way of implementing relational databases.
4. Arguments: Every GraphQL field can have multiplearguments``, but they need to be explicitly passed by name. If an argument is optional we can assign a default value to it.
5. Query and Mutation types: Every service has a query type which defines the entry-point for the GraphQL query. It may or may not have a mutation type. Defined using typekeyword. Question: Can I only query data of fields for which I have a query type?
6. Scalar types: These are the leaves of the query, the fields that have these types do not have a sub-field. GraphQL has following scalar types: Int, String, Float, Boolean, ID. We can also specify custom scalar types, using scalarkeyword by doing scalar typeName
7. Enumeration types: Special types of scalars where you can define a set of allowed values. Anything other than that will be an error during validation We can use enum keyword to define an 'enum'.
8. Lists and Non-Null: While defining the type on a field, we can also apply type modifiers to extend our type. We can do String! to make the string type non-nullable. Once ! is added to the type, the server always expects a non-null value from that field. Second type modifier is List, where we can mark a field to return a list(kind of array) of values by wrapping [ ] around the type name.
9. Both type modifiers can be flexibly combined according to need. Like we can do Numbers : [Int!] to indicate the Numbers field is a list of Int values, where each entry in the list is a non-null object. Although the list can be null itself. Numbers: [Int]! means the list is non-null, but a member of a list can be null. Numbers : [Int!]! means neither the list nor any member on the list is null.
10. Interfaces: Interface is an abstract type, which includes a list of fields that an object type must include if it implements that interface, while that object type can have additional fields too. Similar to inheritance.
11. When a type inherits from an interface, then the fields on the interface can be directly accessed, but the object-specific fields must be accessed by using in-line fragment.
12. Union types: A type whose equivalent is an OR of specified types. This means an object of Union types can be either of the types in the description. For e.g. union Breakfast = Sandwiches | Omelet | Oats means that the union type Breakfast can be either of the types Sandwiches, Omelet or Oats. When querying union types, we should always use in-line fragments for each type(Sandwiches, Omelet, Oats) so that there is no error.
13. Input types: We can pass complex objects as type to a field. For this we first need to create those objects using the input keyword. Then we can start passing them. Useful for mutations, where we pass these input types to the object, we can even pass them as variables. Pretty cool! :)



Chapter 4: Validation(https://graphql.org/learn/validation/)
Validation is done using type system to determine whether a query is valid or not. So there are some rules that we need to follow.
There are a few rules that are mentioned in the documentation:
1. A fragment cannot refer to itself: As this would create a cycle, sort of recurrencebut there is no exit from it. So doing this will lead to an invalid query.
2. For e.g.
food {  
   ...details
   sameCuisine {
            ...details
            sameCuisine {
                  ...details
                 }
          }
   }

fragment details on foodItems {
name
cuisine
}

This valid query, but if we try to implement the same using a fragment like
fragment details on foodItems {
name
cuisine
...details
}

then it is invalid, as a fragment is calling itself.
1. When querying fields, only query for fields that are present in that type: Self explanatory, if we search for a field that is not present in the type, then it will be an error.
2. If the query returns something other than a scalaror enum, like an object type, then we need to specify which fields we want from that object. If we fail to do so the query is invalid. Question: What is the best practice in cases we need info of all fields? Do we make an enum?
3. If a field is scalar, we cannot query any fields inside it.
4. If our type implements an interface, then we can directly query only the fields on the interface. For querying type-specific fields, we can either use inline fragments or create a fragment on the type.



Chapter 5: Execution (https://graphql.org/learn/execution/)
GraphQL query is executed after Validation which resolves to a JSON response, generally.
Each field in a query has a corresponding resolver method which is a function that tells the service how to handle the query. This means it returns the type that is expected, and if that type is a scalartype, it would return the value. This completes the execution. A query always ends at the scalar type.
Root fields and resolver: Root type is the top level of the query. In the example given in the documentation, the root query has a resolver function human, which takes four arguments:
1. obj: The previous object, which we have to enter in order to resolve the query. This is not need for root resolver function.
2. args: The argument provided, for e.g. id, or name.
3. context: Haven't got much idea what this is, but I think we will get to know more about the details of this as we move along. Maybe it contains methods to fetch data, like getHumantById.
4. info: Containing field specific information and schema details.
Asynchronous Resolvers: The query does not always return data, but it returns a Promise, which can be passed around as a token even if we do not have the value yet, in hope that when the Promise is fulfilled, it will provide the data. During execution GraphQL waits for the Promises to resolve(or be rejected).
Trivial Resolvers: Trivial resolver is one that simply fetched the value of the field. Some libraries let us omit these trivial resolvers and do this for us by default.
Scalar Coercion: GraphQL can use scalars(or numbers) internally to store values of some objects. Once the query is made, the scalar is returned and the corresponding value to this scalar that is mapped can be returned.
List Resolvers: When a field type is a list, then GraphQL will return a list of Promises on that.
Producing the result: As the fields are resolved, the result is displayed in form of key-value pair(JSON) which looks like the query we requested.





---

Chapter 1: Intro (https://graphql.org/learn/)
Overview of what GraphQL is ( query language not tied to any specific database or storage ) and how to create a service in which wee need to define types and fields for those types and then provide function for each of those fields.
On receiving queries they are first checked to ensure they only refer to types and fields defined.
Questions: I don't really understand how the functions are associated a specific field but I guess i'll be explained further on.



Chapter 2: Queries and Mutations (https://graphql.org/learn/queries/)
Fields (https://graphql.org/learn/queries/#fields)
Essentially GraphQL is about asking for specific fields on objects. fields can be object and we decide what field of the object we want to fetch preventing overfetching and making it easy to get any specific field.
GraphQL queries look the same for both single items or lists of items, we know which one to expect based on what is indicated in the schema.
Questions: Is there any easy way to get all fields of a object instead of having to declare every field on the query ?
Arguments (https://graphql.org/learn/queries/#arguments)
Every field and nested object can get its own set of arguments, we can even pass arguments into scalar fields, to implement data transformations once on the server.
Aliases (https://graphql.org/learn/queries/#aliases)
The result object fields match the name of the field, if we want to query the same field multiple times with different parameters on the same request wee need these aliases to avoid object naming conflicts.
Fragments (https://graphql.org/learn/queries/#fragments)
A fragment is basically a reusable piece of query ( In GraphQL, is very common the need to query for the same data fields in different queries ).
Operation Name (https://graphql.org/learn/queries/#operation-name)
The operation type is either query, mutation, or subscription and describes what type of operation you're intending to do, it's mostly required
The operation name is a meaningful and explicit name for your operation, not always required but his use is encouraged becase it make easier debugging.


Variables (https://graphql.org/learn/queries/#variables)
In case parameters of our query are dynamic we use variables. In order to this variables to work we need to follow three steps:
* Replace the static value in the query with $variableName
* Declare $variableName as one of the variables accepted by the query
* Pass variableName: value in the separate, transport-specific (usually JSON) variables dictionary
Variables argumentes can be required by setting ! after type when we declare the variables accepted by our query: query HeroNameAndFriends($episode: Episode!)
Variables can also have a default values by adding the default value after the type declaration
Directives (https://graphql.org/learn/queries/#directives)
Directives are used to dynamically change the structure and shape of our queries using variables.
The core GraphQL specification includes exactly two directives:
* @include(if: Boolean)
* @skip(if: Boolean)

Mutations (https://graphql.org/learn/queries/#mutations)
Same as in REST Api where the convention is not to do any modification on GET requests, here in GraphQL there's a convention that any operations that cause writes should be sent explicitly via a mutation operation type.
Important detail -> mutation fields run in series, one after the other.
Inline Fragments (https://graphql.org/learn/queries/#inline-fragments)
We can use inline fragments in case a query field return multiple types with different fields between them and we want to retrieve different information depending on which type was returned.
Also there is a meta field called __typename which allow us to get at any point in a query name of the object type at that point.




---


Chapter 1: Introduction to GraphQL
GraphQL is a query language for APIs, developed and open-sourced by Facebook. It serves as an alternative to REST, but way better in terms of its power, efficiency, and flexibility.
Due to an increase in the usage of mobile devices and a sloppy network, a need for an efficient data loading arises. The declarative data fetching feature of GraphQL increases the efficiency of data loading because it only responds with the exact amount of information requested by a client.
Variety of front-end frameworks (i.e React, Ember, Angular e.t.c), makes it difficult to build an API that satisfies the requirement of all the frameworks. GraphQL solves the problem by exposing a single endpoint responding to queries instead of multiple endpoints returning a fixed data structures.
The breaking features of GraphQL makes it possible for a fast and continuous deployment; because it provides a possibility of building features on-the-fly.
NOTE: GraphQL is not a database, but just a query language for APIs. Its database agnostic, and can be used in any context where an API is used.
