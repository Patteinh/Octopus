# Octopus 🐙

Welcome to `Octopus`.

This project focuses on using Ansible, a powerful automation tool, for deploying a complex application across multiple machines without containers.

## Language and Tools 🛠️

- **Language:** Ansible (YAML)
- **Tools:** Ansible, Virtual Machines

## Project Overview 🔎

`Octopus` is about deploying the poll application (from the Popeye project) onto five different machines using Ansible.

This approach demonstrates the efficient and scalable application of configuration management in a DevOps environment.

### Features and Roles

- **Base Role:** Installs essential packages and configures the instance.
- **Redis Role:** Installs and sets up Redis.
- **PostgreSQL Role:** Installs PostgreSQL 12, sets up users and database schema.
- **Poll Role:** Uploads, installs, and runs the poll web client.
- **Worker Role:** Manages the worker service from upload to execution.
- **Result Role:** Handles the result web client service setup and execution.

### Technical Details

- **Idempotence:** Playbook executions result in no changes.
- **Systemd Management:** All services are managed by systemd and configured to start on boot.
- **Environment Variables:** Services are configured using environment variables.
- **Security:** Secure handling of passwords and sensitive data.

### Inventory and Environment

- **Inventory Groups:** Five groups each containing one instance - `redis, postgres, poll, result, and worker`.
- **Virtual Machines:** Five VMs based on Debian 10 (Buster).

### Repository Structure

Your repository should contain the following:

- **Playbook and Inventory:** `playbook.yml` and `production` inventory file.
- **Roles:** Directories for each role with their respective tasks and files.
- **Group Variables:** `group_vars/all.yml` for common configurations.
- **Service Files:** Tarballs for poll, result, and worker services.

## Installation and Usage 💾

1. Clone the repository.
2. Set up five Debian 10 VMs according to the inventory structure.
3. Run the Ansible playbook: `ansible-playbook -i production playbook.yml`.
4. Ensure idempotence by running the playbook again and checking for 0 `changed` tasks.
5. For detailed guidelines, refer to `octopus.pdf`.

## License ⚖️

This project is released under the MIT License. See `LICENSE` for more details.
