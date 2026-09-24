<!--
SPDX-FileCopyrightText: 2026 youradmin.guru

SPDX-License-Identifier: AGPL-3.0-or-later
-->

# Ente

The playbook can install and configure [Ente](https://ente.io), an end-to-end encrypted photo
storage service, for you.

See the project's [documentation](https://ente.com/help/self-hosting) to learn what it does and
why it might be useful to you.

For details about configuring the [Ansible role for the server](https://gitlab.com/th-ansible/roles/ansible-role-ente),
you can check them via:

- 🌐 [the role's documentation](https://gitlab.com/th-ansible/roles/ansible-role-ente/-/blob/main/docs/configuring-ente.md) online
- 📁 `roles/galaxy/ente/docs/configuring-ente.md` locally, if you have [fetched the Ansible roles](../installing.md)

## Dependencies

This service requires the following other services:

- [Postgres](postgres.md) database
- [Traefik](traefik.md) reverse-proxy server
- S3-compatible object storage, which this playbook does not install

## Configuration

To enable Ente, add the following configuration to your `vars.yml` file:

```yaml
########################################################################
#                                                                      #
# ente                                                                 #
#                                                                      #
########################################################################

ente_enabled: true

# The museum API and the Photos web app are served from hostnames of their own.
# Both need DNS records pointing at the server.
ente_museum_hostname: ente.example.com
ente_web_hostname: photos.example.com

# These secrets protect all user data and must never change once the instance holds data.
# Generate them as described in the role's documentation.
ente_museum_key_encryption: ""
ente_museum_key_hash: ""
ente_museum_jwt_secret: ""

# Ente stores photos and videos in S3-compatible object storage.
# The endpoint must be reachable both from the server and from clients.
ente_museum_s3_endpoint: s3.eu-central-003.backblazeb2.com
ente_museum_s3_region: eu-central-003
ente_museum_s3_bucket: ""
ente_museum_s3_key: ""
ente_museum_s3_secret: ""

########################################################################
#                                                                      #
# /ente                                                                #
#                                                                      #
########################################################################
```

The bucket needs a CORS policy allowing uploads from the web app. See the role's documentation
for the exact policy.

## Installing

After configuring the playbook, run the installation command:

```sh
just install-service ente
```
