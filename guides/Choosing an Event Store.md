# Choosing an event store

You must decide which event store to use with Commanded. You have a choice between two existing event store adapters:

- PostgreSQL-based Elixir [EventStore](https://github.com/commanded/eventstore).

- Greg Young's [Event Store](https://geteventstore.com/).

There is also an [in-memory event store adapter](https://github.com/commanded/commanded/wiki/In-memory-event-store) for *test use only*.

Want to use a different event store? Then you will need to [write your own event store provider](#writing-your-own-event-store-provider).

---

## PostgreSQL-based Elixir EventStore

[EventStore](https://github.com/commanded/eventstore) is an open-source event store using PostgreSQL for persistence, implemented in Elixir.

Please follow the [Getting started](https://github.com/commanded/commanded-eventstore-adapter#getting-started) guide to install and configure the EventStore adapter.

---

## Greg Young's Event Store

[Event Store](https://geteventstore.com/) is an open-source, functional database with Complex Event Processing in JavaScript. It can run as a cluster of nodes containing the same data, which remains available for writes provided at least half the nodes are alive and connected.

The quickest way to get started with the Event Store is by using their official [Event Store Docker container](https://store.docker.com/community/images/eventstore/eventstore).

The Commanded adapter uses the [Extreme](https://github.com/exponentially/extreme) Elixir TCP client to connect to the Event Store.

Please follow the [Getting started](https://github.com/commanded/commanded-extreme-adapter#getting-started) guide to install and configure the EventStore adapter.

### Running the Event Store

You **must** run the Event Store with all projections enabled and standard projections started.

Use the `--run-projections=all --start-standard-projections=true` flags when running the Event Store executable.

---

## Writing your own event store provider

To use an alternative event store with Commanded you will need to implement the `Commanded.EventStore` behaviour. This defines the contract to be implemented by an adapter module to allow an event store to be used with Commanded. Tests to verify an adapter conforms to the behaviour are provided in `test/event_store_adapter`.

You can use one of the existing adapters ([commanded_eventstore_adapter](https://github.com/commanded/commanded-eventstore-adapter) or [commanded_extreme_adapter](https://github.com/commanded/commanded-extreme-adapter)) to understand what is required.
