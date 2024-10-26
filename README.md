# AptlyServed

AptlyServed is an Ansible-powered solution designed to streamline the deployment and management of a local APT repository that is served through Nginx. This project encapsulates best practices and modular design, making deploying and managing Debian package repositories on your network easy.

## Features

- **Automatic Installation:** Sets up and configures Nginx to serve your APT repository.
- **Easy Package Management:** Easily add or update Debian packages within your repository.
- **Modular Design:** Utilizes Ansible roles to clearly separate concerns.
- **Scalable:** Suitable for everything from small labs to large enterprise environments.

## Requirements

- An Ubuntu Server (18.04 or newer)
- Ansible 2.9 or higher
- SSH access to the target server
- Sudo privileges on the server

## Getting Started

### Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/alilotfi23/AptlyServed.git
   cd AptlyServed
   ```

2. **Set Up Inventory:**
   Edit the `inventory` file to include the IP addresses of the servers where you want to deploy the repository.

3. **Configure Variables:**
   Open the `vars/main.yml` to set up necessary configurations like repository directory, server name, etc.

4. **Run the Playbook:**
   ```bash
   ansible-playbook -i inventory setup_repo.yml
   ```

### Directory Structure

```
.
AptlyServed/
├── ansible.cfg                # Ansible configuration file
├── inventory                  # Inventory file defining hosts and groups
├── setup_repo.yml             # Main Ansible playbook
├── roles/
│   ├── base_setup/
│   │   └── tasks/
│   │       └── main.yml       # Tasks for basic server setup
│   ├── nginx/
│   │   ├── tasks/
│   │   │   └── main.yml       # Tasks for installing and configuring Nginx
│   │   ├── handlers/
│   │   │   └── main.yml       # Handlers for reloading Nginx
│   │   └── templates/
│   │       └── repo.conf.j2   # Jinja2 template for Nginx configuration
│   └── repository/
│       ├── tasks/
│       │   └── main.yml       # Tasks for setting up the repository
│       └── handlers/
│           └── main.yml       # Handlers for repository actions
└── vars/
    └── main.yml               # Variables used across the roles

```

### Usage

After deployment, your APT repository will be accessible via the configured domain or IP address. You can add `.deb` files to your repository and run the playbook to update the metadata automatically.

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request
