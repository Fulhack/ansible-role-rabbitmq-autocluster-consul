# Project notes


## Binary sources

`gpg --keyserver hkps.pool.sks-keyservers.net --recv-keys 0x6B73A36E6026DFCA`
```wget https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
gpg --import rabbitmq-release-signing-key.asc```

Trust by signing the key `gpg --sign-key 0x6B73A36E6026DFCA`

files/rabbitmq-erlang.repo
```config
[rabbitmq-erlang]
name=rabbitmq-erlang el-$releasever
baseurl=https://dl.bintray.com/rabbitmq/rpm/erlang/20/el/$releasever
gpgcheck=1
gpgkey=https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
repo_gpgcheck=0
enabled=1
```

[rabbitmq-server-3.6.12-1.el7.noarch.rpm](https://github.com/rabbitmq/rabbitmq-server/releases/download/rabbitmq_v3_6_12/rabbitmq-server-3.6.12-1.el7.noarch.rpm)

### Plugins

https://github.com/rabbitmq/rabbitmq-autocluster/releases/download/0.9.0/autocluster-0.9.0.ez
https://github.com/rabbitmq/rabbitmq-autocluster/releases/download/0.9.0/rabbitmq_aws-0.9.0.ez


rabbitmq_auth_backend_ldap
Authentication / authorisation plugin using an external LDAP server.

rabbitmq_auth_mechanism_ssl
Authentication mechanism plugin using SASL EXTERNAL to authenticate using SSL client certificates.

rabbitmq_consistent_hash_exchange
Consistent hash exchange type.

rabbitmq_federation
Scalable messaging across WANs and administrative domains.

rabbitmq_federation_management
Shows federation status in the management API and UI. Only of use when using rabbitmq_federation in conjunction with rabbitmq_management. In a heterogenous cluster this should be installed on the same nodes as rabbitmq_management.

rabbitmq_management
A management / monitoring API over HTTP, along with a browser-based UI.

rabbitmq_management_agent
When installing the management plugin on some of the nodes in a cluster, you must install rabbitmq_management_agent on all of the nodes in the cluster. You can install the full management plugin on as many of the nodes as you want.

rabbitmq_mqtt
An adapter implementing the MQTT 3.1 protocol.

rabbitmq_shovel
A plug-in for RabbitMQ that shovels messages from a queue on one broker to an exchange on another broker.

rabbitmq_shovel_management
Shows shovel status in the management API and UI. See the plugin README for this plugin. Only of use when using rabbitmq_shovel in conjunction with rabbitmq_management. In a heterogenous cluster this should be installed on the same nodes as rabbitmq_management.

rabbitmq_stomp
Provides STOMP protocol support in RabbitMQ.

https://www.rabbitmq.com/plugins.html

### Federation

Enables messaging between brokers in different clusters and/or on different versions of RabbitMQ/Erlang.

Link clusters (with different versions) together over WAN.

`rabbitmq-plugins enable rabbitmq_federation`

https://www.rabbitmq.com/federation.html
https://github.com/rabbitmq/rabbitmq-federation-management

### Testing

[amqpc](https://github.com/gocardless/amqpc.git) is CLI tool for testing AMQP brokers

### Monitoring

[Datadog](https://docs.datadoghq.com/integrations/rabbitmq/) integration

### Database Integration

[pgsql-listen-exchange](https://github.com/gmr/pgsql-listen-exchange) translates PostgreSQL's NOTIFY messages to AMQP messages and publishes them to bound queues. 

### Administration

[rabbitmqadmin](https://www.rabbitmq.com/management-cli.html), the RabbitMQ Management command line tool
[amqp-utils](https://github.com/dougbarth/amqp-utils), command line utils for interacting with an AMQP based queue (in Ruby)
[amqptools](https://github.com/rmt/amqptools), command line AMQP clients (in C)

### Community Plugins

[rabbitmq_management_themes](https://github.com/rabbitmq/rabbitmq-management-themes), Adds the possibility to customize the management web UI look.
[autocluster](https://github.com/rabbitmq/rabbitmq-autocluster), Adds the possibility to automatically cluster RabbitMQ nodes using Consul, etcd or DNS for service discovery.

[rabbitmq-auth-backend-ip-range](https://github.com/gotthardp/rabbitmq-auth-backend-ip-range), Provides the ability for your RabbitMQ server to perform authorisation based on the client IP address.

[rabbitmq-lager)(https://github.com/hyperthunk/rabbitmq-lager), [Basho's Lager logging](https://github.com/basho/lager) framework as a RabbitMQ plugin.


### Further reading

https://www.rabbitmq.com/production-checklist.html


