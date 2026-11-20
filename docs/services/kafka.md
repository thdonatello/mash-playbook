# Apache Kafka

[Apache Kafka](https://kafka.apache.org/) is an event streaming platform. This playbook runs a
single broker in KRaft mode (no ZooKeeper) with a memory limit, for small installations.

The role lives in [ansible-role-kafka](https://gitlab.com/th-ansible/roles/ansible-role-kafka);
its README lists every setting.

## Configuration

```yaml
kafka_enabled: true
# Generate once and never change:
# docker run --rm apache/kafka:<version> /opt/kafka/bin/kafka-storage.sh random-uuid
kafka_cluster_id: ""
```

Topics are created by the role from `kafka_topics_auto` (filled by services that use Kafka) and
`kafka_topics_custom`. Automatic topic creation is disabled. The broker is not exposed outside
the host.
