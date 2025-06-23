# Node.js-Deployment-EC2
This Repo contains steps to create a virtual server via ec2 and deploy the node.js app
![1](https://github.com/user-attachments/assets/a00cf2e0-e5ee-43fa-8865-fe80b30c8b44)
Step 1) Go to Ec2 and click the launch Instance
![2](https://github.com/user-attachments/assets/50de61b8-ca0f-45d4-be60-58d76b225ab2)
Step 2) Enter the name,select the os type and the instance type
![3](https://github.com/user-attachments/assets/141dbcc7-29b8-40c0-a84b-3f8e67d68031)
Step 3) Select vpc,subnet and the security group.If the particular instance is not available in the az then change the subnet present in different az and check. 
![4](https://github.com/user-attachments/assets/07ac5d9d-adf7-41e2-9223-48a361eea520)
Step 4) Click Launch Instance
![5](https://github.com/user-attachments/assets/02155979-018e-485f-baa9-e0fd40fa3ecf)
Step 5) After successfully deploying that instance.It should be in the running state and after connect to that instance using ec2 instance connect.
It uses temporary, one-time SSH keys that AWS injects just for your session.
For this ssh 22 port should be must and should allow in the security group
![6](https://github.com/user-attachments/assets/f8bcf6f1-6b03-40a8-a83e-9ccdaf2cddd9)

Step 6)
Run these commands
# Update packages
sudo yum update -y <br>

# Install Node.js (Amazon Linux 2 has Node.js 14 in repos)
sudo yum install -y nodejs git
<br>
# Check versions
node -v <br>
npm -v <br>
git --version <br>

# Copy github repo to here and install packages 
git clone https://github.com/johnpapa/node-hello.git <br>
cd node-hello <br>
npm install <br>


# Install pm2 and run the process so that it will run even after closing the session
sudo npm install -g pm2 <br>
pm2 start index.js  # or your main server file <br>
pm2 startup systemd <br>
sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u ec2-user --hp /home/ec2-user <br>
pm2 save <br>

Step 7)
# In the security groups specify the http,https,ssh,tcp port if node.js port is running differently like 3000.
Https can also be done if ssl/tls certificate is available (If domain is present )
![6](https://github.com/user-attachments/assets/f9f11987-29a6-4ab4-9fd2-0f72f6fb2969)

After Executing necessary commandss we can see the ouptut <br>


