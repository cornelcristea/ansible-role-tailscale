# Ansible Role: Tailsclae

## Description

Ansible role to deploy **Tailscale** as docker containers, to have a VPN that keeps your web browsing secure while also letting you access any of your devices, no matter where you are

## Requirements

* Docker (must be installed on the target hosts)

## Installation

```bash
ansible-galaxy install cornelcristea.tailscale
```

## Variables

The role uses the following variables:

| Name | Default | Description |
|---------|---------|-------------|
| `tailscale_auth_key` | *(empty)* | Auth key used to authenticate the node to Tailscale. Generate it from the Tailscale admin panel: https://login.tailscale.com/admin/settings/keys |
| `tailscale_dir` | `/etc/tailscale` | Directory where Tailscale state, configuration, and socket files are stored inside the container or host |
| `tailscale_docker_image` | `tailscale/tailscale:stable` | Docker image used to run the Tailscale client |
| `tailscale_hostname` | `{{ ansible_hostname }}` | Hostname that will appear for this node in the Tailscale admin console |
| `tailscale_port` | `41641` | UDP port used by Tailscale for peer-to-peer WireGuard connections |

## Playbook Example

```yaml
- hosts: servers
  roles:
    - role: cornelcristea.tailsclae
      vars:
        tailscale_auth_key: "my-encrypted-auth-key"
```

## How to Contribute

We welcome contributions! Here’s how you can help improve this role:

1. **Fork the repository**    
  Click the `Fork` button at the top of the repository.

2. **Clone your fork locally**

  ```bash
  git clone https://github.com/cornelcristea/ansible-role-tailscale.git
  cd ansible-role-tailscale
  ```

3. **Create a new branch**

  ```bash
  git checkout -b my-feature-branch
  ```

  * Make your changes following Ansible best practices.
  * Add or update tests if applicable.
  * Update the README for any new variables or features.
  * Test your changes:
```bash
ansible-playbook -i test/inventory test/test.yml 
```
 * Run molecule test:
```bash
molecule test
```

4. **Commit and push your changes**

  ```bash
  git add .
  git commit -m "Add feature XYZ"
  git push origin my-feature-branch
  ```

5. **Open a Pull Request (PR)**   
Submit a PR from your branch. Include a clear description of your changes and why they’re needed.

### We appreciate your contributions!
