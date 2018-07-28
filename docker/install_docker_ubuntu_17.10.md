## Install docker-ce on ubuntu 17.10

From <https://gist.github.com/levsthings/0a49bfe20b25eeadd61ff0e204f50088>


```bash
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu zesty stable"

sudo apt-get update
apt-cache policy docker-ce
sudo apt-get install docker-ce
```