
1. Set up base distro - I like debian containers
2. Set up github-runner user for unprivileged stuff [Github-runner](obsidian://open?vault=Ygg&file=Openstack%2FScripts%2FGithub-runner%20script)
3. update, upgrade, and install packages for a usage:
	1. curl
	2. vim
	3. sudo
	4. docker ([[Docker]]) or [Docker-Official](https://docs.docker.com/engine/install/debian/)
4. ssh-keygen - generate keys so that the runner is able to ssh into production hosts
	1. keep private on deployer
	2. copy public key to authorized_keys on production host
5. Go to github repo -> settings -> actions -> runner and set up self-hosted runner
	1. Add any env variables as need in the secrets -> repository secrets
	2. 