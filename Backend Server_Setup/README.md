# Backend Server Setup and Deployment

## Create Server

[Digital Ocean](https://digitalocean.com/) Welcome to the developer cloud. They make it simple to launch in the cloud and scale up as you grow—whether you’re running one virtual machine or ten thousand.

1. Create a \$5 Droptlet with Ubuntu 20.04, selecting a temporary password option.
2. Create a domain entry pointng to the server
3. Copy the IP Address when the server is created.
4. Login to the server with [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) on Windows or ssh command on mac
   4.1 ssh root@SERVER_IP_ADDRESS

## Update Server

1. Update server components list with `apt update`
2. Upgrade server components with `apt upgrade`
3. Remove unused apps with `apt autoremove`
4. Restart `reboot now`

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

1. Install NVM with `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`
2. Install Node.js with this command: `nvm install node`

## Install PM2

[PM2](https://pm2.keymetrics.io/)  PM2 is a daemon process manager that will help you manage and keep your application online 24/7 

1. `npm i -g pm2`

## Run API

1. Clone Github repo with `git clone GITHUB_REPO_URL`
2. Install project dependencies going inside the folder and type `npm install`
3. Create .env file with `nano .env`
4. Build the app with `npm run build`
5. Run in PM2 with `pm2 start npm --name "app name" -- start`
6. Save PM2 to run on server restart`pm2 startup`
7. Save current PM2 "state" with `pm2 save`

## Add Nginx Reverse Proxy information

1. `sudo nano /etc/nginx/conf.d/api.conf`
2. Type
```bash
server {
        listen          80;
        listen          [::]:80;
        server_name     api.rodolforoman.xyz;

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
    sudo snap install core; sudo snap refresh core
    sudo snap install --classic certbot
    sudo ln -s /snap/bin/certbot /usr/bin/certbot
    sudo certbot --nginx
```
