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

#### Optional Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| default_user | rabbitmq | *Username* | string | Default username for rabbitmq |
| default_password | Strong@321 | *Password* | string | Default password for rabbitmq user |
| cluster_partition_strategy | autoheal | <ul><li>autoheal</li><li>pause_minority</li><li>pause_if_all_down</li></ul> | string | Default partitining strategy for rabbitmq cluster |
| rabbitmq_plugins | <ul><li>rabbitmq_management</li><li>rabbitmq_prometheus</li></ul> | *Plugin Name* | list | List of plugins which needs to be installed |


### Usage

The inventory for rabbitmq role should look like this:-

```ini
[rabbitmq]
rabbitmqnode1 ansible_ssh_host=34.210.213.107 node_type=master
rabbitmqnode2 ansible_ssh_host=35.167.30.255 node_type=follower
rabbitmqnode3 ansible_ssh_host=34.212.230.40 node_type=follower

[rabbitmq:vars]
ansible_ssh_user=ec2-user
```

**Make sure your first node should have node_type=master**

An example playbook should look like this:-

```yaml
---
- hosts: rabbitmq
  roles:
    - rabbitmq
```

and for running the ansible role, we will use ansible cli.

```shell
ansible-playbook -i tests/inventory tests/test.yml
```
## Author

**[Abhishek Dubey](abhishek.dubey@opstree.com)**
