# Backend Server Setup and Deployment

## Create Server

[Digital Ocean](https://digitalocean.com/) Welcome to the developer cloud. They make it simple to launch in the cloud and scale up as you grow—whether you’re running one virtual machine or ten thousand.

1. Create a \$5 Droptlet with Ubuntu 18.04, selecting a temporary password option.
2. Create a domain entry pointng to the server
3. Copy the IP Address when the server is created.
4. Login to the server with [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) on Windows or ssh command on mac
   4.1 ssh root@SERVER_IP_ADDRESS

## Update Server

1. Update server components list with `apt update`
2. Upgrade server components with `apt upgrade`

## Add Normal Sudo User and disable Root remote Login

1. `adduser username` Where username is the name that you want to use
   1.1 Type password and information needed
2. `usermod -aG sudo username` Where username is the user created in previous step
3. Test user conenction exits the server and acces now with `username` instead of `root`
4. Log back with root and execute `nano /etc/ssh/sshd_config`
5. Change `PermitRootLogin yes` to `PermitRootLogin no` and `#PermitEmptyPasswords no` to `PermitEmptyPasswords no`
6. Exit and save with `Ctrl+x` and then `Y` and finally `Enter`
7. Restart ssh with `/etc/init.d/ssh restart`
8. Exit the server

## Add Firewall

1. Login with your username account (not root)
2. Type `sudo ufw status` to view firewall status
3. Install Firewall with `sudo apt-get install ufw`
4. Enable Ports on Firewall
   4.1 `sudo ufw allow ssh`
   4.2 `sudo ufw allow http`
   4.3 `sudo ufw allow https`
5. Enable Firewall `sudo ufw enable`
6. Type `sudo ufw status` to view firewall status

## Install Nginx (HTTP Server)

1. Install with `sudo apt install nginx`
2. Start nginx `systemctl start nginx`

## Install Node

1. Install NVM with `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash`
2. Install Node.js with this command: `nvm install 12.13.1`

## Install Yarn

1. `curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -`
2. `echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list`
3. `sudo apt-get update && sudo apt-get install --no-install-recommends yarn`
4. Open .bashrc to add yarn bin to path with `nano ~/.bashrc`
5. Add at the end ```export PATH="$PATH:`yarn global bin`"```
6. Exit and save with `Ctrl+x` and then `Y` and finally `Enter`


## Install PM2

[PM2](https://pm2.keymetrics.io/)  PM2 is a daemon process manager that will help you manage and keep your application online 24/7 

1. `yarn global add pm2`

## Run API

1. Clone Github repo with `git clone GITHUB_REPO_URL`
2. Install project dependencies going inside the folder and type `yarn`
3. Create .env file with `nano .env`
4. Run in PM2 with `pm2 start yarn --interpreter bash --name api -- prod`

## Add Nginx Reverse Proxy information

1. `sudo nano /etc/nginx/conf.d/api.conf`
2. Type
```bash
server {
        listen          80;
        listen          [::]:80;
        server_name     api.rodolfo-roman.site;

        location / {
                proxy_pass http://localhost:3000;
        }

}
```
3. Exit and save with `Ctrl+x` and then `Y` and finally `Enter`
4. Test configuration with `sudo nginx -t`
5. Test configuration with `sudo nginx -s reload`


## Add Certbot to have Https on the server

```bash
    sudo apt-get update
    sudo apt-get install software-properties-common
    sudo add-apt-repository universe
    sudo add-apt-repository ppa:certbot/certbot
    sudo apt-get update
    sudo apt-get install certbot python-certbot-nginx
    sudo certbot --nginx
    sudo certbot certonly --nginx
```
