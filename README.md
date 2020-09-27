## Ansible Role: RabbitMQ

Ansible role to setup, manage RabbitMQ cluster/standalone

Some of the highlighting features are:-

  - Cluster and Standalone setup of RabbitMQ
  - User management for RabbitMQ
  - Management console setup for UI management
  - Prometheus metrics support for detailed insights

This role supports RedHat family right now, other OS support is under construction.

### Requirements

**No third party requirement is needed by this role**

### Roles Variables

Roles variables are categorized into two divisions i.e. Mandatory and Optional.

#### Mandatory Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| create_cluster | true | <ul><li>true</li><li>false</li></ul> | boolean | RabbitMQ setup mode is cluster or standalone |
| rabbitmq_users.name | monitoring | *Username* | string | Username for rabbitmq setup |
| rabbitmq_users.password | Strong@321 | *Password* | string | Password for rabbitmq username |
| rabbitmq_users.tags | monitoring | *Tags* | string | Some special tags for identification |
| rabbitmq_users.vhosts | / | *Vhost Path* | string | Vhost path for user access |
