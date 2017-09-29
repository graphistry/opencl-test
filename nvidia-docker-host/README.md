# Setting up a host for nvidia-docker containers

## You May Already Be Done

1. You may already have nvidia-docker setup. You can test via:

Run `nvidia-docker run --rm graphistry/cljs:1.1 npm test`

Expected output:

```
> cljs@0.0.1 test /app
> ./tests/add.js

Ran
Success
```

2. Check a more involved demo with visual verification:

* Run `sudo nvidia-docker run -p 80:3001 -d graphistry/cljs:1.0`
* Go to `257.257.257.257/?mode=opencl`
* You should see two pandas, one in black and white. The compute time should be < 20ms: refresh the page if not.
* Stop the test: `docker ps` to get the `Container ID` and then `docker stop MY_CONTAINER_ID`


## Ubuntu Xenial

1. Follow `http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-apt-ubuntu` to install Ansible.
   (In short, `sudo apt-add-repository ppa:ansible/ansible && sudo apt-get update && sudo apt-get install ansible`.)

2. Make your remove server's private key readable at `~/.ssh/nvidia-docker-host.pem`.

3. Change the contents of the file `inventory` to the host ip address / cname. If your IPv4 address is 257.257.257.257, `echo 257.257.257.257 > inventory`.

4. Run `ansible-playbook setup.yml -i inventory  -e 'ansible_python_interpreter=/usr/bin/python3'`. This includes some tests; if this finishes cleanly, you will have run edge detection using Javascript on the CPU and OpenCL compiled to the GPU in a container.

5. For additional verification, try to run the cljs convolution demo above.
