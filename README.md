# Deploying a Node Js Application on AWS EC2

### Testing the project locally

1. Clone this project
```
git clone https://github.com/embedpj/AWS-EC2-Example.git
git clone git@github.com:embedpj/AWS-EC2-Example.git
```
2. Setup the following environment variables - `(.env)` file
```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""

DOMAIN="http://localhost:3000" 
PORT=3000 
STATIC_DIR="./client" 
PUBLISHABLE_KEY="pk_test_51L5AsSSCC8JVWfvgEtfJkzHMTh7Z5PLY5m1yhR379sJgwAVZEe13NaiG33wsHSyHnPJMjTNOosiPk6AeMI8q0ims0049IKffiu" 
SECRET_KEY="sk_test_51L5AsSSCC8JVWfvgxpyZvQyBRRkHmGBkdyIa94vPD3Zs71qbHGrnSPlrJOIWiR74fbcn1A85yESCFnrrp3aX0Oz900JaunHrhe"
```
3. Initialise and start the project
```
npm install
npm run start
```

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console
    - Access Type - Password
    - Permissions - Admin
2. Create an EC2 instance
    - Select an OS image - Ubuntu
    - Create a new key pair & download `.pem` file
    - Instance type - t2.micro
3. Connecting to the instance using ssh
```
ssh -i instance.pem ubunutu@<IP_ADDRESS>
```

### Configuring Ubuntu on remote VM

1. Updating the outdated packages and dependencies
```
sudo apt update
```
3. Install Git - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-22-04) 
4. Configure Node.js and `npm` - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04)

### Deploying the project on AWS

1. Clone this project in the remote VM
```
https://github.com/embedpj/AWS-EC2-Example.git
```
2. Setup the following environment variables - `(.env)` file
```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
> For this project, we'll have to set up an [Elastic IP Address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) for our EC2 & that would be our `DOMAIN`

3. Initialise and start the project
```
npm install
npm run start
Add a second port 3000 below SSH port 22
```

> NOTE - We will have to edit the **inbound rules** in the security group of our EC2, in order to allow traffic from our particular port

### Project is deployed on AWS 🎉
