# Setting up a host for nvidia-docker containers

## RHEL

0. Start with a relatively recent RHEL 7.2 image and give it over 20GB of disk on the root partition.

1. Follow `http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum` to install Ansible.

2. Make your server's private key readable at `~/.ssh/nvidia-docker-host.pem`.

3. Change the contents of the file `inventory` to the host ip address / cname. If your IPv4 address is 257.257.257.257, `echo 257.257.257.257 > inventory`.

4. Run `ansible-playbook setup.yml -i inventory`. This includes some tests; if this finishes cleanly, you will have run the cljs convolution demo in a GPU container.

5. For visual verification, run the cljs convolution demo manually: run `sudo docker run -p 80:3001 -d graphistry/cljs:1.0` and then go to `257.257.257.257/?mode=opencl`.
