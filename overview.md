<!---
   Copyright 2018 Ericsson AB.
   For a full list of individual contributors, please see the commit history.

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
--->

# RemRem Architecture
![RemRem Architecture](https://github.com/eiffel-community/eiffel-remrem/raw/master/media/remrem_architecture.png "RemRem Architecture")

Architecture of remrem is based on Microservice and API design principles utilizing state of the art in development.

## Principles
- Microservices driven
 - Independent deployment
 - Decoupled services
 - No shared libraries
 - Stateless
 - Isolates failures
 - Decentralized

# RemRem Components
- Generate (Microservice): Can be used to generate validated Eiffel messages. [Generate Github Repo](https://github.com/eiffel-community/eiffel-remrem-generate)
- Publish (Microservice): Can be used to publish Eiffel messages. [Publish Github Repo](https://github.com/eiffel-community/eiffel-remrem-publish)
- Semantics (Library): Injectable library used with Generate Microservice to enable generation of new Eiffel messages. [Semantics Github Repo](https://github.com/eiffel-community/eiffel-remrem-semantics)
- Shared (Library): Interface information used in injecting message libraries. Utilized by Semantics and Eifel3Messaging innersource projects [Shared Github Repo](https://github.com/eiffel-community/eiffel-remrem-shared)

# Building and releasing
For every RemRem component it is needed to create a new release tag in the component's repository on github. Once the tag is created the build for the new release tag will be started when you visit the component's page on jitpack.io (i.e. https://jitpack.io/#eiffel-community/eiffel-remrem-generate) and published on component's page on jitpack.io or when another application is build and it is dependent of the new release tag from jitpack.io.
