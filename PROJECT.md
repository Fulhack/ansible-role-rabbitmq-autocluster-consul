# Project notes


## Binary sources

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


### Further reading

https://www.rabbitmq.com/production-checklist.html


