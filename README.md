# MQTT Client Load Balancing

MQTT hands every subscriber a copy of every message, so a second consumer on a
topic doubles the work instead of splitting it. This repository demonstrates two
ways to split it: partitioning the topic by hand, and MQTT v5 shared
subscriptions. There is one runnable demo per approach, on a branch each.

Why they work and what each one costs:
[Two ways to split one MQTT topic across consumers](https://ssupawat.github.io/posts/mqtt-one-topic-many-consumers/).

## The branches

| Branch | Approach |
| --- | --- |
| `multiple-partitions-topic-hierarchy` | Multiple partitions via the topic hierarchy — a custom scheme, works on MQTT v3.1.1 |
| `shared-subscriptions-mqtt-v5` | Shared subscriptions, the `$share/<group>/topic` feature in MQTT v5 |

## Running the demo

Prerequisites: Docker.

1. Clone the repository:

```bash
git clone [repository-url]
```

2. Switch to the branch for the desired approach:

```bash
git checkout [branch-name]
```

3. Run the demo:

```bash
docker-compose up
```

4. Analyze the logs to see how messages are distributed to each consumer.

## References

- [StackOverflow thread: Is it possible to distribute reads of an MQTT topic over multiple consumers?](https://stackoverflow.com/questions/27850819/is-it-possible-to-distribute-reads-of-an-mqtt-topic-over-multiple-consumers)
- [HiveMQ Blog: Shared Subscriptions in MQTT v5](https://www.hivemq.com/blog/mqtt5-essentials-part7-shared-subscriptions/)
