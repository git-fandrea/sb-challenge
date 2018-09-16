# sb-challenge

This playbook is just and exercise. It provision a simple infrastructure on AWS, then install docker and other required packages and deploy containers with a proxy and a simple test app within the EC2 instances.

Check the roles README for further details.

# Example playbook

```yaml
- hosts: localhost
  gather_facts: False
  roles:
  - role: sb-provision_vm
    tags: provision_vm
  - role: sb-deploy_vm
    tags: deploy_vm
```

The first to roles must be runned in a single playbook since they share in-memory inventory file for the provisioned instances. You should add the provisioned EC2 instances to you inventory file before running the 2nd playbook. Instances could have been added to the inventory file but some more knowledge about how you manage your inventory is needed.

```yaml
- hosts: my_ec2_hosts
  gather_facts: False
  roles:
  - role: sb-docker_app
    tags: docker_app
```

If you are using dynamic inventory your could run your playbook against tagged_instances (see role ssb-provision_vm for tagging).

```yaml
- hosts: tag_sb
  user: ec2-user
  roles:
  - role: sb-docker_app
    tags: docker_app
```
