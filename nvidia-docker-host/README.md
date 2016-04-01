# Setting up a host for nvidia-docker containers

## Ubuntu

1. Follow `http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-apt-ubuntu` to install Ansible.
   (In short, `sudo apt-add-repository ppa:ansible/ansible && sudo apt-get update && sudo apt-get install ansible`.)

2. Make your server's private key readable at `~/.ssh/nvidia-docker-host.pem`.

3. Set the host ip address / cname to the contents of the local file `inventory`.

4. Run `ansible-playbook setup.yml -i inventory`.

5. If the playbook completes, you will have run the matrix multiply demo on a GPU container on your nvidia-docker-host.
