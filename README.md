# Annotate_Work
Annotation software developed at work
Installation guide:
° Install Docker (& Linux).
    - https://www.docker.com/
    -
° Open VS studio or something comparable
type:
    cd cvat
    docker-compose up -d
or:
    docker-compose -f docker-compose.yml -f docker-compose.dev.yml build
    docker-compose up -d
    (docker-compose -p CUSTOMNAME up -d) if you dont want the default name

ATTENTION!
might need to run:
docker-compose -f docker-compose.yml -f components/serverless/docker-compose.serverless.yml up -d
instead

then:
    docker exec -it cvat /bin/bash
    python3 manage.py createsuperuser

IF you need to reinstall and "ERROR: Pool overlaps with other one on this address space" is giving you pain, type:
    docker network prune



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
git clone https://github.com/opencv/cvat
cd cvat


docker-compose up -d


docker exec -it cvat bash -ic 'python3 ~/manage.py createsuperuser'


docker-compose down


CVAT on Google (GCP):

CVAT with Automatic Annotation support: