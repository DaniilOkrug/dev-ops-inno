# Ansible

## Details
As the virtual machines to which Ansible connects, the created VMs in VK Cloud are used.To connect to them, the key is used, the path to which is specified in the Ansible configuration file.

Inventory contains Vk hosts to connect to.

Playbook launches Docker deployment.

Roles includes a docker role for installing and configuring Docker on a VM.


## Deployment Output

```sh
ansible-playbook playbooks/dev/main.yaml
```

```sh
PLAY [Deploy Docker] ************************************************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************************************************
ok: [vk01]

TASK [docker : Install pip] *****************************************************************************************************************************************************************
included: /home/ubuntu/dev-ops-inno/ansible/roles/docker/tasks/install_pip.yml for vk01

TASK [docker : Update apt] ******************************************************************************************************************************************************************
changed: [vk01]

TASK [docker : Install python] **************************************************************************************************************************************************************
ok: [vk01]

TASK [docker : Install pip] *****************************************************************************************************************************************************************
ok: [vk01]

TASK [docker : Install docker] **************************************************************************************************************************************************************
included: /home/ubuntu/dev-ops-inno/ansible/roles/docker/tasks/install_docker.yml for vk01

TASK [docker : Install docker] **************************************************************************************************************************************************************
ok: [vk01]

TASK [docker : Install docker-compose] ******************************************************************************************************************************************************
included: /home/ubuntu/dev-ops-inno/ansible/roles/docker/tasks/install_compose.yml for vk01

TASK [docker : Install docker-compose] ******************************************************************************************************************************************************
changed: [vk01]

PLAY RECAP **********************************************************************************************************************************************************************************
vk01                       : ok=9    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

## Inventory details
```sh
ansible-inventory -i inventory/default.yml --list
```

```sh
{
    "_meta": {
        "hostvars": {
            "vk01": {
                "ansible_host": "37.139.42.39"
            }
        }
    },
    "all": {
        "children": [
            "ungrouped",
            "vk_hosts"
        ]
    },
    "vk_hosts": {
        "hosts": [
            "vk01"
        ]
    }
}
```