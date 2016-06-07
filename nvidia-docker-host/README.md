# Setting up a host for nvidia-docker containers

## Ubuntu

0. Start with a relatively recent Ubuntu Trusty image (available at https://cloud-images.ubuntu.com/locator/ec2/ ) and give it over 20GB of disk on the root partition. (If installing from the stock AWS Ubuntu image, do a dist-upgrade first.)

1. Follow `http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-apt-ubuntu` to install Ansible.
   (In short, `sudo apt-add-repository ppa:ansible/ansible && sudo apt-get update && sudo apt-get install ansible`.)

2. Make your server's private key readable at `~/.ssh/nvidia-docker-host.pem`.

3. Change the contents of the file `inventory` to the host ip address / cname. If your IPv4 address is 257.257.257.257, `echo 257.257.257.257 > inventory`.

4. Run `ansible-playbook setup.yml -i inventory`. This includes some tests; if this finishes cleanly, you will have run edge detection using Javascript on the CPU and OpenCL compiled to the GPU in a container.

5. For additional verification, try to run the cljs convolution demo: run `sudo docker run -p 80:3001 -d graphistry/cljs:1.0` and then go to `257.257.257.257/?mode=opencl`.
