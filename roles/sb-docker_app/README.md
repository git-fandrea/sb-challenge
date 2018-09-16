# sb-docker_app

This role is just and exercise. It builds docker images with a simple web app with a nginx proxy and start containers from it.

# Requirements

* Ansible >= 2.1
* Python >= 2.6
* Docker-py >= 1.7.0
* Docker API >= 1.20

# Role Variables

See default/main.yml for example. Ansible use a dict file for providing variables for all the containters. Ansible will fail if "*_ports" variables are empty so leave them commented if you do not want to use it (see tasks for details).


```yaml
    containers:
      "my-docker-container-name-1":
        image: "anapsix/alpine-java"
        tag: "latest"
        dockerfile_name: "dockerfile_name_1"
        working_dir: "path_to_my_dir"
        exposed_ports: "8080"
        # published_ports:
        ipv4: x.x.x.x

    # Network section
    network_name: "SB-Net"
    subnet_class: "172.16.10.0/28"

    # general vars
    git_repo: "my_repo_on_github"
    dockerfile_path: "./roles/{{role_name}}/files/"
    temp_repo_path: "/tmp/sb/"
```

Insert path of your dockerfile and a path for cloning repository on remote hosts

# Known issues
There is some issues with Ansible 2.6.x. See https://github.com/ansible/ansible/issues/42162 
