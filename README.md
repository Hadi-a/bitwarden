# Install Bitwarden on your premises

### Step1: Update your instance/server
```$ sudo apt-get update -y && sudo apt-get upgrade -y```

### Step 2: Install Docker and Docker Compose 

  - Copy the setup-docker.sh file into your server 
  - Give executable permission to the file by the command ```chmod +x setup-docker.sh```
  - Now run the bash script by ```$ ./setup-docker.sh```
  - The bash script will automatically install Docker and Docker-Compose into your server.
  - You can check the docker version by ```$ docker --version ``` OR to check the service status ```$ systemctl status docker```
  - To check the docker-compose version you can use the command ```$ docker compose version```

### Step 3: Create a new user and assign the ownership

_Follow the below commands_

```
$ useradd -G docker,sudo -s /bin/bash -m -d /opt/bitwarden bitwarden
$ passwd bitwarden
$ chown -R bitwarden: /opt/bitwarden
```

### Step 4: Bitwarden Installation 

 _Switch to the new user_

```
$ su - bitwarden
$ pwd (check the working directory it should be /opt/bitwarden)
$ curl -Lso bitwarden.sh https://go.btwrdn.co/bw-sh
$ chmod +x bitwarden.sh
$ ./bitwarden.sh install
```

The script will ask you to enter your domain name, press Y for SSL, and your email address for SSL. Once it has installed all its files then we have to run the command
```$ ./bitwarden.sh start```

### DONE
-----------------
If you make any changes in the .env file then you should restart the containers by
```$ ./bitwarden.sh restart```


