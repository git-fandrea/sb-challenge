# SB-aurora_RDS
This role allows you to create an Aurora cluster and master/replica using AWS cli.

## Requirements
Since this role interacts with AWS using AWS CLI, the CLI and all its depencencies must be installed. The role itself
 does not create security and parameters group, so they should be present on AWS before running the playbook.

## Role Variables

See default/main.yml for example 

## Credits

This role is based on the Tom Wright role, see https://medium.com/@tomwwright/automating-with-ansible-aurora-clusters-7272364777dd
