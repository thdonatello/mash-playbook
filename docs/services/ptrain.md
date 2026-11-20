# ptrain

[ptrain](https://gitlab.com/youradmin_guru/ptrain) is a Telegram bot with a Telegram Mini App for
a personal trainer and their clients. Each environment (`prod`, `test`) runs three containers:
the Mini App server, the bot program and the Mini App screens.

The role lives in the private repository
[ansible-role-ptrain](https://gitlab.com/th-ansible/roles/ansible-role-ptrain); its README lists
every setting. It needs [Postgres](postgres.md) and [Apache Kafka](kafka.md).

## Configuration

See `deploy/mash/INTEGRATION.md` in the ptrain repository for the `vars.yml` and `vault.yml`
keys of each environment.
