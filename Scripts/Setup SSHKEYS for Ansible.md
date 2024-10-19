#!/bin/bash

# Define the public key file
PUB_KEY="~/.ssh/id_rsa.pub"

# Define the user (change 'your_user' to your target remote user)
USER="your_user"

# Iterate over each server in the list
while IFS= read -r server
do
  echo "Copying key to $server"
  
  # Use scp to copy the key to each server
  scp $PUB_KEY "$USER@$server:/tmp/id_rsa.pub"
  
  # SSH into the server to append the key to the authorized_keys file
  ssh "$USER@$server" 'cat /tmp/id_rsa.pub >> ~/.ssh/authorized_keys && rm /tmp/id_rsa.pub'
  
done < servers.txt

echo "SSH key copied to all servers."


