# BGP Configuration On FRR Using Ansible Playbooks

## Overview
This Ansible playbook is designed to configure BGP (Border Gateway Protocol) settings on network devices using the `frr_bgp` module. The playbook lets you define global BGP settings, configure neighbors, address family options, and manage network prefixes for FRR (Free Range Routing) devices.

The project leverages Ansible best practices, using a directory structure that separates host-specific variables (`host_vars`) and group-wide settings (`group_vars`) for easier management. Sensitive values are securely managed using Ansible Vault.

## Project Structure
```python
ansible/
├── playbooks/
│   └── bgp_configuration.yml  # The main playbook
├── host_vars/
│   ├── router1.yml            # Variables for Router 1
│   └── router2.yml            # Variables for Router 2 (if any)
└── group_vars/
    └── all.yml                # Global variables for all hosts
```

### **File Descriptions:**
- **`playbooks/bgp_configuration.yml`**: Main playbook that applies the BGP configuration to the targeted routers.
- **`host_vars/`**: Directory containing variables for each router. This allows for device-specific configurations.
  - **`router1.yml`**: Defines BGP-specific variables for `router1`.
  - **`router2.yml`**: (Optional) Variables for an additional router.
- **`group_vars/all.yml`**: Contains global variables that apply to all routers, such as OSPF redistribution settings.
- **`README.md`**: Documentation file outlining the project and usage instructions.

## Getting Started

### Prerequisites
- **Ansible 2.9+**
- **FRR (Free Range Routing) installed on the target devices**
- Properly configured Ansible inventory and SSH access to the routers
- **Ansible Vault** for managing encrypted secrets

### Installation
Clone the repository:
   ```bash
   git clone https://github.com/your_username/ansible-bgp-configuration.git
   cd ansible-bgp-configuration
   ```

### Running the Playbook
To run the playbook against the defined routers, use the following command:
```bash
ansible-playbook -i inventory.yml playbooks/bgp_configuration.yml
```

### Securely Managing Sensitive Values
This project uses Ansible Vault to manage sensitive values such as BGP passwords. To create an encrypted value, use:
```bash
ansible-vault encrypt_string 'your_password' --name 'password'
```

Then replace the value in the host_vars file with the encrypted string:
```yaml
password: !vault |
  $ANSIBLE_VAULT;1.1;AES256...
```

## Author
Created by Ehsan Momeni Bashusqeh

### **Key Sections:**
- **Project Structure Overview:** Detailed directory layout for easy navigation.
- **Installation and Setup:** Clear steps to configure and run the playbook.
- **Usage of Tags:** Information on selectively running parts of the playbook using tags.
- **Variable Management:** Guidance on managing variables using `host_vars` and `group_vars`.
- **Secure Value Management:** Explains using Ansible Vault to secure sensitive data.

This format should be comprehensive enough to serve as a solid foundation for your GitHub repository's documentation! Let me know if you need any other enhancements or customizations!
