[Complete Intro to Containers](https://frontendmasters.com/courses/complete-intro-containers/)

[Good introductory video to docker](https://www.youtube.com/watch?v=YFl2mCHdv24)
- Check the follow up videos about docker-compose and other stuff

Here you will put all the content you know related to Docker and especially content from the FM course

# Docker commands
Docker ADD vs COPY - add goes to internet to get file (eg github) and automatically unzips file if necessary
when inside container you can use 'cat /etc/issue' to check what version&distro of Linux you are in

Kubernetes
svc - is for service in kubernetes
Node is a deployment target. It can have multiple pods.


# Terminology
A “build” is given by dev team to the test team. A “release” is formal release of the product to its customers. A build when tested and certified by the test team is given to the customers as “release”.
![Build vs Release vs Version](./assets/build-release.png)


- ```ldd /bin/bash```
     - this command is printing all libraries on which /bin/bash is dependent
