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

![SHOT1](https://user-images.githubusercontent.com/42558850/141885111-82ea03ad-c614-4194-8339-999b047f7ec0.png)


10. Go to the Configuration tab and choose Targets.
11. Create a new Target:

![SHOT2](https://user-images.githubusercontent.com/42558850/141885136-7f316170-cc96-46ff-ba3e-ef9b44abc27d.png)


12. Create a new Task to scan the site:

![SHOT3](https://user-images.githubusercontent.com/42558850/141885152-8cef0a6f-79aa-4a24-918c-e75785282e33.png)

Hmm... The report for utulsa.edu was taking over 30 minutes and was stuck at 60%. Hopefully that isn't bad news. I started a new report querying google.com.

13. Once the scan is done, you can view the security report:

![SHOT4 1](https://user-images.githubusercontent.com/42558850/141885170-3f2829e3-68cc-429e-a721-575aaec3a8d9.png)

![SHOT4 2](https://user-images.githubusercontent.com/42558850/141885184-9fc0daa1-3ae6-4ad1-93f6-8885f71657a1.png)

Using the tool Professor West provided, my docker-compose.yml file is:
```
version: '3.3'
services:
    openvas:
        ports:
            - '443:443'
        container_name: openvas
        image: mikesplain/openvas
```
