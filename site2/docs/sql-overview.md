---
id: sql-overview
title: Pulsar SQL Overview
sidebar_label: "Overview"
---

Apache Pulsar is used to store streams of event data, and the event data is structured with predefined fields. With the implementation of the [Schema Registry](schema-get-started.md), you can store structured data in Pulsar and query the data by using [Trino (formerly Presto SQL)](https://trino.io/).

As the core of Pulsar SQL, the Presto Pulsar connector enables Presto workers within a Presto cluster to query data from Pulsar.

![The Pulsar consumer and reader interfaces](/assets/pulsar-sql-arch-2.png)

The query performance is efficient and highly scalable, because Pulsar adopts [two-level-segment-based architecture](concepts-architecture-overview.md#apache-bookkeeper). 

Topics in Pulsar are stored as segments in [Apache BookKeeper](https://bookkeeper.apache.org/). Each topic segment is replicated to some BookKeeper nodes, which enables concurrent reads and high read throughput. You can configure the number of BookKeeper nodes, and the default number is `3`. In Presto Pulsar connector, data is read directly from BookKeeper, so Presto workers can read concurrently from a horizontally scalable number of BookKeeper nodes.

![The Pulsar consumer and reader interfaces](/assets/pulsar-sql-arch-1.png)
