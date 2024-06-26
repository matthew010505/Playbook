# Ansible Playbook: Install and Deploy Application with Nginx

This Ansible playbook automates the deployment of an application with Nginx on remote servers. It installs Nginx, Node.js, and npm, creates necessary directories, copies the application files, installs dependencies, and builds the application.

## Prerequisites

- Ansible installed on your local machine.
- SSH access to remote servers with sudo privileges.
- Remote servers running a Debian-based Linux distribution (e.g., Ubuntu).

## Usage

1. **Clone the repository**:

   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```
2. **Update the Inventory File**:
    
    ```bash
        [web]
        <server-ip>
    ```
3. **Modify playbook variables (deploy.yml)**:

    Update the app_dir variable to specify the path where your application should be deployed on the server.

    ```bash
        vars:
        node_version: "14.x"
        app_dir: /var/www/my-application  # Update this path
    ```
4.  **Run the playbook**:
     
      ```bash
       ansible-playbook -i inventory nginx_deploy.yml
      ```
**Playbook Structure**

    1.deploy.yml: Main Ansible playbook file.
    2.inventory: Inventory file listing remote server(s).
    3.README.md: This documentation file.
**Playbook Tasks**

    1.Update and Install Dependencies  : Ensures the package cache is updated and installs required dependencies.

    2.Install Nginx: Installs the Nginx web server.

    3.Start Nginx: Starts the Nginx service.

    4.Install Node.js and npm: Installs Node.js and npm.

    5.Ensure app directory Exists: Creates the directory where the application will be deployed.
    
    6.Copy application to server: Copies the application files to the specified directory on the server.

    7.Install Project Dependencies: Installs dependencies required by the application using npm.

    8.Build the Application: Executes the npm build command to build the application.

    9.Customization: Modify variables such as node_version and app_dir in deploy.yml to suit your application and environment.

    10.Update : Nginx configuration (nginx.conf) or application build commands (npm run build) as needed.


**Notes**

    Ensure your application repository (./application in the playbook) contains the necessary files and configuration for deployment.

    Adjust ownership and permissions (owner, group, mode) as per your server setup and security requirements.
     


    

