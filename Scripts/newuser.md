#!/bin/bash

# Define variables
USER="ansi"
SSH_KEY_PATH="~/.ssh/id_rsa.pub"  # Path to the public key you want to use
REMOTE_USER="your_remote_user"     # The user you use to SSH into the remote server
SERVERS_FILE="servers.txt"         # File containing a list of target servers

# Create a temporary bash script to be copied to the remote servers
cat <<'EOF' > /tmp/create_user.sh
#!/bin/bash

# Variables
USER="ansi"
PUB_KEY="~/.ssh/authorized_keys"

# Create the ansi user and add the user to the sudo group
sudo useradd -m -s /bin/bash "$USER"
sudo usermod -aG sudo "$USER"

# Set passwordless sudo for the ansi user
echo "$USER ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/$USER

# Create the .ssh directory and authorized_keys file
sudo mkdir -p /home/$USER/.ssh
sudo touch /home/$USER/.ssh/authorized_keys

# Set permissions for the .ssh directory and authorized_keys file
sudo chmod 700 /home/$USER/.ssh
sudo chmod 600 /home/$USER/.ssh/authorized_keys
sudo chown -R $USER:$USER /home/$USER/.ssh

# Disable password login for the ansi user (set ssh keys only)
sudo sed -i '/^PasswordAuthentication/s/yes/no/' /etc/ssh/sshd_config
sudo service sshd restart
EOF

# Iterate over each server in the servers.txt file
while IFS= read -r server
do
  echo "Deploying to $server"

  # Copy the create_user.sh script and public key to the remote server
  scp /tmp/create_user.sh "$REMOTE_USER@$server:/tmp/"
  scp "$SSH_KEY_PATH" "$REMOTE_USER@$server:/tmp/id_rsa.pub"

  # Run the script on the remote server
  ssh "$REMOTE_USER@$server" 'bash /tmp/create_user.sh'

  # Append the public key to the ansi user’s authorized_keys
  ssh "$REMOTE_USER@$server" 'sudo cat /tmp/id_rsa.pub >> /home/ansi/.ssh/authorized_keys'

  # Clean up the remote server
  ssh "$REMOTE_USER@$server" 'sudo rm /tmp/create_user.sh /tmp/id_rsa.pub'

done < "$SERVERS_FILE"

# Remove the temporary script
rm /tmp/create_user.sh

echo "User creation and SSH setup completed."
