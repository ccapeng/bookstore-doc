# Tech Stacks

In these days, most of applications are on the web.  
With various frameworks, how do you pick for your need?

## Framework selection and transition

In the simple data collection/presentation, we want to the application ready in a short time.  
In a mission critical transaction, we may consider the performance.

What if you want to have a quick prototype to present to manager team, then deep dive into the right solution after planned?  
In here, I am going to have solution of how to do.  
Use bookstore model as example in some different kinds of projects.

![Tech Stacks](.gitbook/assets/bookstore%20%282%29.png)

## Bookstore Projects in Github

* Fullstack MVC
  * [Django MVC](https://github.com/ccapeng/django-bookstore)
    * [Form validation in view class](topic-django-class-view-validation.md)
  * [Django REST Framework + React](https://github.com/ccapeng/bookstore_api)
    * [Serializer validation](topic-serializer-validation.md)
  * [Server Side React, login required](https://github.com/ccapeng/bookstore_pro)

    Django REST Framework + Fully Server Side React JS \(No Next.js\)

    Need to login to have both REST APIs and React JS to work.  
    No React JS expose to public.  
    [How this works?](topic-protect-react.md)

  * [Go & Beego](https://github.com/ccapeng/beego-bookstore)
  * [Laravel php](https://github.com/ccapeng/laravel_bookstore)
* REST
  * Object relationship model \(ORM\)
    * [Django Data model](topic-django-rest.md)
    * Flask w/SQLAlchemcy
    * Node.js w/typeORM
    * Node.js w/Adonis
  * Backend
    * [Python Django REST](https://github.com/ccapeng/bookstore_openapi)
    * [Python Flask REST](https://github.com/ccapeng/bookstore_flask_api)
    * [Node.js w/typeORM](https://github.com/ccapeng/typeorm-bookstore)
    * [Node.js w/Adonis](https://github.com/ccapeng/adonis-bookstore)
  * Frontend
    * [React Context](https://github.com/ccapeng/bookstore-context)
    * [React Hook Redux](https://github.com/ccapeng/bookstore-hook-redux)
    * [React Hook Redux TypeScript](https://github.com/ccapeng/bookstore-tx-redux)
    * [React with Jotai](https://github.com/ccapeng/bookstore-jotai)
      * [Migrate state management from Redux to Jotai](topic-migrate-redux-to-jotai.md)
* GraphQL
  * Backend [Django Graphene](https://github.com/ccapeng/bookstore_graphene).
  * Frontend
    * [React redux graphQL](https://github.com/ccapeng/bookstore-redux-graphql)
  * [Migrate from REST to GraphQL](topic-rest-to-graphql.md)  
* gRPC
  * Backend

      [Django gRPC](https://github.com/ccapeng/bookstore_grpc).  

  * Frontend
    * [React redux grpc](https://github.com/ccapeng/bookstore-redux-grpc)
* Migration Options:
  * Migrate Your Prototype to Your Coding framework :
    * Once your have prototype for demo, 

      [Use Open API data model](topic-use-open-api.md) to migrate.  

      Django is battery included framework.   

      It can be set up easy for the presentation.  

      Once you have ideas to demo to team, you can start use the following to migrate.
    
    * [Migrate Django to Flask](topic-migrate-django-to-flask.md)
    * [Migrate Django to Node](topic-migrate-django-to-node.md)
    
  * [React context and redux difference](topic-react-context-and-redux-diff.md)
  * [How to handle cross origin?](topic-cross-origin.md)

## Other Topics -- more experiences to share

* [Best practice of programming](https://ccapeng.gitbook.io/programming/)
* [Graph](https://ccapeng.gitbook.io/graph/)
* [Namespace](https://ccapeng.gitbook.io/namespace/)
* [Context](https://ccapeng.gitbook.io/context/)

## Contact Me

`ccapeng@gmail.com` [`ccapeng.github.io`](https://ccapeng.github.io)

[View full document](https://ccapeng.gitbook.io/bookstores/)

