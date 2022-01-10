# REMReM
REMReM ( **RE**ST **M**ailbox for **Re**gistered **M**essages ) contains a set of tools to generate validated Eiffel messages and publish them on a RabbitMQ message bus. They can operate as micro services or as stand-alone CLI versions.

REMReM consists of two main functions:
- REMReM Generate: for generating valid Eiffel messages and validating them against the [protocol schemas](https://github.com/eiffel-community/eiffel/tree/master/schemas).
- REMReM Publish: for publishing Eiffel messages on an RabbitMQ with authentication. When using REMReM as a service it provides an endpoint to both generate the messages and publishing them. For information on how to use the publish service please see the [REMReM publish usage](https://github.com/eiffel-community/eiffel-remrem-publish/blob/master/wiki/markdown/usage/service.md#usage).

## REMReM Architecture
![RemRem Architecture](https://github.com/eiffel-community/eiffel-remrem/raw/master/media/remrem_architecture.png "RemRem Architecture")

The architecture of REMReM is based on Microservice and API design principles utilizing state of the art in development.

### Principles
- Microservices driven
 - Independent deployment
 - Decoupled services
 - No shared libraries
 - Stateless
 - Isolates failures
 - Decentralized

## RemRem Components
- Generate (Microservice): Can be used to generate validated Eiffel messages. [Generate Github Repo](https://github.com/eiffel-community/eiffel-remrem-generate)
- Publish (Microservice): Can be used to publish Eiffel messages. [Publish Github Repo](https://github.com/eiffel-community/eiffel-remrem-publish)
- Semantics (Library): Injectable library used with Generate Microservice to enable generation of new Eiffel messages. [Semantics Github Repo](https://github.com/eiffel-community/eiffel-remrem-semantics)

## Building and releasing
For every REMRem component it is needed to create a new release tag in the component's repository on GitHub. Once the tag is created the build for the new release tag will be started when you visit the component's page on jitpack.io (i.e. https://jitpack.io/#eiffel-community/eiffel-remrem-generate) and published on component's page on jitpack.io or when another application is build and it is dependent of the new release tag from jitpack.io.
