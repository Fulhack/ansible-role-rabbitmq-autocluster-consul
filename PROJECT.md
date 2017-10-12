# Project notes


## Installation

### Docker

Example using [docker-compose](https://github.com/rabbitmq/rabbitmq-autocluster/tree/stable/examples/compose_consul_haproxy)

Small RabbitMQ [Alpine image](https://github.com/gmr/alpine-rabbitmq-autocluster.git) (~42MB) with the autocluster plugin.

The default credentials for the management web-ui is `guest/guest`.

### Install GPG keys

Start by retrieving the RPM signing key

```sh
gpg --keyserver hkps.pool.sks-keyservers.net --recv-keys 0x6B73A36E6026DFCA
```

```sh
wget https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
gpg --import rabbitmq-release-signing-key.asc
```

You can avoid GPG warnings by signing the key after you've imported it.
```
gpg --sign-key 0x6B73A36E6026DFCA
```

### Install yum repositories

[rabbitmq-erlang.repo](blob/master/files/rabbitmq-erlang.repo)

```ini
[rabbitmq-erlang]
name=rabbitmq-erlang el-$releasever
baseurl=https://dl.bintray.com/rabbitmq/rpm/erlang/20/el/$releasever
gpgcheck=1
gpgkey=https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
repo_gpgcheck=0
enabled=1
```

[![Download](https://api.bintray.com/packages/rabbitmq/rpm/erlang/images/download.svg) ](https://bintray.com/rabbitmq/rpm/erlang/%5FlatestVersion)

[rabbitmq-server-3.6.12-1.el7.noarch.rpm](https://github.com/rabbitmq/rabbitmq-server/releases/download/rabbitmq_v3_6_12/rabbitmq-server-3.6.12-1.el7.noarch.rpm)

[autocluster-0.9.0.ez](https://github.com/rabbitmq/rabbitmq-autocluster/releases/download/0.9.0/autocluster-0.9.0.ez)

[rabbitmq_aws-0.9.0.ez](https://github.com/rabbitmq/rabbitmq-autocluster/releases/download/0.9.0/rabbitmq_aws-0.9.0.ez)


### Official plugins

| Plugin name | Description |
| ----------- | ----------- |
| rabbitmq_auth_backend_ldap | Authentication / authorisation plugin using an external LDAP server. |
| rabbitmq_auth_mechanism_ssl | Authentication mechanism plugin using SASL EXTERNAL to authenticate using SSL client certificates. |
| rabbitmq_consistent_hash_exchange | Consistent hash exchange type. |
| rabbitmq_federation | Scalable messaging across WANs and administrative domains. |
| rabbitmq_federation_management | Shows federation status in the management API and UI. Only of use when using rabbitmq_federation in conjunction with rabbitmq_management. In a heterogenous cluster this should be installed on the same nodes as rabbitmq_management. |
| rabbitmq_management | A management / monitoring API over HTTP, along with a browser-based UI. |
| rabbitmq_management_agent | When installing the management plugin on some of the nodes in a cluster, you must install rabbitmq_management_agent on all of the nodes in the cluster. You can install the full management plugin on as many of the nodes as you want. |
| rabbitmq_mqtt | An adapter implementing the MQTT 3.1 protocol. |
| rabbitmq_shovel | A plug-in for RabbitMQ that shovels messages from a queue on one broker to an exchange on another broker. |
| rabbitmq_shovel_management | Shows shovel status in the management API and UI. See the plugin README for this plugin. Only of use when using rabbitmq_shovel in conjunction with rabbitmq_management. In a heterogenous cluster this should be installed on the same nodes as rabbitmq_management. |
| rabbitmq_stomp | Provides STOMP protocol support in RabbitMQ. |


[Official](https://www.rabbitmq.com/plugins.html) plugins included in the binary release.


`rabbitmq-plugins enable rabbitmq_federation`

### Federation

* [Federation](https://www.rabbitmq.com/federation.html), Enables messaging between brokers in different clusters and/or on different versions of RabbitMQ/Erlang and is tolerant to high latency WAN links.
* [rabbitmq-federation-management](https://github.com/rabbitmq/rabbitmq-federation-management), Plugin to manage federation


### Testing

* [amqpc](https://github.com/gocardless/amqpc.git) is CLI tool for testing AMQP brokers


### Monitoring

* [Datadog](https://docs.datadoghq.com/integrations/rabbitmq/) integration


### Database Integration

* [pgsql-listen-exchange](https://github.com/gmr/pgsql-listen-exchange) translates PostgreSQL's NOTIFY messages to AMQP messages and publishes them to bound queues.


### Administration / CLI

* [rabbitmqadmin](https://www.rabbitmq.com/management-cli.html), RabbitMQ Management command line tool
* [amqp-utils](https://github.com/dougbarth/amqp-utils), command line utils for interacting with an AMQP based queue (in Ruby)
* [amqptools](https://github.com/rmt/amqptools), command line AMQP clients (in C)


### Community Plugins

* [rabbitmq_management_themes](https://github.com/rabbitmq/rabbitmq-management-themes), Customize the management web UI look.
* [autocluster](https://github.com/rabbitmq/rabbitmq-autocluster), Automatically cluster RabbitMQ nodes using Consul, etcd or DNS for service discovery.
* [rabbitmq-auth-backend-ip-range](https://github.com/gotthardp/rabbitmq-auth-backend-ip-range), Provides the ability for your RabbitMQ server to perform authorisation based on the client IP address.
* [rabbitmq-lager](https://github.com/hyperthunk/rabbitmq-lager), [Basho's Lager logging](https://github.com/basho/lager) syslog-friendly framework as a RabbitMQ plugin.


### Further reading

* [Production checklist](https://www.rabbitmq.com/production-checklist.html)


## Terraform

* [rabbitmq-aws-cluster](https://github.com/ulamlabs/rabbitmq-aws-cluster), simple terraform for HA RabbitMQ in an ASG.
