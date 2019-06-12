# mattermost-refined

A brand-new Mattermost client focused on progressive enhancement.

## Technical Goals

- Maintainable stylesheet integrated with React component by CSS-in-JS approach

- Shared codebase, but fully native targets includes Web, Android, iOS, Desktop using React Native

- Robust Networking and Offline support using GraphQL. Also avoid unnecessary state sharing like the mattermost-redux via Client-side schema based cache control

- Organize deterministic navigation system

- For Web version, the improvements of first meaningful paint and interaction are prioritized through optimized web technology.

## Subprojects

- [mattergen](https://github.com/cometkim/mattergen):

  Parsing mattermost-server and generate type definitions to help building client stub.  
  
  The Mattermost server lacks type stability. Types in Mattermost are difficult to inference correctly becuase complex structure is often treated as map and also there is no Enumulator in the language (Golang).  
  
  Mattergen will provide a more strictly powerful type system based merging automatically-analized models with self-written sub-typing. 

- [mattermost-plugin-graphql](https://github.com/cometkim/mattermost-plugin-graphql):

  GraphQL is type-safe, efficient query-based remote API. And plugin is an way to extend Mattermost behavior for either the server and client.
  
  mattermost-plugin-graphql is add new **GraphQL** endpoint to exist Mattermost server.
