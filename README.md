# wit-contentServe
Provides content (data) for all wit products, significantly so for the `wit-dash` application. As a data rich service, `wit-contentServe` is a GraphQL interface served through the excellent `nest.js` (node.js) framework. The data store is provided by the excellent `MongoDB`.

`wit-contentServe` includes data caching and resolves against a set of local and and remote microservices. GraphQL resolvers can run local, and representations of all such dependable microservices are provided within this nest.js application making it easy to ran this application locally, with no external dependencies.

Deployed with TDD (Test Driven Development) approach, `wit-contentServe` comes with a set of unit and integration `Jest` test scripts.

For 'WOZiTech' hosted services, AWS ECS is a the default platform. But `wit-contentServe` can run in local dev, private local or cloud (OpenStack) or public (Google/Azure/IBM) cloud environment. `wit-contentServe` is targetted to be created as a Docker image and presented at runtime via Kubernetes/AWS ECS. A docker image will be maintained by 'WOZiTech Ltd' and available for download, but equally, a `dockerfile` is maintained as part of this code base that can be used to create custom images on-demand using ansible. This `dockerfile` is used by the Jenkins CI/CD pipeline to maintain the downloadable Docker image.

# Security
Data is king they say, and as such, all data must be protected. A GraphQL interface makes it easy to access and navigate data. However, access to any data is protected using an Auth0 token with a specific claim and authorisation to specific customer data for the client ID scope within the token. The tokens are only available via the PI local `wit-piSecure` and central `wit-auth` services.

## GraphQL Schema
GraphQL allows for schema browsing; via the GraphiQL web interface. This is available in your own local environments, but intentionally blocked from the 'WOZiTech' hosted services. Hosted data is securely protected at all times; it is not available for discovery. Besides, without a valid token, you won't get access anyway.

# GraphQL Data
Example data is provided as part of the jest test suite. Simply run 'npm test'. Yes, I use `npm` not `yarn`.

# TODO

# Dependencies
* [Even for local development, MongoDB is required. Can be locally installed or can be cloud provided (Atlas)] (https://www.mongodb.com/ "MongoDB Homepage")
