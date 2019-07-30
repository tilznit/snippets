### Quick and easy kali docker install.

[Install docker](https://docs.docker.com/v17.12/docker-for-mac/install/#download-docker-for-mac) (Get stable) for mac os

```
docker pull kalilinux/kali-linux-docker
docker run -t -i kalilinux/kali-linux-docker /bin/bash

apt-get install update
apt-get install upgrade

apt install kali-linux-*    # whichever [metapackage](https://www.kali.org/news/kali-linux-metapackages/?source=post_page---------------------------) you need
```

### Useful

```
docker ps -a  # view all containers
docker stop <container_id>  # stop the container
docker container prune  # remove all stopped containers
docker rm <CONTAINER ID or NAME>  # rm specific container
```

### Sources

[https://www.kali.org/news/kali-linux-metapackages/?source=post_page---------------------------](https://www.kali.org/news/kali-linux-metapackages/?source=post_page---------------------------)
[https://medium.com/@airman604/kali-linux-in-a-docker-container-5a06311624eb](https://medium.com/@airman604/kali-linux-in-a-docker-container-5a06311624eb)
[https://www.kali.org/news/official-kali-linux-docker-images/](https://www.kali.org/news/official-kali-linux-docker-images/)
