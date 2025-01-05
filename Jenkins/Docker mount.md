#creation_date:  2025-01-05 18:40
#modification_date: Sunday 5th January 2025 18:40:08
Error generating daily quote
#jenkins #docker #nexus

command to make docker available in jenkins container
```bash
sudo docker run -d -p8080:8080 -p50000:50000 \
-v jenkins_home:/var/jenkins_home \
-v /var/run/docker.sock:/var/run/docker.sock \
-v $(which docker):/usr/bin/docker jenkins/jenkins:lts
```
Then we need to give permissions to jenkins user
```bash
sudo docker exec -u 0 -it 0c3df75ccaf9 bash

chmod 666 /var/run/docker.sock
```
now we can use docker login and etc.

To push docker images to nexus
In jenkins host. We need to configure insecure-registries
```bash
sudo vim /etc/docker/daemon.json
```
and paste this
```vim
{
 "insecure-registries" : ["192.168.15.110:8083"]
}
```

and restart docker

```bash
systemctl restart docker
```

check permissions of jenkins for docker.sock

then in jenkins UI

![[Pasted image 20250105201338.png]]

![[Pasted image 20250105201356.png]]