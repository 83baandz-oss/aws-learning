# Amazon EC2 — Learning Notes

## 1. What is Amazon EC2?

Amazon Elastic Compute Cloud (EC2) is an AWS service that provides resizable virtual servers called **instances**.

Instead of purchasing and maintaining a physical server, I can launch a virtual server in AWS and configure it for different workloads.

### Common EC2 use cases

* Hosting websites
* Running applications
* Running APIs
* Hosting databases
* Development and testing
* Running Linux environments
* Automating workloads
* Building cloud infrastructure

---

# 2. EC2 Key Concepts

## Instance

An EC2 instance is a virtual server running inside AWS.

When launching an instance, I choose things such as:

* Operating system
* Instance type
* Storage
* Network configuration
* Security groups
* Key pair

---

## AMI — Amazon Machine Image

An AMI is a template used to launch an EC2 instance.

An AMI can contain:

* Operating system
* System configuration
* Required software
* Application configuration

Examples:

* Amazon Linux
* Ubuntu
* Windows Server

---

## Instance Type

The instance type determines the computing resources available to the server.

Resources include:

* CPU
* Memory
* Network performance
* Instance capabilities

Example:

`t3.micro`

The exact resources and pricing depend on the instance type and AWS region.

---

# 3. EC2 Instance Lifecycle

An EC2 instance can move through several states.

### Launch

Creates and starts a new EC2 instance.

### Stop

Shuts down the virtual machine while generally preserving its attached storage.

### Start

Starts a stopped instance again.

### Reboot

Restarts the operating system.

### Terminate

Permanently deletes the instance and its associated resources that are configured for deletion.

**Important:** Termination should be treated as destructive.

---

# 4. Connecting to a Linux EC2 Instance

For Linux instances, I can connect using SSH.

Example:

```bash
ssh -i my-key.pem ec2-user@PUBLIC-IP
```

The username depends on the AMI.

Examples can include:

```text
Amazon Linux → ec2-user
Ubuntu → ubuntu
```

The private key must be protected.

Example:

```bash
chmod 400 my-key.pem
```

---

# 5. Security Groups

A security group acts as a virtual firewall for an EC2 instance.

It controls network traffic that is allowed to reach the instance.

Common inbound rules include:

| Protocol | Port | Purpose               |
| -------- | ---: | --------------------- |
| SSH      |   22 | Remote administration |
| HTTP     |   80 | Web traffic           |
| HTTPS    |  443 | Secure web traffic    |

### Security principle

I should only open the ports that are actually required.

For example, SSH access should not automatically be exposed to the entire internet if access can be restricted to a trusted IP address.

---

# 6. Public vs Private IP Addresses

An EC2 instance can have private and public networking information.

### Private IP

Used for communication inside the AWS network/VPC.

### Public IP

Can allow communication with the instance from the public internet when the networking configuration permits it.

A public IP can change when an instance is stopped and started.

For persistent public addressing, AWS provides Elastic IP functionality.

---

# 7. EC2 Storage

EC2 commonly uses **Amazon EBS (Elastic Block Store)** for persistent block storage.

EBS volumes can be used for:

* Operating system files
* Application files
* Logs
* Databases
* Other persistent data

Useful Linux commands for inspecting storage:

```bash
lsblk
df -h
du -sh
```

---

# 8. Basic Linux Administration on EC2

After connecting to an EC2 Linux instance, I can use Linux commands to manage the server.

### Check current user

```bash
whoami
```

### Display current directory

```bash
pwd
```

### List files

```bash
ls
```

### Change directories

```bash
cd directory-name
```

### Create a directory

```bash
mkdir test-directory
```

### Create a file

```bash
touch test.txt
```

### View a file

```bash
cat test.txt
```

### Edit a file

```bash
nano test.txt
```

---

# 9. Installing Software

Linux package managers can be used to install software.

For Amazon Linux:

```bash
sudo dnf install nginx
```

For Ubuntu:

```bash
sudo apt update
sudo apt install nginx
```

The exact commands depend on the operating system and version.

---

# 10. Managing Services

Linux systems commonly use `systemctl` to manage services.

Start a service:

```bash
sudo systemctl start nginx
```

Stop a service:

```bash
sudo systemctl stop nginx
```

Check service status:

```bash
sudo systemctl status nginx
```

Enable a service at boot:

```bash
sudo systemctl enable nginx
```

---

# 11. Basic EC2 Web Server

One practical EC2 exercise is deploying a simple web server.

Basic workflow:

1. Launch an EC2 Linux instance.
2. Configure a security group.
3. Allow HTTP traffic on port 80.
4. Connect to the instance using SSH.
5. Install a web server.
6. Start the web server.
7. Create an HTML page.
8. Access the page using the instance's public IP address.

This demonstrates that I can provision a cloud server and deploy a basic service.

---

# 12. Troubleshooting EC2

When an EC2 server cannot be accessed, I should troubleshoot systematically.

### SSH connection problems

Check:

* Instance is running
* Correct public IP/DNS name
* Correct username
* Correct private key
* Security group allows SSH
* Network configuration allows the traffic

### Website cannot be reached

Check:

* Web server is running
* Security group allows HTTP/HTTPS
* Operating-system firewall
* Correct public IP
* Web server configuration
* Application/service logs

Useful commands:

```bash
sudo systemctl status nginx
```

```bash
ss -tulpn
```

```bash
curl localhost
```

```bash
df -h
```

```bash
free -h
```

---

# 13. Security Practices I Learned

While working with EC2, I am practicing basic cloud security principles.

* Use least-privilege access.
* Avoid exposing unnecessary ports.
* Protect SSH private keys.
* Avoid using passwords when key-based authentication is appropriate.
* Keep operating systems and packages updated.
* Avoid exposing administrative services to the entire internet when unnecessary.
* Remove resources that are no longer needed.
* Monitor server activity and resource usage.

---

# 14. Skills Demonstrated

Through my EC2 practice, I am developing experience with:

* Amazon EC2
* AWS Management Console
* Linux
* SSH
* Security Groups
* Networking fundamentals
* EBS storage
* Linux file systems
* Linux package management
* Linux services
* Web server deployment
* Basic cloud security
* Server troubleshooting
* Cloud infrastructure fundamentals

---

# 15. What I Actually Practiced

I am using this repository to document hands-on cloud learning rather than only reading AWS documentation.

My EC2 practice includes:

* Launching Linux EC2 instances
* Connecting to instances through SSH
* Navigating the Linux file system
* Creating and modifying files
* Installing packages
* Managing Linux services
* Configuring security groups
* Deploying a basic web server
* Troubleshooting connectivity
* Monitoring server resources
* Terminating unused AWS resources

---

# 16. Career Relevance

EC2 is helping me build foundational skills for cloud and infrastructure roles.

The skills practiced in this section are relevant to roles such as:

* Cloud Support Associate
* Cloud Technician
* Junior Cloud Engineer
* Junior DevOps Engineer
* Systems Administrator
* Cloud Operations Associate

My goal is to continue building these skills through progressively more realistic AWS projects.

