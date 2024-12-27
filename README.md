# Rocky Linux CIS Benchmark Project

This repository provides an Ansible-based implementation for configuring Rocky Linux systems according to the CIS Benchmark guidelines. The configurations are divided into **Level 1** and **Level 2** security profiles, ensuring compliance with industry standards.

## Features

- **Level 1**: Basic security measures that balance usability and protection.
- **Level 2**: Advanced security configurations for environments requiring stricter compliance.
- **Unified Playbook**: The `site.yml` file combines Level 1 and Level 2 configurations for flexible deployments.
- Modular structure with roles, tasks, and templates.

## Repository Structure

- **level1.yml**: Playbook for Level 1 CIS Benchmark configuration.
- **level2.yml**: Playbook for Level 2 CIS Benchmark configuration.
- **site.yml**: Master playbook to apply both Level 1 and Level 2 configurations.
- **hosts**: Inventory file for specifying target systems.
- **tasks**, **templates**, and other directories: Organized structure for Ansible roles.

## Getting Started

### Prerequisites

1. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html).
2. Ensure SSH access to target systems is configured.
3. Clone this repository.

### Clone the Repository

```bash
git clone https://github.com/electromech-cpl/rockylinux-cis-project.git
cd rockylinux-cis-project
```

### Edit the Hosts File

Before running the playbooks, open the `hosts` file in this repository and configure it with the IP address, username, and PEM key of the target system.

Example:

```ini
[rockylinux_ec2]
remote_system_ip ansible_user=your_user

[rockylinux_ec2:vars]
ansible_user=your_user
ansible_ssh_private_key_file=/your/pam/key/pem/path/
```

### Running the Playbooks

#### Apply Level 1 Configuration

```bash
ansible-playbook -i hosts level1.yml --tags "level1"
```

#### Apply Level 2 Configuration

```bash
ansible-playbook -i hosts level2.yml --tags "level2"
```

#### Apply Both Levels

```bash
ansible-playbook -i hosts site.yml --tags "level1,level2"
```

### Testing

The repository includes Molecule testing configurations. To test the configurations, ensure Molecule is installed and run:

```bash
molecule test
```

## Contributing

Contributions are welcome! If you find an issue or have suggestions for improvement, please create a pull request or open an issue in this repository.

## License

This project is licensed under the [MIT License](LICENSE).

## Author Information

Developed by Disha Rajyaguru and the team at Electromech CPL.

## Support

For any issues, please open an issue in the [GitHub repository](https://github.com/electromech-cpl/rockylinux-cis-project.git).
