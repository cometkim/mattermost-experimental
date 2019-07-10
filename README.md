# mattermost-experimental

An experimental Mattermost client focused on technical enhancements.

## Technical Goals

- End-to-end type-safety
- Sharing codes in the right way
- Faster client experience

### Problems

1. Modeling: Mattermost's model is based on a golang which is much less expressive of the type system than other modern languages, and does not provide a separate abstraction on the client. This is not useful in client code and interoperability to other languages.

2. Sharing codes: The mattermost-redux is a way to share network bindings between the web and mobile, but it also has the disadvantage of sharing heavy and unnecessary logic. On the other hand, the UI for the web, mobile, desktop is almost fragmented.

3. Missing optimizations:

### Solutions

**GraphQL, React Native(includes Web & Desktop), ReasonML(or just TypeScript?)**

- With **GraphQL**, we can build more useful models for Mattermost client while retaining existing store models, and it has excellent interoperability with other languages through tooling.

- With **React Native Web**, we can share almost UI codebase, but still fully supports native targets. native desktop app also would be an option.

- With **Apollo Client**, while Apollo is implementing and optimizing the GraphQL specification, we can focus more on developing the UI instead of paying attention to the network binding (include WebSockets).

- With **ReasonML**, It is very well integrated with GraphQL, React Native, and can be developed with super-strong type system support.

And more...

- Robust Networking and Offline support using GraphQL and Apollo. Also avoid unnecessary state sharing like the mattermost-redux via Client-side schema based cache control

- For Web version, we can improve of first meaningful paint and interaction are prioritized through optimized web technology.

## Subprojects

### Mattergen

Status: Redesigning

- [mattergen](https://github.com/cometkim/mattergen):

  Parsing mattermost-server and generate type definitions to help building client stub.  
  
  The Mattermost server is very weakly-typed because of flexibility. Types in Mattermost are difficult to inference correctly becuase complex structure is often treated as map and also there is no Enumulator in the language (Golang).  
  
  Mattergen will provide a more strictly powerful type system based merging automatically-analized models with self-written sub-typing. 

### mattermost-plugin-graphql

Status: Waiting for mattergen

- [mattermost-plugin-graphql](https://github.com/cometkim/mattermost-plugin-graphql):

  GraphQL is type-safe, efficient query-based remote API. And plugin is an way to extend Mattermost behavior for either the server and client.
  
  mattermost-plugin-graphql is add new **GraphQL** endpoint to exist Mattermost server.
