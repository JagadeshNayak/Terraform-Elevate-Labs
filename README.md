**Infrastructure as Code (IaC) with Terraform**
**Objective: Provision a local Docker container using Terraform**
**Step.1:** Launch oen ec2 instance with t2 named like this and select the server as your prefereed
I use Ubuntu server because it comes lot of bult-in packages.

<img width="953" alt="1" src="https://github.com/user-attachments/assets/c95c99f2-4183-41b1-8d0d-c6385404f9ce" />

Select the key pair: Choose an existing key pair available on your system to ensure secure SSH access to the instance.
Security Group Rules: Configure the security group to allow inbound traffic on the required ports (e.g., port 22 for SSH, port 80 for HTTP).
Enable Public IP Address: Ensure that a public IP address is associated with the instance so it can be accessed from the internet.
Storage Type: Use gp2 (General Purpose SSD) storage. It is cost-effective and provides sufficient performance for this project.
Launch the Instance: After configuring the above settings, proceed to launch the instance.

<img width="958" alt="3" src="https://github.com/user-attachments/assets/6862f5ec-7398-4a15-bdc4-acc34ba18c05" />

Before connecting to the instance, follow these steps to configure the security group:
Go to the EC2 Dashboard and select your instance.
Click on the Security group associated with your instance.
Navigate to the Inbound Rules tab and click Edit Inbound Rules.
Add a new rule with the following settings:
Type: Custom TCP
Port Range: 80-10000
Source: Anywhere (IPv4) — 0.0.0.0/0
Click Save rules.
This allows incoming traffic on ports 80 through 10000, which may be necessary for web services, APIs, or custom applications running on your instance.

<img width="959" alt="4" src="https://github.com/user-attachments/assets/7fe533dd-3e46-4633-9074-07beca1fcbbf" />

**Step 2.:** Connect the server and update the server as you choosen one 
My server is AWS ubuntu server 
Command for updating server is **sudo apt update**

<img width="938" alt="5" src="https://github.com/user-attachments/assets/1aa3aaff-9554-4e65-8702-6825461a473f" />

Install The docker Command for this 
**sudo apt install docker.io -y**

This command is used  to add your current user to the Docker group, which allows you to run Docker commands without needing sudo every time.
**sudo usermod -aG docker ubuntu**

It is used to apply group membership changes immediately in your current shell session without needing to log out and log back in.
your user is added to the docker group — but the change won’t apply until your session is refreshed (typically by logging out and back in).
**newgrp docker**

Then update the server and for fresh user
**sudo apt update**
In our project the docker is included right i am using here nginx image and to install the nginx image
**sudo docker pull nginx** It will download the nginx image for use
**Step -3:** Write the main.tf code for the docker container creation and installtion
Create one file named and use this command
**sudo nano main.tf**

<img width="958" alt="9" src="https://github.com/user-attachments/assets/eaf7c649-745f-4a45-b5f2-74acf0cd1e9c" />

**NOTE: Install all the docker packages and terraform packages befor proceeding to Terraform init.**

**Terraform init**:initializes a Terraform working directory by downloading required provider plugins and setting up the backend configuration.It will show like this

<img width="932" alt="10" src="https://github.com/user-attachments/assets/73298d9e-9d79-4b22-9592-6a8510cc4cc0" />

**Terraform plan**:Shows a preview of changes Terraform will make to match the desired infrastructure state.It will show like this
<img width="959" alt="11" src="https://github.com/user-attachments/assets/0b455561-9a5e-4f96-9944-6f5088703dcd" />

**Terraform Apply**: Applies the planned changes to create, update, or delete infrastructure. It will show like this

<img width="956" alt="13" src="https://github.com/user-attachments/assets/8944c1f7-188a-4d2c-a854-fc62389232ae" />

**Terraform destroy**: Destroys all resources managed by the current Terraform configuration. 

<img width="959" alt="15" src="https://github.com/user-attachments/assets/2dcf1d31-57cd-4215-b5d1-8418a3196821" />

**Terraform state**: Manages the state file which tracks the current infrastructure and resource metadata.

<img width="956" alt="16" src="https://github.com/user-attachments/assets/1135d7fb-7173-4a3e-b551-d3f91fe0db38" />

We successfully provisioned a local Docker container using Terraform, created a container named nginx, verified its creation, and
then destroyed it while monitoring the changes in the Terraform state.
**THANK YOU ELEVATE LABS**





















