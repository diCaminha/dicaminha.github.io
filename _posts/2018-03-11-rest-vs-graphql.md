---
layout: post
title: INTRODUCTION TO GRAPHQL FOR REST DEVS
---
Hi there! 
First of all this article is not exactly a well done comparation article between two tools (architecture to be more precise). I will
humbly try to show you some of concerns and highlights about to concepts used to transfer/achieve data on the web: GraphQL and REST.  
First I'm gonna review what is REST after all, then I will explore the weakness of this concept, and finally introduce GraphQL.
  
## *RE*presentation *S*tate *T*ransfer
  To get a good enough knowledge about what really is REST we need to review a little bit **'HTTP Verbs'** or the famous HTTP methods
  (GET, POST, DELETE,PUT,... ). Those methods were created aiming to turn the requests 'more human' in a semantic way. I mean, for instance,
  if I make a request like: GET hhtp://anecommerce.com/products it is clear that I’m getting the products. Also, when I do DELETE http://anecommerce.com/products/3 I’m, easily visible, trying to delete the product with id equals to 3.

Another good point is about the structure of a request and response HTTP. Let’s break it down and try to figure it out:
- Endpoint: 
  - The route, the url which you request by the browser to a server.
- Method: 
  - HTTP verbs commented earlier.
- Headers: 
  - used to exchange info, as authentication,...
- Body: 
  - The info in fact. Literally the body of the communication.
	
The big logic is that having this we got a set of ‘rules’ that when obeyed in the right way, promise a well pattern application with self-explained interfaces to communicate easily throughout the web.
  
  When we’re developing an application which will consume from a server REST, we should have as reference a resource in our requests. For instance, in our demonstration of URL earlier on this article the resource was the ‘product’ 
Another key point, both to the client and to the server, is the **‘Content-type’**. 

It works on the information exchange, where  both client and server will look at this content type and then figure out with  which ‘clothes’ the coming datas are dressing. (json, text,xml ...).


## Downsides with REST:
	
In the previous topic about REST we got the idea that if an API is adapted to verbs related to HTTP, then it will have a well enough income as to communication, information transfer via apps. 

**BUT**, when an application needs to change some business logic or even increase a new functionality beyond those from HTTP verbs, then we got some difficulties. Also try to fetch multiple resource using REST; I guarantee you it won´t be that easy. 
Let’s create a situation about this here: Suppose we tried to get ‘conferences’ and all the ‘articles’ of those events. 

With REST, we have to make many requests to the servr, or require a response more elaborated by the server (fact that opens space for dumb stuffs as response’s size). The size also appears in another ugly problem when we got A LOT of unusual informations about ‘articles’ (date, author, university,...) when we only needed was the name of this.                                                                                                                                                                                                                                                                                                                                                                                                

## GRAPHQL:
	
Using GraphQL, some of those problems might disappear. (if you define it as problems. Because if not, not interest to you what is coming).
Firstly let’s take a look of how we’re used to do a request using it:

```javascript
  query {
    someConferences(count:20 , offset: 0){

      id
      region
      theme
      articles {
        id
        author {
          name
        }
      }
    }
}
```
Turning a blind eye for a while to concerns as ‘where do I should to send this’ or ‘how does the server receive this’ (I will work on it later), it’s pretty understandable what it means, what it want: A list of ‘conferences’ with its articles and authors (only his name).

Analyzing more closely, we know that articles (on real world) have many informations beyond ‘name’, but in this request we don’t care for those informations; we just want the name of it; and we inform it to the server. 
Nothing else more. Less of Kbytes flying from side to side.

This is the big idea of GraphQL: *be susint, give what it suppose to give*. It’s like a query on database: not always we go like select * from articles, sometimes we just want select name from articles.  This is GraphQL, making queries throughout the web; oriented by query.
So, but things work from the server side? I mean, what to do with a bunch of informations inside a JSON object called query? For that, there’s a schema implemented by the server that specify everything reachable by the webservice. It’s made by typing elements (resources) having fields. Pretty like we have on O.O.

```javascript
schema {

	type Conference{
	id: ID!
	region: String!
	theme: String
	articles: [Article]!	
	
}

type Article {
	
	id: ID!
	title: String!
	date_published: Date
	author: [Author]!
}

type Author {
	id: ID!
	name: String
	lastname: String
	age: int
}

#Here comes some method’s definitions to be used by clients.
	someConferences(count: Int , offset: Int): [Conference]!	

}
```

* The simbol ! means non-null field 
* [] means a list

With this scheme already known by the server, and knowing the client can check any time this structure , so become peace of cake to make searches pointing to only what we really want.

So, that's it for now. Later I'll be writing an article with more work's day examples of using graphql (and implementing it in different languages like **JAVA**, **JS**, **Ruby** and so on...).

## Fonts
* [link 1: caelum](http://blog.caelum.com.br/todo-o-poder-emana-do-cliente-explorando-uma-api-graphql/)
* [link 2: Phil Sturgeon](https://philsturgeon.uk/api/2017/01/24/graphql-vs-rest-overview/)
* [![GRAPHQL](http://img.youtube.com/vi/lAJWHHUz8_8&t=1s/0.jpg)](http://www.youtube.com/watch?v=lAJWHHUz8_8&t=1s)
)
