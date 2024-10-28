# Node Exporter Installation Playbook

## Overview

This Ansible playbook is designed to automate the installation and configuration of Prometheus Node Exporter on target Linux systems. It downloads the specified version of Node Exporter, sets up a system user with limited privileges, and configures the systemd service to ensure Node Exporter runs as a background service.

## Features

- Downloads the specified version of Node Exporter.

- Creates a dedicated system user for running Node Exporter with /bin/false as the default shell for security.

- Configures Node Exporter as a systemd service for easy management.

- Ensures the service starts on boot and is running.

## Requirements

- Ansible installed on your local machine or control node.

- Target servers must support SSH connections and have root privileges (or be sudo-enabled).

## Variables

- `node_exporter_version`: Specifies the version of Node Exporter to be installed. This can be passed as an extra variable when running the playbook.

## Usage

### Clone the Repository

Clone this repository to your local machine:

```bash
$ git clone https://github.com/krasimirstoev/node-exporter-ansible-playbook.git
```

### Run the Playbook

Use the following command to run the playbook:
```bash
$ ansible-playbook install.yml -i hosts.ini -e node_exporter_version=1.6.1
```
- Replace ```hosts.ini``` with the inventory file specifying the target hosts.

- Use the ```-e``` flag to specify the desired version of Node Exporter.

### Inventory File Example

The inventory file (```hosts.ini```) should contain the target servers where you want to install Node Exporter. Example:
```bash
[node_exporter_servers]
server1 ansible_host=192.168.1.101 ansible_user=root
server2 ansible_host=192.168.1.102 ansible_user=root
```
# License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
