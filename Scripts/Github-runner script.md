#!/bin/bash

apt-get update && apt-get upgrade -y

adduser github-runner

usermod -aG sudo github-runner

apt-get install vim curl sudo -y
