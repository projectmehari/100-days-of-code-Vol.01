# Day 86

Tags: Backend development
Date: October 8, 2023
Status: Done

Tasks of the day

- Monit
- Github Actions
- Ansible
- Terraform

Exercise // Knowledge checkpoints

- Monitoring
- CI / CD
- Automation
- Infrastructure

---

### Monit

When it comes to monitoring the health of your applications, there are several different options available. My favorite monitoring stack is Prometheus and Grafana, but it can be a bit overwhelming to set up and configure. If you’re looking for a simpler solution, **Monit** is a great alternative that can be utilized to monitor and manage system resources such as services, processes, files, directories, devices, and network connections, making your application more reliable and resilient to issues like crashes, unresponsiveness, or resource exhaustion.

Some of the keys features of Monit are:

- **Automatic Recovery:** Monit can automatically restart a service or process if it fails, making your application more resistant to unexpected issues.
- **Alert Notifications:** Monit can send email notifications when a problem is detected or when a certain condition is met, keeping you informed about the health of your application.
- **Event Logging:** All events detected by Monit are stored in a log for easy troubleshooting and analysis.
- **Resource Limit Monitoring:** Monit can monitor the resource utilization (CPU, memory, network, etc.) of a process or service and take action if a specific limit is exceeded.
- **Flexible Configuration:** Monit uses a simple, human-readable configuration syntax that allows you to tailor its behavior to your needs.
- **Web Interface:** Monit provides a built-in web interface for remotely monitoring your application’s status and manage services.

[https://www.youtube.com/watch?v=3cA5lNje1Ow](https://www.youtube.com/watch?v=3cA5lNje1Ow)

Have a look at the following resources to learn more about Monit:

- **[Monit - Opensource Self Healing Server Monitoring](https://www.youtube.com/watch?v=3cA5lNje1Ow)**
- **[Monit documentation](https://mmonit.com/monit/documentation/)**

---

### Github Actions

GitHub Actions is a workflow automation tool provided by GitHub that can be used to automate various tasks in the app development process. It makes it easy to automate all your software workflows, now with world-class CI/CD. Build, test, and deploy your code right from GitHub. Make code reviews, branch management, and issue triaging work the way you want.

Demo code: https://github.com/fireship-io/225-github-actions-demo

### 4 ways to DevOps-ify your App - Github Actions Tutorial

[https://www.youtube.com/watch?v=eB0nUzAI7M8](https://www.youtube.com/watch?v=eB0nUzAI7M8)

1. **[Continuous integrations](https://www.atlassian.com/continuous-delivery/continuous-integration):** Continuous integration (CI) is the practice of automating the integration of code changes from multiple contributors into a single software project. It’s a primary [DevOps best practice](https://www.atlassian.com/devops/what-is-devops/devops-best-practices), allowing developers to frequently merge code changes into a central repository where builds and tests then run. Automated tools are used to assert the new code’s correctness before integration.

A source code version control system is the crux of the CI process. The version control system is also supplemented with other checks like automated code quality tests, syntax style review tools, and more.

2. **[Continuous Deployment](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwia-LPoheeBAxWjEVkFHbO-BBAQFnoECDEQAQ&url=https%3A%2F%2Faws.amazon.com%2Fdevops%2Fcontinuous-delivery%2F&usg=AOvVaw3DX0CHXog8rz-L54s93jV4&opi=89978449):** Continuous deployment is **a strategy in software development where code changes to an application are released automatically into the production environment**. This automation is driven by a series of predefined tests. Once new updates pass those tests, the system pushes the updates directly to the software's users.

3. [Publish NPM Packages](https://www.freecodecamp.org/news/how-to-create-and-publish-your-first-npm-package/)

4. Schedule background jobs : How do I export Firestore data on a regular basis?
    1. Crontab guru app

---

**Ansible**

Ansible is an open-source configuration management, application deployment and provisioning tool that uses its own declarative language in YAML. Ansible is agentless, meaning you only need remote connections via SSH or Windows Remote Management via Powershell in order to function.

[https://www.youtube.com/watch?v=7GJjhZoYEus](https://www.youtube.com/watch?v=7GJjhZoYEus)

Visit the following resources to learn more:

- **[Ansible Website](https://www.ansible.com/)**
- **[Official Documentation](https://docs.ansible.com/)**
- **[Ansible Getting Started Guide](https://www.ansible.com/resources/get-started)**
- **[Ansible Full Course for Beginners](https://www.youtube.com/watch?v=9Ua2b06oAr4)**

---

### Terraform

Terraform is an extremely popular open source Infrastructure as Code (IaC) tool that can be used with many different cloud and service provider APIs. Terraform focuses on an immutable approach to infrastructure, with a terraform state file center to tracking the status of your real world infrastructure.

[https://www.youtube.com/watch?v=h970ZBgKINg](https://www.youtube.com/watch?v=h970ZBgKINg)

Visit the following resources to learn more:

- **[Terraform Website](https://www.terraform.io/)**
- **[Terraform Documentation](https://www.terraform.io/docs)**
- **[Terraform Tutorials](https://learn.hashicorp.com/terraform)**
- **[Intro to Terraform Video](https://www.youtube.com/watch?v=h970ZBgKINg&ab_channel=HashiCorp)**
- **[Terraform CDK Website](https://www.terraform.io/cdktf)**
- **[What is the CDKTF?](https://www.terraform.io/cdktf/concepts/cdktf-architecture)**
- **[CDKTF Getting Started Guide](https://learn.hashicorp.com/tutorials/terraform/cdktf-install?in=terraform/cdktf)**
- **[CDKTF Examples](https://www.terraform.io/cdktf/examples)**
- **[How to Scale Your Terraform Infrastructure](https://thenewstack.io/how-to-scale-your-terraform-infrastructure/)**

---

### Exercise - Monitoring

To implement monitoring and autorestarts for your application using Monit and optionally PM2, follow these step-by-step instructions:

**Step 1: Install Monit**

If Monit is not already installed on your system, you can install it using your system's package manager. For example, on a Debian-based system like Ubuntu, you can use the following command:

```bash
bashCopy code
sudo apt-get install monit

```

**Step 2: Configure Monit**

Monit configuration files are typically located in **`/etc/monit/`**. Follow these sub-steps:

2.1. Create a configuration file for your application in **`/etc/monit/conf-available/`**, e.g., **`/etc/monit/conf-available/your-app`**.

2.2. Edit the configuration file you just created. You can use a text editor like **`nano`** or **`vim`**. Here's a basic example of a Monit configuration for your application:

```bash
bashCopy code
check process your-app with pidfile /path/to/your-app.pid
  start program = "/path/to/your-app/start-script"
  stop program = "/path/to/your-app/stop-script"
  if totalmem > 80.0 MB for 5 cycles then restart
  if cpu > 95% for 5 cycles then restart
  if failed port 80 protocol HTTP
    request /
    with timeout 10 seconds
    then restart

```

Replace **`/path/to/your-app`** with the actual path to your application and adjust the monitoring conditions as needed.

2.3. Once you've configured your Monit file, create a symbolic link to it in the **`/etc/monit/conf-enabled/`** directory:

```bash
bashCopy code
sudo ln -s /etc/monit/conf-available/your-app /etc/monit/conf-enabled/

```

**Step 3: Test Your Monit Configuration**

Before proceeding, test your Monit configuration to ensure there are no syntax errors:

```bash
bashCopy code
sudo monit -t

```

If the configuration is valid, you should see a message indicating "Control file syntax OK."

**Step 4: Start Monit**

Start the Monit service:

```bash
bashCopy code
sudo systemctl start monit

```

**Step 5: Access the Monit Web Interface (Optional)**

Monit provides a web interface for monitoring and managing services. To access it, you can open a web browser and navigate to **`http://localhost:2812`**. You'll need to log in with the username and password specified in **`/etc/monit/monitrc`**.

**Step 6: Configure PM2 for Autorestarts (Optional)**

If you want to use PM2 for autorestarts in addition to Monit, you can install PM2 and set up your application:

```bash
bashCopy code
npm install -g pm2
cd /path/to/your-app
pm2 start your-app.js
pm2 save

```

This will configure PM2 to start and monitor your application.

**Step 7: Monitor Other Metrics (Optional)**

To monitor CPU usage, memory usage, disk usage, network usage, and service availability, you may need to set up additional Monit configurations. You can create separate Monit configuration files for each metric or service and enable them in **`/etc/monit/conf-enabled/`** following a similar process as in Step 2.

**Step 8: Monitor Process Availability**

To monitor the availability of specific processes, you can create additional Monit configurations using the **`check process`** directive, as shown in the example configuration in Step 2.2.

**Step 9: Restart Services**

After making changes to Monit configurations, restart the Monit service to apply the changes:

```bash
bashCopy code
sudo systemctl restart monit

```

Your application is now being monitored by Monit, and optionally, it is being managed by PM2 for autorestarts. You can access Monit's web interface to view metrics and manage your services as needed.

---

### Exercise - CI / CD

Setting up CI/CD for your application using GitHub Actions is a crucial step towards automating your deployment process. Follow these steps to implement CI/CD for your application:

**Step 1: Watch DevOps CI/CD Explained in 100 Seconds**
If you're not already familiar with CI/CD, start by watching "DevOps CI/CD Explained in 100 Seconds" to get a basic understanding of what Continuous Integration and Continuous Deployment are.

**Step 2: Create a GitHub Repository**
If you haven't already, create a GitHub repository for your application. Make sure your application code is in this repository.

**Step 3: Set Up AWS**
Ensure you have an AWS account set up, and you should have an EC2 instance or another server where you want to deploy your application.

**Step 4: Create a GitHub Action Workflow**
Create a GitHub Actions workflow file in your repository. You can create a new file named **`.github/workflows/main.yml`**. In this file, you will define the workflow for CI/CD. Here's a sample workflow using rsync:

```yaml
yamlCopy code
name: CI/CD with GitHub Actions

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Install dependencies (if needed)
      run: |
        # Add any commands here to install project dependencies
        # For example, npm install or pip install

    - name: Deploy to AWS
      run: |
        ssh-keyscan -H your-aws-server-ip >> ~/.ssh/known_hosts
        rsync -r --delete-after --exclude=".git" $GITHUB_WORKSPACE/ username@your-aws-server-ip:/path/to/destination
      env:
        SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}

```

Make sure to replace **`your-aws-server-ip`**, **`username`**, and **`/path/to/destination`** with your AWS server details.

**Step 5: Set Up SSH Key**
To securely connect to your AWS server, you need to set up an SSH key. Create an SSH key pair if you haven't already. Add the public key to your AWS server's **`~/.ssh/authorized_keys`** file. Then, add the private key as a secret in your GitHub repository named **`SSH_PRIVATE_KEY`**.

You can add secrets by going to your repository > Settings > Secrets > New repository secret.

**Step 6: Push to Master**
Whenever you push changes to the **`master`** branch, this GitHub Action workflow will automatically run.

With these steps, you have implemented CI/CD for your application using GitHub Actions. Now, every push to the **`master`** branch will trigger a deployment of your application to your AWS server using rsync. Make sure to adapt this workflow to your specific project's needs, such as installing project dependencies or configuring your application for production use.

---

### Exercise - Automation

**Objective:** Automate the deployment of an application on a new EC2 instance using Ansible.

Prerequisites:

1. AWS Account with Access Keys.
2. Ansible installed on your local machine.
3. Knowledge of SSH and SSH keys.
4. An existing Ansible project directory.

**Step 1: Set Up Ansible Directory**

- Open your terminal and navigate to your Ansible project directory.

**Step 2: Create Ansible Playbook**

- Inside your Ansible project directory, create a new YAML playbook file (e.g., **`deploy_app.yml`**) using a text editor.

**Step 3: Define Hosts and Variables**

- In the playbook, define the target hosts (your EC2 instance(s)) and any necessary variables. For example:

```yaml
yamlCopy code
---
- name: Deploy Application
  hosts: ec2_instance
  become: yes
  vars:
    app_directory: /path/to/your/app

```

**Step 4: Define Tasks**

- Define tasks to automate the setup. You can use Ansible modules like **`yum`**, **`apt`**, or **`shell`** to execute commands on the remote server. For example:

```yaml
yamlCopy code
  tasks:
    - name: Update Package Cache
      yum:
        name: '*'
        state: latest
      become: yes

    - name: Install Node.js
      shell: curl -sL https://deb.nodesource.com/setup_14.x | bash -
      become: yes

    - name: Install Git
      yum:
        name: git
        state: present
      become: yes

    - name: Install PostgreSQL
      yum:
        name: postgresql-server
        state: present
      become: yes

    - name: Start PostgreSQL Service
      service:
        name: postgresql
        state: started
      become: yes

    - name: Clone Git Repository
      git:
        repo: https://github.com/your/repository.git
        dest: "{{ app_directory }}"
      become: yes

    - name: Install Application Dependencies
      npm:
        path: "{{ app_directory }}"
        name: production
      become: yes

```

**Step 5: Run the Playbook**

- Save the playbook and run it using the **`ansible-playbook`** command:

```bash
bashCopy code
ansible-playbook -i your_inventory_file deploy_app.yml

```

Ensure that **`your_inventory_file`** contains the IP address or DNS name of your EC2 instance(s).

**Step 6: Verify the Deployment**

- After the playbook execution is complete, SSH into your EC2 instance and verify that the application is deployed correctly.

Congratulations! You've automated the deployment of your application using Ansible. This exercise helps you understand how to use Ansible playbooks to streamline the setup and configuration of remote servers. You can further enhance the playbook to suit your specific application and environment requirements.

---

### Exercise - Infrastructure

here's a step-by-step exercise to automate the process of creating infrastructure for your application using Terraform, provisioning with Ansible, setting up CI/CD with GitHub Actions, and implementing monitoring using Monit:

**Step 1: Define Your Application Infrastructure**

Before you start automating, you need to have a clear understanding of your application's infrastructure requirements. Create a Terraform configuration file (e.g., **`main.tf`**) that defines the infrastructure components such as virtual machines, networking, databases, and any other resources your application needs.

**Step 2: Set Up Terraform**

If you haven't already, install Terraform on your local development machine. You can download it from the official Terraform website ([https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html)) and follow the installation instructions for your platform.

**Step 3: Initialize Terraform**

Navigate to the directory containing your Terraform configuration file (**`main.tf`**) and run the following command to initialize your Terraform workspace:

```bash
bashCopy code
terraform init

```

This will download any necessary providers and initialize your working directory.

**Step 4: Plan Your Infrastructure**

Use the following command to create an execution plan, which will show you what Terraform will do when you apply your configuration:

```bash
bashCopy code
terraform plan

```

Review the plan to ensure that Terraform will create the desired infrastructure.

**Step 5: Apply Your Infrastructure**

Execute the plan to create your infrastructure:

```bash
bashCopy code
terraform apply

```

Confirm by typing "yes" when prompted. Terraform will create the infrastructure defined in your configuration file.

**Step 6: Set Up Ansible**

Install Ansible on your local machine if you haven't already. You can follow the installation instructions for your platform here: [https://docs.ansible.com/ansible/latest/installation_guide/index.html](https://docs.ansible.com/ansible/latest/installation_guide/index.html)

**Step 7: Create Ansible Playbooks**

Write Ansible playbooks to automate the provisioning and configuration of your application on the infrastructure you've created. Store these playbooks in a separate directory, e.g., **`ansible/`**.

**Step 8: Set Up GitHub Repository**

Create a GitHub repository to store your Terraform and Ansible code. Initialize a Git repository in your project directory and push it to GitHub.

**Step 9: Configure GitHub Actions**

In your GitHub repository, create a **`.github/workflows`** directory and add a GitHub Actions workflow YAML file. This workflow should define the CI/CD pipeline for your application. It should include steps to:

- Check out the code from the repository.
- Use Terraform to apply infrastructure changes.
- Use Ansible to provision and configure the application.
- Deploy the application.
- Run tests if applicable.
- Push the application to production if all previous steps are successful.

Commit and push this workflow to your GitHub repository.

**Step 10: Implement Monitoring with Monit**

Install Monit on your servers and configure it to monitor key aspects of your application, such as server health, application processes, and system resources. Create Monit configuration files to define the monitoring rules.

**Step 11: Test the Entire Workflow**

Make a change to your application code or infrastructure, commit it to the repository, and push it to GitHub. Watch the GitHub Actions workflow execute the CI/CD pipeline automatically.

**Step 12: Monitor and Maintain**

Regularly review Monit alerts and the GitHub Actions workflow to ensure your infrastructure is running smoothly. Make necessary updates to your Terraform and Ansible code as your application evolves.

By following these steps, you can achieve a fully automated infrastructure and deployment pipeline for your application, incorporating Terraform, Ansible, GitHub Actions, and Monit for infrastructure setup, provisioning, CI/CD, and monitoring, respectively.