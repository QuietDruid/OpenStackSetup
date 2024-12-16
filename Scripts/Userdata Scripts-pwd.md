#cloud-config

# User creation with sudo access
users:
  - name: cloudadmin
    gecos: Cloud Admin User
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    groups: [sudo, adm, systemd-journal]
    shell: /bin/bash
    lock_passwd: false
    passwd: $6$rounds=4096$tqAgdXYclLfS$3cddIJ1Q8zDfStQzjOOoe2QXXZu/KNbuEtKKjSb0lOmqvUSrcvJ4QIw67B3Ru/u8Q5PaSqC59jXH6ZyqnMMmh.

# Enable password authentication
ssh_pwauth: true

# Optional: Add SSH key (recommended for additional security)
# ssh_authorized_keys:
#   - ssh-rsa AAAA... your-public-key

# Ensure system is updated on first boot
package_upgrade: true

# Additional system packages you might want to install
packages:
  - vim
  - tmux
  - curl