# How To Deploy **EverShop** (for Free)

I created this method since i tried to develop EverShop in AWS free tier, and the machine simply didnt had enough power to build the App

<details>
<summary> Creating AWS Instances </summary>

> ### Managing AWS Services
>
> Firstly, you will land in this page **right after your registration**, if u dont have an account yet you can create one [here](https://aws.amazon.com/free/)
>
> On this page, you go into "**See All Services**"
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/aws-start.png?raw=true)
>
> ### Finding the Right One
>
> Right under the tab "**Compute**" select "**EC2**"
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/aws-services.png?raw=true)
>
> ### Creating Instance
>
> Now, u can click directly into "**Launch Instance**" or "**Instances**" then "**Launch Instances**"
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/aws-ec2.png?raw=true)
>
> Then you will land in this page
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instances-new.png?raw=true)
>
> ### Configuring your Instance
>
> **Hint**: You can customize your server region, on the right top of your screen, on the left of your user.
>
> Here you can name your instance, i named it "**EverShop**"
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-name.png?raw=true)
>
> Now you select your intance OS, we will be using Ubuntu (If u use another OS, remember to check if it's qualified for the Free Tier)
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-os.png?raw=true)
>
> Then you check if your instance type is set for the Free Tier 
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-hardware.png?raw=true)
>
> Here we will set up some security when accessing your instance, click on "**Create new key pair**"
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-keys.png?raw=true)
> Name the key pair, then create it (Put the one u downloaded somewhere safe, if u later on want to access it by another methods)
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/keys-new.png?raw=true)
>
> Now setting up more security Configs, here u can check "**Allow HTTPS traffic from the internet**" and "**Allow HTTP traffic from the internet**" (You can leave the SSH one checked too)
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-ports.png?raw=true)
>
> Every thing else you can leave it as it is (If u want to, u can get the storage size up to 30GB), then hit the "**Launch instance**" button
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-create.png?raw=true)
>
> ### Connecting to your Instance
> Now your instance is being created! Hit the "**Connect to Instance**" button to proceed
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-created.png?raw=true)
>
> Right here it is prety much everithing configured for default, so just hit the "**Connect**" button (Remember to grab this "**IPv4**")
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-conect.png?raw=true)
>
> And thats it! You successfully connected to your new Instance
> ![AWS Start Page](https://github.com/PedroWoicoleskoCrespo/HowTo-EverShop/blob/main/media/instance-shell.png?raw=true)
>
> Now you can continue to follow the tutorial

</details>

<details>
<summary> Setting up AWS Instance </summary>

> ## Instance Preparation
> ### Checking for updates
> At first, we need to check for updates
> ```bash
> sudo apt-get update
> sudo apt-get upgrade -y
> ```
> 
> ### Installing ZIP Package
> ```bash
> sudo apt-get install zip -y
> ```
> 
> ### Installing NodeJS and NPM
> (This will take a while, be patient)
> ```bash
> sudo apt-get install nodejs npm -y
> ```
>
> ### Installing PostgreSQL
> ```bash
> sudo apt-get install postgresql -y
> ```
> 
> ### Installing Nginx
> ```bash
> sudo apt-get install nginx -y
> ```
> 
> ### Configuring Nginx
> Now, you need to create a config file for your server, get the **IPv4** u grabed earlier, or your instance public domain, create your file
> ```bash
> sudo nano /etc/nginx/sites-available/evershop.conf
> ```
>
> Now, ur in the file, paste the content below **replacing the domain.com with your instance IP or Domain**
> ```conf
> server {
>     listen 80;
>     server_name domain.com;
> 
>     location / {
>         proxy_pass http://localhost:3000;
>         proxy_http_version 1.1;
>         proxy_set_header Upgrade $http_upgrade;
>         proxy_set_header Connection 'upgrade';
>         proxy_set_header Host $host;
>         proxy_cache_bypass $http_upgrade;
>     }
> }
> ```
> Now hit **Ctrl** + **X** then **Y** and finally **Enter** to save the file
> 
> Enabling config
> ```bash
> sudo ln -s /etc/nginx/sites-available/evershop.conf /etc/nginx/sites-enabled/
> ```
>
> Disabling default config
> ```bash
> sudo unlink /etc/nginx/sites-enabled/default
> ```
>
> Restarting Nginx
> ```bash
> sudo systemctl restart nginx
> ```

</details>

<details>
<summary> Setting up EverShop </summary>

> ## Instance Preparation

</details>

admin@admin.com
admin123



```bash
sudo apt-get update
sudo apt-get upgrade -y
```



```bash
npm run user:changePassword -- --email "admin@admin.com" --password "SOMETHING ABSURD"
```

```bash
npm run user:changePassword -- --email "superuser email" --password "new password"
```



```sql
CREATE USER evershop WITH PASSWORD 'evershop';
```

```sql
CREATE DATABASE evershop;
```

```sql
GRANT ALL PRIVILEGES ON DATABASE evershop TO evershop;
```

```sql
ALTER DATABASE evershop OWNER TO evershop;
```

```sql
\! psql -U evershop -d evershop -f /path/to/evershop-db.sql -W
```
- Remember to change the path to your file