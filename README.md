# Docker Install | OpenVAS/Greenbone

I am doing this in my Ubuntu Virtual Machine
1. Install docker with `sudo apt update`, `sudo apt upgrade`, then `sudo apt install docker.io`
2. Install Curl with `sudo apt install curl`
3. Install Docker Compose with `sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose` then `sudo chmod +x /usr/local/bin/docker-compose`
4. Test with `docker-compose --version`
5. Make sure docker is running with `sudo service docker status`. It should already be running. If not use `sudo service docker start`
6. Install container with `sudo docker run -d -p 443:443 --name openvas mikesplain/openvas`
7. Wait for everything to finish downloading by looking at your System Monitor and waiting for the CPU usage to drop to nomral levels. In the mean time, have a nice glass of wine.
8. Open FireFox and go to `https://localhost/`
9. Sign in with `admin` as username and password.

Here is the main dashboard:

SHOT1

10. Go to the Configuration tab and choose Targets.
11. Create a new Target:

SHOT2

12. Create a new Task to scan the site:

SHOT3

13. Once the scan is done, you can view the security report:

SHOT4
