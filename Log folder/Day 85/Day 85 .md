# Day 85

Tags: AWS, Backend development
Date: October 7, 2023
Status: Done

Tasks of the day 

- Linux basics
- Basic AWS services
    - Route53
    - SES
    - EC2
    - VPC
    - S3

Exercise:  Application Deployment to AWS

---

### Linux Basics

Linux is a family of open-source Unix-like operating systems based o the Linux kernel developed by Linus Torvalds. It’s essential for a software developer to at least have an idea of how Linux and how to use it. 

![Screen Shot 2023-10-07 at 6.12.12 PM.png](Day%2085%20317923a010b944e39e3079d265a85d83/Screen_Shot_2023-10-07_at_6.12.12_PM.png)

[UNIX / LINUX Tutorial](https://www.tutorialspoint.com/unix/index.htm)

---

### Basic AWS Services

AWS has several services but you don’t need to know all of them. Here are the most common ones that you can get started with:

**[Amazon Elastic Compute Cloud (EC2)](https://aws.amazon.com/ec2/)**

Amazon Elastic Compute Cloud (Amazon EC2) offers the broadest and deepest compute platform, with over 700 instances and choice of the latest processor, storage, networking, operating system, and purchase model to help you best match the needs of your workload. We are the first major cloud provider that supports Intel, AMD, and Arm processors, the only cloud with on-demand EC2 Mac instances, and the only cloud with 400 Gbps Ethernet networking. We offer the best price performance for machine learning training, as well as the lowest cost per inference instances in the cloud. More SAP, high performance computing (HPC), ML, and Windows workloads run on AWS than any other cloud.

**Use cases**

- **Run cloud-native and enterprise applications:** Amazon EC2 delivers secure, reliable, high-performance, and cost-effective compute infrastructure to meet demanding business needs.
- **Scale for HPC applications:** Access the on-demand infrastructure and capacity you need to run HPC applications faster and cost-effectively
- **Develop for Apple platforms:** Build, test, and sign on-demand macOS workloads. Access environments in minutes, dynamically scale capacity as needed, and benefit from AWS’s pay-as-you-go pricing.
- **Train and deploy ML applications:** Amazon EC2 delivers the broadest choice of compute, networking (up to 400 Gbps), and storage services purpose-built to optimize price performance for ML projects.

[https://www.youtube.com/watch?v=oHAQ3TzUTro](https://www.youtube.com/watch?v=oHAQ3TzUTro)

**Amazon Virtual Private Cloud (VPC)**

Amazon Virtual Private Cloud (Amazon VPC) gives you full control over your virtual networking environment, including resource placement, connectivity, and security. Get started by setting up your VPC in the AWS service console. Next, add resources to it such as Amazon Elastic Compute Cloud (EC2) and Amazon Relational Database Service (RDS) instances. Finally, define how your VPCs communicate with each other across accounts, Availability Zones, or AWS Regions. In the example below, network traffic is being shared between two VPCs within each Region.

![Screen Shot 2023-10-07 at 6.35.27 PM.png](Day%2085%20317923a010b944e39e3079d265a85d83/Screen_Shot_2023-10-07_at_6.35.27_PM.png)

**Use cases**

- **Launch a simple website or blog:** Improve your web application security posture by enforcing rules on inbound and outbound connections.
- **Host multi-tier web application**: Define network connectivity and restrictions between your web servers, application servers, and databases.
- **Create hybrid connections:** Build and manage a compatible VPC network across your AWS services and on premises.

[https://www.youtube.com/watch?v=TUTqYEZZUdc](https://www.youtube.com/watch?v=TUTqYEZZUdc)

**Amazon S3**

Amazon Simple Storage Service (Amazon S3) is an object storage service offering industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can store and protect any amount of data for virtually any use case, such as [data lakes](https://aws.amazon.com/big-data/datalakes-and-analytics/datalakes/), cloud-native applications, and mobile applications.

**Use cases**

- **Build a data lake :**Run big data analytics, artificial intelligence (AI), machine learning (ML), and high performance computing (HPC) applications to unlock data insights.
- **Back up and restore critical data:** Meet Recovery Time Objectives (RTO), Recovery Point Objectives (RPO), and compliance requirements with S3’s robust replication features.
- **Archive data at the lowest cost:** Move data archives to the Amazon S3 Glacier storage classes to lower costs, eliminate operational complexities, and gain new insights.
- **Run cloud-native applications:** Build fast, powerful mobile and web-based cloud-native apps that scale automatically in a highly available configuration.

[https://www.youtube.com/watch?v=NZElg91l_ms](https://www.youtube.com/watch?v=NZElg91l_ms)

**Amazon Route 53**

Amazon Route 53 is a highly available and scalable [Domain Name System (DNS)](https://aws.amazon.com/route53/what-is-dns/) web service. Route 53 connects user requests to internet applications running on AWS or on-premises.

![Screen Shot 2023-10-07 at 6.40.19 PM.png](Day%2085%20317923a010b944e39e3079d265a85d83/Screen_Shot_2023-10-07_at_6.40.19_PM.png)

**Use cases**

- **Manage network traffic globally:** Create, visualize, and scale complex routing relationships between records and policies with easy-to-use global DNS features.
- **Build highly available applications:** Set routing policies to pre-determine and automate responses in case of failure, like redirecting traffic to alternative Availability Zones or Regions.
- **Set up private DNS:** Assign and access custom domain names in your Amazon Virtual Private Cloud (VPC). Use internal AWS resources and servers without exposing DNS data to the public Internet.

[https://www.youtube.com/watch?v=RGWgfhZByAI](https://www.youtube.com/watch?v=RGWgfhZByAI)

**[Amazon simple email service](https://aws.amazon.com/ses/)**

Amazon Simple Email Service (Amazon SES) lets you reach customers confidently without an on-premises Simple Mail Transfer Protocol (SMTP) email server using the [Amazon SES API](https://docs.aws.amazon.com/ses/latest/dg/send-email-api.html) or SMTP interface.

Amazon SES is a cloud-based email service provider that can integrate into any application for high volume email automation. Whether you use an email software to send transactional emails, marketing emails, or newsletter emails, you pay only for what you use. Amazon SES is an email tool that also supports a variety of deployments including dedicated, shared, or owned IP addresses. Reports on sender statistics and email deliverability tools help businesses make every email count.

![Screen Shot 2023-10-07 at 6.42.12 PM.png](Day%2085%20317923a010b944e39e3079d265a85d83/Screen_Shot_2023-10-07_at_6.42.12_PM.png)

**Use cases**

- **Automate transactional messages:** Keep your customers up to date by sending automated emails, such as purchase or shipping notifications, order status updates, and policy change notices.
- **Deliver marketing emails globally:** Tell customers around the world about products and services through newsletters, special offers, and engaging content.
- **Send timely notifications to customers:** Send customers timely notifications about their interaction with your products and services, including daily reminders, weekly usage reports, and newsletters.
- **Send bulk email communications:** Deliver messages—including notifications and announcements—to large groups, and track results using configuration sets.

---

### Exercise: Application Deployment to AWS

**Step #1**

Setup an EC2 instance using any Amazon machine image (AMI)

1. **Sign in to AWS Console:**
Log in to your AWS account using your credentials at [https://aws.amazon.com](https://aws.amazon.com/).
2. **Access EC2 Dashboard:**
After logging in, you'll be in the AWS Management Console. To create an EC2 instance, navigate to the EC2 dashboard. You can either click on "Services" in the top left corner and select "EC2" under "Compute," or you can search for "EC2" in the AWS services search bar and select it.
3. **Launch Instance:**
On the EC2 Dashboard, click the "Launch Instance" button.
4. **Choose an Amazon Machine Image (AMI):**
In the "Step 1: Choose an Amazon Machine Image (AMI)" section, you'll be presented with a list of AMIs. You can select a pre-configured AMI based on your requirements. AWS provides various options, including different operating systems and software configurations. Choose the AMI that suits your application needs, and then click the "Select" button.
5. **Choose an Instance Type:**
In the "Step 2: Choose an Instance Type" section, you need to select the hardware configuration (CPU, memory, storage, etc.) for your EC2 instance. Choose an instance type that aligns with your application's requirements. After selecting an instance type, click the "Next: Configure Instance Details" button.
6. **Configure Instance Details (Optional):**
In this step, you can configure advanced settings for your instance, such as network settings, IAM role, and user data. If you're unsure about these settings, you can leave them at their default values for now and proceed by clicking the "Next: Add Storage" button.
7. **Add Storage:**
Specify the size and type of storage you need for your EC2 instance. You can adjust the default storage settings if necessary. After configuring storage, click the "Next: Add Tags" button.
8. **Add Tags (Optional):**
You can add tags to your instance for better organization and resource identification. Tags are key-value pairs that can help you label your instances. This step is optional but can be useful for managing multiple instances. Click the "Next: Configure Security Group" button when you're ready to proceed.
9. **Configure Security Group:**
In the "Step 6: Configure Security Group" section, you'll need to configure the security group rules that control inbound and outbound traffic to your instance. Define the rules based on your application's requirements. For example, you may open port 80 for HTTP traffic or port 22 for SSH access. Once you've configured the security group, click the "Review and Launch" button.
10. **Review and Launch:**
Review the configuration details of your EC2 instance to ensure everything is set up correctly. If everything looks good, click the "Launch" button.
11. **Create a Key Pair (if necessary):**
If you haven't created an SSH key pair for accessing your instance, AWS will prompt you to create one. Download the private key (.pem) file to a secure location. You'll need this key to access your instance later.
12. **Launch the Instance:**
After creating or selecting a key pair, click the "Launch Instances" button. AWS will start provisioning your EC2 instance.
13. **View Instances:**
Once the instance is successfully launched, you'll be taken to the "Instances" page, where you can see the status of your new EC2 instance. It may take a few minutes for the instance to become available.

**Step #2**

Install Node.js on the EC2 instance

1. **Connect to Your EC2 Instance:**
Use an SSH client to connect to your EC2 instance. You'll need the private key (.pem) file you downloaded when creating the instance.
    
    ```bash
    bashCopy code
    ssh -i /path/to/your-key.pem ec2-user@your-ec2-instance-public-ip
    
    ```
    
    Replace **`/path/to/your-key.pem`** with the actual path to your private key file and **`your-ec2-instance-public-ip`** with your EC2 instance's public IP address.
    
2. **Update Package Lists:**
Before installing Node.js, it's a good practice to update the package lists on your instance to ensure you're installing the latest version of software packages:
    
    ```bash
    bashCopy code
    sudo yum update -y
    
    ```
    
    For Ubuntu-based instances, you can use **`sudo apt update`** instead.
    
3. **Install Node.js with Node Version Manager (NVM):**
Installing Node.js with Node Version Manager (NVM) allows you to manage multiple Node.js versions easily. First, you'll need to install NVM:
    
    ```bash
    bashCopy code
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    
    ```
    
    This command will download and install NVM. After installation, you may need to reload your shell for the changes to take effect. You can do this by closing and reopening your SSH session or by running:
    
    ```bash
    bashCopy code
    source ~/.bashrc
    
    ```
    
    For Ubuntu-based instances, you can use **`~/.bashrc`** or **`~/.profile`** depending on your shell configuration.
    
4. **Install a Specific Node.js Version:**
Once NVM is installed, you can install a specific version of Node.js. For example, to install the LTS (Long Term Support) version, use:
    
    ```bash
    bashCopy code
    nvm install --lts
    
    ```
    
    To check the Node.js version installed, you can use:
    
    ```bash
    bashCopy code
    node -v
    
    ```
    
    This will display the installed Node.js version.
    
5. **Set the Default Node.js Version (Optional):**
If you want to set a default Node.js version for your user, you can do this by running:
    
    ```bash
    bashCopy code
    nvm alias default <version>
    
    ```
    
    Replace **`<version>`** with the version number you want to set as the default.
    
6. **Verify the Installation:**
To verify that Node.js and npm (Node Package Manager) are installed correctly, you can run:
    
    ```bash
    bashCopy code
    node -v
    npm -v
    
    ```
    
    You should see the version numbers displayed in the terminal.
    

Node.js is now installed on your EC2 instance, and you can start using it to run your Node.js applications. Remember that if you close your SSH session or log out, you'll need to use NVM to manage Node.js versions in future sessions as well.

**Step #3**

Install git on the EC2

1. **Connect to Your EC2 Instance:**
If you're not already connected to your EC2 instance, use SSH to connect to it:
    
    ```bash
    bashCopy code
    ssh -i /path/to/your-key.pem ec2-user@your-ec2-instance-public-ip
    
    ```
    
    Replace **`/path/to/your-key.pem`** with the actual path to your private key file, and **`your-ec2-instance-public-ip`** with your EC2 instance's public IP address.
    
2. **Update Package Lists:**
It's a good practice to update the package lists on your instance before installing new software:
    
    ```bash
    bashCopy code
    sudo yum update -y
    
    ```
    
    For Ubuntu-based instances, you can use **`sudo apt update`** instead.
    
3. **Install Git:**
To install Git, use the package manager for your Linux distribution. For Amazon Linux and CentOS, use **`yum`**:
    
    ```bash
    bashCopy code
    sudo yum install git -y
    
    ```
    
    For Ubuntu-based instances, use **`apt`**:
    
    ```bash
    bashCopy code
    sudo apt install git -y
    
    ```
    
4. **Verify Git Installation:**
After the installation is complete, you can verify that Git has been successfully installed by checking its version:
    
    ```bash
    bashCopy code
    git --version
    
    ```
    
    This should display the installed Git version.
    

Git is now installed on your EC2 instance, and you can use it to manage your source code repositories. You can clone Git repositories, commit changes, and work with your code as needed

**Step #4**

Install and configure database on the EC2 instance (e.g. PostgreSQL)

1. **Connect to Your EC2 Instance:**
If you're not already connected to your EC2 instance, use SSH to connect to it:
    
    ```bash
    bashCopy code
    ssh -i /path/to/your-key.pem ec2-user@your-ec2-instance-public-ip
    
    ```
    
    Replace **`/path/to/your-key.pem`** with the actual path to your private key file and **`your-ec2-instance-public-ip`** with your EC2 instance's public IP address.
    
2. **Update Package Lists:**
As always, it's a good practice to update the package lists on your instance before installing new software:
    
    ```bash
    bashCopy code
    sudo yum update -y
    
    ```
    
    For Ubuntu-based instances, you can use **`sudo apt update`** instead.
    
3. **Install PostgreSQL:**
To install PostgreSQL, use the package manager for your Linux distribution. For Amazon Linux and CentOS, use **`yum`**:
    
    ```bash
    bashCopy code
    sudo yum install postgresql postgresql-server -y
    
    ```
    
    For Ubuntu-based instances, use **`apt`**:
    
    ```bash
    bashCopy code
    sudo apt install postgresql postgresql-contrib -y
    
    ```
    
4. **Initialize and Start PostgreSQL:**
After installation, initialize the PostgreSQL database and start the PostgreSQL service:
    
    For Amazon Linux and CentOS:
    
    ```bash
    bashCopy code
    sudo service postgresql initdb
    sudo service postgresql start
    
    ```
    
    For Ubuntu-based instances:
    
    ```bash
    bashCopy code
    sudo systemctl start postgresql
    
    ```
    
5. **Enable PostgreSQL to Start on Boot (Optional):**
To ensure PostgreSQL starts automatically when your EC2 instance reboots, enable it:
    
    For Amazon Linux and CentOS:
    
    ```bash
    bashCopy code
    sudo chkconfig postgresql on
    
    ```
    
    For Ubuntu-based instances:
    
    ```bash
    bashCopy code
    sudo systemctl enable postgresql
    
    ```
    
6. **Secure Your PostgreSQL Installation (Optional, but recommended):**
PostgreSQL comes with security features to protect your database. You should consider configuring these settings, including setting passwords for PostgreSQL users, configuring authentication methods, and setting up a firewall if necessary. This is a broad topic, and you should follow PostgreSQL documentation and best practices for your specific use case.
7. **Access PostgreSQL:**
You can access the PostgreSQL command-line interface by running:
    
    ```bash
    bashCopy code
    sudo -i -u postgres
    psql
    
    ```
    
    From there, you can create databases, roles, and perform other database-related tasks.
    

That's it! You have installed and configured PostgreSQL on your EC2 instance. You can now use PostgreSQL to create and manage databases for your applications. Remember to follow security best practices to secure your database and control access to it.

**Step #5**

Make sure that the security group of the EC2 instance allows HTTP and HTTPS traffic

1. **Sign in to AWS Console:**
Log in to your AWS account using your credentials at [https://aws.amazon.com](https://aws.amazon.com/).
2. **Access EC2 Dashboard:**
After logging in, navigate to the EC2 dashboard. You can either click on "Services" in the top left corner and select "EC2" under "Compute," or you can search for "EC2" in the AWS services search bar and select it.
3. **Locate Your EC2 Instance:**
In the EC2 dashboard, click on "Instances" in the left navigation pane to view a list of your EC2 instances.
4. **Identify the Security Group:**
Identify the security group associated with the EC2 instance you want to modify. In the "Security Groups" column of the instance's row, you can see the name of the security group. Click on the security group's name to access its settings.
5. **Edit Inbound Rules:**
Inside the security group settings, you'll see the "Inbound rules" tab. Click on it to configure inbound traffic rules.
6. **Add Rule for HTTP (Port 80):**
To allow HTTP traffic, click the "Edit inbound rules" button, then click the "Add rule" button.
    - For the "Type," select "HTTP (80)" from the dropdown list.
    - For the "Source," you can specify the IP range that should be allowed to access your EC2 instance via HTTP. You can use "0.0.0.0/0" to allow access from anywhere, or you can specify a more restrictive IP range for added security.
    
    After configuring these settings, click the "Save rules" button to add the HTTP rule.
    
7. **Add Rule for HTTPS (Port 443):**
To allow HTTPS traffic, click the "Add rule" button again.
    - For the "Type," select "HTTPS (443)" from the dropdown list.
    - For the "Source," similarly, you can specify the IP range that should be allowed to access your EC2 instance via HTTPS.
    
    Click the "Save rules" button to add the HTTPS rule.
    
8. **Review and Apply Changes:**
After adding both HTTP and HTTPS rules, review your inbound rules to ensure they are correctly configured.
9. **Confirm Changes:**
Once you are satisfied with the rule configurations, click the "Save rules" button to apply the changes to the security group.

Now, your EC2 instance's security group should allow HTTP (port 80) and HTTPS (port 443) traffic as per the rules you defined. Users can access your EC2 instance via web browsers using these ports. Make sure to secure your server and applications running on it accordingly, especially if it's a web server handling sensitive data or user accounts.

**Step #6**

Try to access your application using the public IP address of the EC2 instance

1. **Locate Your EC2 Instance:**
In the AWS Management Console, navigate to the EC2 dashboard.
2. **Find the Public IP Address:**
On the EC2 dashboard, you should see a list of your EC2 instances. Find the instance for which you want to access the application. In the "Public IP" column, you'll see the public IP address associated with that instance. Note down this public IP address.
3. **Open a Web Browser:**
Open a web browser on your local machine.
4. **Access the Application:**
In the web browser's address bar, enter the public IP address of your EC2 instance, followed by the port number if your application uses a different port than the default HTTP (port 80) or HTTPS (port 443).
    
    For example, if your EC2 instance's public IP address is **`1.2.3.4`** and your application runs on port 80 for HTTP, enter:
    
    ```arduino
    arduinoCopy code
    http://1.2.3.4
    
    ```
    
    If your application runs on a different port, you should specify it in the URL, like this (replace **`PORT_NUMBER`** with your application's actual port number):
    
    ```arduino
    arduinoCopy code
    http://1.2.3.4:PORT_NUMBER
    
    ```
    
    If your application uses HTTPS and runs on the default port (443), enter:
    
    ```arduino
    arduinoCopy code
    https://1.2.3.4
    
    ```
    
    If you're using a custom domain or hostname instead of the IP address, you should use that domain or hostname in the URL.
    
5. **Press Enter:**
Hit Enter in your web browser after entering the URL.
6. **Access the Application:**
The web browser should now attempt to access your application running on the EC2 instance using the public IP address. Depending on your application, you may see a login page, a website, or another interface.
7. **Log In or Interact with the Application:**
If your application requires authentication, log in with the appropriate credentials. Otherwise, interact with your application as needed.

That's it! You've successfully accessed your application using the public IP address of your EC2 instance. Please note that the success of this step depends on various factors, including the correct configuration of your application, any firewall or security group settings, and the network accessibility of your EC2 instance. If you encounter issues, make sure that your security groups and firewall settings allow traffic on the required ports (e.g., 80 for HTTP or 443 for HTTPS) and that your application is properly configured to listen on the specified port.

**Step #7**

Purchase or setup a domain name using Route53 (or any other domain name provider) and point it to the public IP address of the EC2 instance

To purchase or set up a domain name using Amazon Route 53 and point it to the public IP address of your EC2 instance, follow these step-by-step instructions:

**Step 1: Sign in to AWS Console:**
Log in to your AWS account using your credentials at [https://aws.amazon.com](https://aws.amazon.com/).

**Step 2: Access Route 53:**
After logging in, navigate to the Route 53 service. You can either click on "Services" in the top left corner and select "Route 53" under "Networking & Content Delivery," or you can search for "Route 53" in the AWS services search bar and select it.

**Step 3: Choose "Hosted Zones" on the Route 53 Dashboard:**
In the Route 53 dashboard, choose "Hosted Zones" from the left navigation pane.

**Step 4: Create a New Hosted Zone:**
Click the "Create Hosted Zone" button.

**Step 5: Configure the Hosted Zone:**

- **Domain Name:** Enter the domain name you want to purchase or configure. For example, if you want to set up "example.com," enter "example.com" (without quotes).
- **Type:** Choose the type of hosted zone you want to create. For a new domain name, choose "Public Hosted Zone."
- **Comment (optional):** You can add an optional comment for reference.
- **Tags (optional):** You can add tags for organization and tracking (optional).

Click the "Create hosted zone" button.

**Step 6: Note Down the Nameservers:**
After creating the hosted zone, you'll see a set of nameservers listed. Take note of these nameservers as you'll need to update your domain registrar's settings with this information.

**Step 7: Configure Domain Registrar (e.g., GoDaddy, Namecheap):**

- Log in to your domain registrar's website (where you purchased your domain name).
- Locate the domain management section.
- Find the domain name you want to configure and choose to edit its DNS settings or nameservers.
- Replace the existing nameservers with the nameservers provided by Route 53 in the previous step.
- Save the changes. Note that DNS propagation may take some time, typically up to 48 hours, although it often happens much faster.

**Step 8: Create a Record Set in Route 53:**

- In the Route 53 dashboard, select the hosted zone you created.
- Click the "Create Record Set" button.
- For "Name," enter the subdomain or leave it blank if you want to configure the root domain (e.g., "www" for [www.example.com](http://www.example.com/)).
- Choose the record type based on your needs. For pointing to an EC2 instance, choose "A - IPv4 address."
- In the "Value" field, enter the public IP address of your EC2 instance.
- Leave the "TTL" (Time to Live) at its default setting, or adjust it as needed.
- Click the "Create" button to create the record set.

**Step 9: Verify DNS Configuration:**
It may take some time for DNS changes to propagate globally. You can use tools like "nslookup" or online DNS lookup tools to verify that your domain name is resolving to the correct IP address.

**Step 10: Access Your Application with the Domain:**
Once DNS propagation is complete, you should be able to access your EC2 instance using your domain name (e.g., [http://www.example.com](http://www.example.com/)).

That's it! You've purchased or configured a domain name using Route 53 and pointed it to the public IP address of your EC2 instance. Your website or application should now be accessible via the domain name you've configured.

**Step #8**

To set up HTTPS using Certbot on your EC2 instance, you'll need to install Certbot, obtain an SSL/TLS certificate, and configure your web server (e.g., Apache or Nginx) to use the certificate. Here's a step-by-step guide:

**Step 1: Connect to Your EC2 Instance:**
If you're not already connected to your EC2 instance, use SSH to connect to it:

```bash
bashCopy code
ssh -i /path/to/your-key.pem ec2-user@your-ec2-instance-public-ip

```

Replace **`/path/to/your-key.pem`** with the actual path to your private key file and **`your-ec2-instance-public-ip`** with your EC2 instance's public IP address.

**Step 2: Update Package Lists:**
Update the package lists on your EC2 instance to ensure you're installing the latest software:

For Amazon Linux and CentOS:

```bash
bashCopy code
sudo yum update -y

```

For Ubuntu-based instances:

```bash
bashCopy code
sudo apt update

```

**Step 3: Install Certbot:**
Install Certbot, which is a tool for obtaining and managing SSL/TLS certificates:

For Amazon Linux and CentOS:

```bash
bashCopy code
sudo yum install certbot python3-certbot-apache -y

```

For Ubuntu-based instances:

```bash
bashCopy code
sudo apt install certbot python3-certbot-apache -y

```

**Step 4: Obtain the SSL/TLS Certificate:**
Run Certbot to obtain an SSL/TLS certificate and configure your web server. Certbot will guide you through the process and ask for some information:

For Apache, use:

```bash
bashCopy code
sudo certbot --apache

```

For Nginx, use:

```bash
bashCopy code
sudo certbot --nginx

```

Follow the prompts and provide the required information, including your domain name. Certbot will automatically configure your web server to use the certificate.

**Step 5: Test HTTPS Access:**
Once Certbot has successfully obtained the certificate and configured your web server, you can test HTTPS access to your website. Open a web browser and enter your domain name with "https://" (e.g., [https://www.example.com](https://www.example.com/)). You should see a padlock icon indicating that the connection is secure.

**Step 6: Automatic Renewal (Optional):**
Certbot can automatically renew your SSL/TLS certificates to ensure they don't expire. Certbot will set up a cron job to run renewal checks daily. You can check the renewal status with:

```bash
bashCopy code
sudo certbot renew --dry-run

```

**Step 7: Secure Your Server (Optional):**
While setting up HTTPS is an essential step for security, you should also ensure that your server and web application are securely configured. This includes proper security group settings, firewall rules, and secure application coding practices.

That's it! You've successfully set up HTTPS using Certbot on your EC2 instance, and your website or application is now accessible via a secure HTTPS connection. Make sure to monitor certificate expiration and renew it before it expires to maintain a secure website.