# Ansible Playbook: Create User and Group on Windows Server

This repository contains an Ansible playbook to automate the creation of a user group and an administrative user on Windows Server hosts.

## Features

- Creates a custom local group for Ansible Automation Platform users.
- Creates a local user with administrative privileges.
- Adds the user to the custom group.
- Ensures idempotency by checking if the user already exists.

## Files

- `create_user_group_with_control.yml`: Main playbook to create the group and user.
- `requirements.yml`: Specifies the required Ansible collection (`ansible.windows`).

## Prerequisites

- Ansible control node (Linux/macOS/WSL recommended).
- Windows Server(s) configured for remote management (WinRM).
- Python and Ansible installed on the control node.
- The `ansible.windows` collection installed:
    ```sh
    ansible-galaxy collection install -r requirements.yml
    ```

## Usage

1. **Configure your inventory** to include your Windows hosts (e.g., `inventory.ini`):

        ```ini
        [windows_servers]
        winserver01 ansible_host=192.168.1.10 ansible_user=Administrator 
        ansible_password=YourPassword 
        ansible_connection=winrm ansible_winrm_server_cert_validation=ignore
        ```

2. **Run the playbook**:

        ```sh
        ansible-playbook -i inventory.ini create_user_group_with_control.yml
        ```

## Variables

You can customize the group and user details in the playbook under the `vars` section.

## Security Note

- Update the default password in the playbook to a secure value.
- Ensure password complexity meets your organization's policy.

## License

MIT License
