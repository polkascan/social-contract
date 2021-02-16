# Progress Report 2

This is the second progress report for Polkascan's PolkADAPT project. Details of our project can be found here: https://docs.google.com/document/d/1AUmILFpAqh_BRR1wlxdE9GS9iWPt-4X9SXaguaJXBfQ/edit?usp=sharing. The Polkassembly post can be found here: https://kusama.polkassembly.io/treasury/57. 

In general the groundwork has been laid in our three basic respositories of the project:
1. PolkADAPT: https://github.com/polkascan/polkadapt
2. Polkascan UI: https://github.com/polkascan/polkascan-ui
3. Explorer API: https://github.com/polkascan/explorer-api

The remainder of this document provides an account of our activities and design decisions per repository. The next milestone and deliverables will focus on more visible and tangible deliverables for the general public by combining these respositories into our Polkascan Beta platform on https://beta.polkascan.io. This platform will incrementally gain features to mirror the feature of our current explorer platform https://polkascan.io and will eventualy be its replacement. Additionally the next milestone and deliverables will further improve our repositories CI/CD pipeline.

## 1. PolkADAPT (Michiel + Wouter)


### 1.1. Overview of time spent per category

| Category                 | Hours spent |
|:------------------------ | ----------- |
| Project overhead         | 14          |
| Research & Prototyping   | 10          |
| Development              | 31          |
| Testing & Bugfixing      | 8           |


### 1.2. Result

As part of [PolkADAPT](https://github.com/polkascan/polkadapt) we have built an experimental [PolkascanAdapter library](https://github.com/polkascan/polkadapt/tree/main/projects/polkascan), which connects to the HTTP and websocket interfaces of the Polkascan Explorer API. For now the adapter only uses a static graphQL query to fetch data for testing purposes.

An improvement has been made to the [core library](https://github.com/polkascan/polkadapt/blob/main/projects/core/src/lib/core.ts) readystate functionality. PolkADAPT now waits until the websocket connection is connected and in ready state to accept incoming messages. The adapterBase requires each adapter to expose a promise that resolves the adapters ready state. The [SubstrateRpcAdapter](https://github.com/polkascan/polkadapt/blob/main/projects/substrate-rpc/src/lib/substrate-rpc.ts) now exposes this promise.

### 1.3. Design Decisions

The Explorer API is based on the GraphQL standard, therefore the [PolkascanAdapter](https://github.com/polkascan/polkadapt/tree/main/projects/polkascan) has to communicate with the server by sending a GraphQL query. For all exposed adapter functions we will hard-code the queries in the adapter.
We have looked at different javascript GraphQL libraries, but most of them are bloated with functionality that we do not want our application to use. We also don't want to enforce third party libraries to other developers who use the PolkascanAdapter.

### 1.4. Next steps

We will start using PolkADAPT in the Explorer UI to serve data in lists and detail views. For every view the necessary GraphQL queries will have to be written in the PolkascanAdapter.

PolkADAPT offers subscriptions to data changes, so this type of connection will be built and tested. The current Polkascan website uses polling to update views, whereas the new Explorer UI will use subscriptions on both the RPC and Polkascan websockets.

When working with subscriptions, data from different sources can be emitted in different order. We will need to figure out how incoming data from subscriptions on the same call path need to be merged or added. For example a list view wants a different type of subscription than a detail view that has interest in only one object. 


## 2. Polkascan UI (Michiel + Wouter)

### 2.1. Overview of time spent per category

| Category                 | Hours spent |
|:------------------------ | ----------- |
| Project overhead         | 14          |
| Development              | 85          |

### 2.2. Result

We've layed the foundation of the new Angular-based Polkascan Application. We've developed some [components](https://github.com/polkascan/polkascan-ui/tree/main/src/app/pages/network) and [services](https://github.com/polkascan/polkascan-ui/tree/main/src/app/services) to switch between Substrate networks. The Application is still very limited in functionality, but the main goal for this deliverable was to utilize PolkADAPT to get streaming data from multiple adapters and show a [dynamic list of latest blocks](https://github.com/polkascan/polkascan-ui/blob/main/src/app/pages/network/explorer/explorer.component.ts). Check the [README](https://github.com/polkascan/polkascan-ui/blob/main/README.md) for build and run instructions.


### 2.3. Design Decisions

Because the Application depends on PolkADAPT, and both projects are in heavy development, we've decided to incorporate PolkADAPT as a Git Submodule. This makes it easier for us to simultaneously develop on both projects.

We've decided to create a [Dockerfile](https://github.com/polkascan/polkascan-ui/blob/main/Dockerfile) to be able to test the build process and generate a ready-to-run image with an nginx webserver. You can change the URL of each adapter's endpoint with container runtime environment variables.


### 2.4. Next steps

Next step for the Polkascan UI is to add more functionality, such as master-detail views for blocks, extrinsics, etc. Where possible, we'll leverage the multi-adapter approach of retrieving and displaying augmented data.

Also, we want to set up a CI/CD pipeline to automatically publish new versions of the UI.


## 3. Explorer API (Matthijs)

### 3.1. Overview of time spent per category

| Category                        | Hours spent  |
|---------------------------------|--------------|
| Design discussions              | 16           |
| Research                        | 36           |
| Prototyping                     | 30           |
| Project overhead                | 5            |


### 3.2. Result

In this second reporting term I've built upon the graphql api; making it possible to add flexible filters to queries / subscriptions and supporting GraphQL v3 in combination with both http and websockets.

A docker and docker-compose file is created to allow for easy local deployment. A Github action is created to streamline the future testing and deployment pipeline.

All unexpected errors are now logged to Sentry. For logging and visualizing metrics Prometheus and Grafana are chosen. For regular logging we decided to use the ELK stack (Elasticsearch, Logstash and Kibana), for which we will set up a dedicated logging server.


### 3.3. Design Decisions

The main objective this period was to support live queries through graphql subscriptions. Unfortunately this is not something that is supported out of the box by Graphene yet (https://rob-blackbourn.medium.com/graphene-3-queries-mutations-subscriptions-a699926ca469), so I settled for starlette-graphene3 (https://pypi.org/project/starlette-graphene3/) until the next release. A few modifications had to be made for dependent libraries, which is far from ideal, but makes it possible to go forward with the required functionality and upgrade to a better supported library once graphene v3 is released (https://github.com/graphql-python/graphene/blob/master/ROADMAP.md).

Graphene-sqlalchemy-filter (https://pypi.org/project/graphene-sqlalchemy-filter/
) is chosen to add flexible filtering to all graphql resources. All these libraries combined together make the code very DRY, nevertheless each time we add such libraries they should provide sane defaults. We make sure we can always override this logic with our own so we don't get "locked in".

For deployment dotenv was chosen to transparently manage settings between local development and docker based deployments.


### 3.4. Next steps

* Keyset based query pagination
* Live updates -> allow for subscriptions on realtime data from the harvester
* Logging & metrics
* Implement more GraphQL queries & subscriptions required by PolkADAPT
* Add unit tests



## 4. Project Support (Arjan)

This progress report will include activities covering deliverable 1 and 2 as described in the IT development agreement for PolkAdapt.

### 4.1. Overview of time spent per category

| Category          | Hours spent |
|:----------------- | ----------- |
| Technical support | 24          |
| Development       | 16          |

### 4.2. Activities

Most of the time was spent discussing various technical solutions about the new Polkascan API, like choosing GraphQL, researching how to utilize Prometheus and how to implement logging. I also provided support with how to use Docker to build the new Polkascan API. 

The development work included constructing the new SQLAlchemy models and get working example metrics of Prometheus for the new Polkascan Harvester.