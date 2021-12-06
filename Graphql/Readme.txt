PT-BR

Introdução a Graphql

GraphQL[1] é uma linguagem de consulta criada pelo Facebook em 2012 e lançada publicamente em 2015.[2] É considerada uma alternativa para arquiteturas REST, além de oferecer um serviço runtime para rodar comandos e consumir uma API.

Why a GraphQL Client?
In the Clients section in the GraphQL part, we already covered the responsibilities of a GraphQL client on a higher level. It’s now time to get more concrete.

In short, we should use a GraphQL client for tasks that are repetitive and agnostic to the app we’re building. For example, being able to send queries and mutations without having to worry about lower-level networking details or maintaining a local cache. This is functionality we’ll want in any frontend application that’s talking to a GraphQL server. Why build these features yourself when we can use one of the amazing GraphQL clients out there?

There are several GraphQL client libraries available that all give us varying degrees of control over ongoing GraphQL operations and come with different benefits and drawbacks. For very simple use cases (such as writing scripts), graphql-request might already be enough for our needs. Libraries like it are thin layers around sending HTTP requests to our GraphQL API.

Chances are that you’re writing a somewhat larger application where you want to benefit from caching, optimistic UI updates and other handy features. In these cases you’ll likely want to use a full GraphQL client that handles the lifecycle of all your GraphQL operations. You have the choice between Apollo Client, Relay, and urql.