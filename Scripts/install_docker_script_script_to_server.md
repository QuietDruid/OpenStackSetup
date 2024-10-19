#!/bin/bash

# Variables
DOCKER_INSTALL_SCRIPT="docker_install.sh"  # Path to your Docker installation script
REMOTE_USER="your_remote_user"               # The user you use to SSH into the remote server
SERVERS_FILE="servers.txt"                   # File containing a list of target servers

# Iterate over each server in the servers.txt file
while IFS= read -r server
do
  echo "Copying Docker installation script to $server"

  # Use scp to copy the installation script to the remote server
  scp "$DOCKER_INSTALL_SCRIPT" "$REMOTE_USER@$server:/tmp/"

  echo "Docker installation script copied to $server"
done < "$SERVERS_FILE"

echo "All servers processed."
