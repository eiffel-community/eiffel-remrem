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
For every REMReM component it is needed to create a new release tag in the component's repository on GitHub. Once the tag is created the build for the new release tag will be started when you visit the component's page on jitpack.io (i.e. https://jitpack.io/#eiffel-community/eiffel-remrem-generate) and published on component's page on jitpack.io or when another application is build and it is dependent of the new release tag from jitpack.io.

## Branching Strategy
Development and releasing on REMReM repositories proceeds sequencially in most cases, i.e. releases are available on master branch.
Sometimes, however, things get more complicated. Then, utilization of _maintenance_ branche is suggested.

A maintenance branch is created when release cannot be created on master branch, see examples below.

~~~~
master   ... 1.0.0 -- 1.0.1 ... 2.1.4 ... 3.2.5 -- 4.0.0    ...   4.1.13 -- 4.1.14 -- ...
                            \                  \                        /
                             \                  \                      /
1.0-maintenance                1.0.2 -- 1.0.3    \                    /
                                                  \                  /
                                                   \                /
3.2-maintenance                                      3.2.6 -- 3.2.7 -- 3.2.8
~~~~

Here, the following scenario is depicted:
* After some initial development versions `1.0.0` and `1.0.1` are released.
* Development continues and series of versions `2.0.X` is released.
* Later, when the latest release is `2.1.4`, a bug on release `1.0.1` is reported and needs to be fixed. So far all of the releases were released on master branch, but now fix of the bug cannot be released on master after release `1.0.1`. That is why a new branch `1.0-maintenance` is introduced and the bug is fixed in releases `1.0.2`. If they are other fixes or improvements of series `1.0`, they are released on the maintenance branch.
* Suppose a situation when the latest release is `4.1.13` and a fix must be done for `3.2.5`. Analogously to series `1.0`, a maintenance branch `3.2-maintenance` is created and the fix is released by `3.2.6` and `3.2.7`. If an issue, fixed by `3.2.7`, is also detected in `4.0` series, the fix needs to be merged to master and released as `4.1.14`.
* Other fixes or improvements of series `3.2` continue on branch `3.2-maintenance`.

Note, that each release is _tagged_ as stated in [previous section](#building-and-releasing).
