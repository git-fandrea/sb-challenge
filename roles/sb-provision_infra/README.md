# sb-provision_infra

This role is just and exercise. It provision VMs with their own keys and SG if not alredy present, it also create an ELB in front of the VMs

# Requirements

* AWS credential
* Ansible >= 2.5
* boto
* boto3
* python >= 2.6

# Role Variables

See default/main.yml for example

    keypair_name: "my_aws_keypair"
    instance_type: t2.micro
    security_group_VM: "sg for VM default to ssh"
    security_group_ELB: "sg for ELB default to 80"
    security_group_VPC: "sg for VPC networking"
    ami_image: ami-0bdb1d6c15a40392c
    ec2_count: instance to be present
    elb_name: "my_aws_elb"
    aws_region: eu-west-1

The default image is AMI Linux 2, and default region is AWS Ireland.

The EC2 instances and the ELB should be attached to a common SG for network communication. This is not created by the role, it's usually the default SG for the VPC.

AWS credentials are stored in a vars file to be easily encrypted as needed

    aws_access_key: "my_aws_access_key"
    aws_secret_key: "my_aws_secret_key"

# Knows issues

When adding the EC2 instances to the ELB the HealthCheck fails since the app is not yet started. Added ignore_errors to the task as a workaround
