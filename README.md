# Annotate_Work
Annotation software developed at work




Installation Guide:

sudo apt-get update
sudo apt-get --no-install-recommends install -y \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"
sudo apt-get update
sudo apt-get --no-install-recommends install -y docker-ce docker-ce-cli containerd.io



sudo groupadd docker
sudo usermod -aG docker $USER



sudo apt-get --no-install-recommends install -y python3-pip python3-setuptools
sudo python3 -m pip install setuptools docker-compose



sudo apt-get --no-install-recommends install -y git
git clone https://github.com/AronIS98/VinnuMappa.git
cd cvat


docker-compose up -d


docker exec -it cvat bash -ic 'python3 ~/manage.py createsuperuser'


docker-compose down


CVAT on Google (GCP):
First see the following video tutorial on how to create a GCP server that is able to run CVAT.
-----Video in progress-----
next type:
sudo nano docker-compose.yml
locate: CVAT_HOST: LOCALHOST
and change LOCALHOST to the servers external ip address:
![external_IP](https://user-images.githubusercontent.com/54920024/129982693-b0a47c8d-47a2-4e43-b9a2-e63f15a764c3.png)

CVAT with Automatic Annotation support:
docker-compose -f docker-compose.yml -f components/serverless/docker-compose.serverless.yml up -d
finally:
    docker exec -it cvat /bin/bash
    python3 manage.py createsuperuser

---ATTENTION---
If you if you ever get the error "ERROR: Pool overlaps with other one on this address space" is giving you pain, type:
    either typing:
    docker network prune
    and compose docker up again using chosen method.
