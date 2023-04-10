# Ansible Create Mgmt User

This Ansible project creates and configures a management user (mgmt) on target machines, and secures SSH access for the user. The playbook has been optimized for readability and maintainability by organizing tasks into roles and using handlers to restart services only when necessary.

## File Structure

```bash
.
├── ansible.cfg (optional)
├── inventory.ini (optional)
├── playbook.yml
└── roles
├── ssh_config
│ ├── handlers
│ │ └── main.yml
│ └── tasks
│ └── main.yml
└── user_mgmt
└── tasks
└── main.yml
```

## Usage

1. Ensure you have Ansible installed on your control machine.
2. Clone this repository or copy the provided file structure to your control machine.
3. Modify the `inventory.ini` file (if applicable) to include the target machines you want to apply the changes to.
4. Run the playbook using the following command:

```bash
ansible-playbook -i inventory.ini playbook.yml
```

f you don't have a separate inventory file or are using the default settings from `ansible.cfg`, the command should be:

```bash
ansible-playbook playbook.yml
```

## Roles

### User Management (user_mgmt):

This role is responsible for:
i
- Creating the `mgmt` user
- Adding the `mgmt` user to the `sudo` group
- Configuring passwordless `sudo` for the mgmt user
- Copying the SSH public key from the control machine to the target machines for the `mgmt` user

## SSH Configuration (ssh_config)

This role is responsible for:

- Disabling password authentication in the SSH configuration
- Restarting the SSH service if changes have been made to the configuration
