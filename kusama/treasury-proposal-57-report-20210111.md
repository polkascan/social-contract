# Progress Report 1
This is the first progress report (of many) that will report on progress of Polkascan's PolkADAPT project. Details of our project can be found here: https://docs.google.com/document/d/1AUmILFpAqh_BRR1wlxdE9GS9iWPt-4X9SXaguaJXBfQ/edit?usp=sharing. The Polkassembly post can be found here: https://kusama.polkassembly.io/treasury/57. 

We have had a slight delay due to the Christmas break and COVID-related issues. In general the community can expect progress reports with two week intervals towards full delivery of the project's objectives. Deliverables are divided into three distict repositories which are reported on separately in the following sections. In our forthcoming progress reports these repositories and the work will increasingly converge towards the common goals set out in the project outline.

## PolkADAPT



### Overview of time spent per category

| Category                 | Hours spent |
|:------------------------ | ----------- |
| Project Kickoff/Overhead | 16          |
| Research & Prototyping   | 40          |
| Development & Testing    | 40          |

### Result

We've committed the first lines of code to the [PolkADAPT Github repository](https://github.com/polkascan/polkadapt).

We've layed the groundwork for PolkADAPT. Besides setting up the development environment and the project structure, we've focussed mainly on creating the @polkadapt/core library. This library orchestrates routing of functionality and augmentation of data from Adapters.

The [core library](https://github.com/polkascan/polkadapt/blob/main/projects/core/src/lib/core.ts) makes it possible to have the same function call for multiple data sources (provided by the Adapters). The resulting data will then be combined.

Also, we've created the [SubstrateRpcAdapter](https://github.com/polkascan/polkadapt/blob/main/projects/substrate-rpc/src/lib/substrate-rpc.ts) that brings the Substrate on-chain data to PolkADAPT through the use of Polkadot.js @polkadot/api.

### Design Decisions

For developers that need to combine data from various sources, we wanted to create a single tool to simplify this process.

We decided to create a system that consists of a [core library](https://github.com/polkascan/polkadapt/blob/main/projects/core/src/lib/core.ts) and adapter libraries for each data source. The core serves as an intermediary service that has the ability to communicate between an application and data sources.

We allow multiple adapters to register the exact same call signature. The core library proxies the call to the endpoints in these adapters and combines the response from the endpoints into one result object.

The [SubstrateRpcAdapter](https://github.com/polkascan/polkadapt/blob/main/projects/substrate-rpc/src/lib/substrate-rpc.ts) is one of the cornerstones for PolkADAPT. It's the first adapter we needed and thus developed. It is mandatory to connect with chains. Other adapters will be able to augment the functionality of this adapter. This adapter is a thin layer that just passes the @polkadot/api library.

The PolkADAPT libraries are meant to be framework-independent. You can use PolkADAPT in React, Vue, Angular, vanilla JS, etc.

The development environment (to develop the PolkADAPT libraries) is generated with the Angular CLI. It includes all the batteries needed to develop, test and build a set of libraries using TypeScript. Angular provides easy mechanics to keep the toolchain up to date.

### Next steps

There is no offically released package for PolkADAPT, yet. The next phase will include setting up the CI/CD pipeline to generate and publish new releases to NPM.

Next step is to create a new Adapter for Polkascan, making PolkADAPT the primary entrypoint for communication with the Polkascan web service. As this web service is being rebuilt into a v2 API, the adapter will be updated to this version in parallel.

## Explorer UI

### Design decisions

The new explorer UI will be build on the Angular framework. First steps will be to recreate the original Polkascan using PolkADAPT instead of the current Polkascan web service. The new block explorer will combine direct on-chain data together with the (off-chain) data collections from Polkascan. Graphics design is also on the roadmap, but our focus is on the tech first.

### Next steps

- Build the base framework for the new Polkascan, including a dashboard and at least one master-detail view.
- Build a testing adapter that uses the current polkascan api.
- Work on design specs for the new explorer API adapter.
- Collect reusable components used in Polkascan to be added to the Polkadot-Angular component library.



## Explorer API

### Overview of time spent per category

| Category                        | Hours spent  |
|---------------------------------|-----|
| Project Kickoff/Discussions     | 24  |
| Research & Prototyping          | 19  |


### Result

We’ve committed the first lines of code to the Explorer API Github repository.

In this first reporting term I've started work on the new Explorer API. The time is mostly spent on making architectural desisions and creating a prototype to test how the chosen components could work together. In this prototype all required components are tied together to create our API to build upon.

### Design Decisions

The main focus was to explore viable options to chose from. Given the earlier work done for Polkascan, Python was chosen as language. One of the niceties of Python is it's ability to quickly develop and iterate, a disadvantage is it's losely typing system and lacklustre runtime performance.

A relatively new framework called FastAPI [https://fastapi.tiangolo.com/] aims to at least fix part of this, leveraging Python 3 typing hints interwoven in it's core and schema validations system.

One of the requirements was to provide websocket support (and optionally traditional HTTP requests), both which are natively supported by FastAPI [https://fastapi.tiangolo.com/advanced/websockets].

After evaluating some options i settled with GraphQL for query requests [https://graphql.org/]. It is a widely accepted standard and fulfils our requirement for flexible query configuration. It also supports subscriptions [https://graphql.org/blog/subscriptions-in-graphql-and-relay/] on data changes which was a requirement for the websocket part of our API.

I settled with Graphene [https://graphene-python.org/] for the implementation, it is widely used and supported and integrates very nicely with FastAPI.

For the database / ORM i chose to use SQLALchemy [https://www.sqlalchemy.org/], which is a very flexible SQL toolkit. It is used in combination with Alembic to manage all DDL changes. These libraries are also used by Polkascan, which makes sharing the ddl/data very convenient.

Another important aspect this framework provides is easy request schema validation, data serialization & deserialization. Graphql-python was chosen for the bulk of this, it's a very convenient library for serialize SQLALchemy models [https://github.com/graphql-python/graphene-sqlalchemy].
For more complex models custom GraphQL schemas can be written. FastAPI provides schema validation using Pydantic [https://pydantic-docs.helpmanual.io/], there are also options to convert these to GraphQL schemas using [https://github.com/graphql-python/graphene-pydantic].

For error logging Sentry [https://sentry.io/welcome/] is used to diagnose any errors that might occur.

### Next steps

Next up is deployment; creating docker/docker-compose files and setting up testing (unit tests).

After that, logging will be connected to Grafana to gain insights in all kinds of metrics for API usage.

When deployment, testing and logging is in place, I will work on the Explorer API & PolkADAPT connector
