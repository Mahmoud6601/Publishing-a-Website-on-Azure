# Publishing a Website on Azure

This project demonstrates two methods to publish a website on Azure: using IIS on a Microsoft server hosted on a Virtual Machine (IaaS) and using Azure App Service (PaaS) via Azure Portal and Visual Studio.

## Method 1: Publishing Using IIS on a Microsoft Server (IaaS)

### Step 1: Set Up a Virtual Machine on Azure
1. **Sign in to Azure Portal**: Go to [Azure Portal](https://portal.azure.com) and sign in with your credentials.
2. **Create a Virtual Machine**:
   - Navigate to "Virtual Machines" from the left-hand menu.
   - Click on "Create" and choose "Virtual Machine."
   - Fill in the details, such as the resource group, VM name, region, image (choose a Windows Server image), size, and administrator account.
   - Configure the networking settings, such as Virtual Network and Subnet.
   - Review and create the VM.

### Step 2: Install IIS on the Virtual Machine
1. **Connect to the VM**:
   - In the Azure Portal, go to your VM and click on "Connect" to download the RDP file.
   - Open the RDP file and connect to the VM using the administrator credentials.
2. **Install IIS**:
   - Open the Server Manager on the VM.
   - Click on "Add roles and features."
   - In the wizard, select "Role-based or feature-based installation."
   - Choose the current server and select "Web Server (IIS)" from the server roles list.
   - Proceed through the wizard and install IIS.

### Step 3: Deploy the Website to IIS
1. **Prepare the Website**:
   - On your local machine, create or move your website files to a folder.
2. **Transfer Files to the VM**:
   - Use RDP or any file transfer method to move your website files to the VM.
   - Place the files in the `C:\inetpub\wwwroot\` directory.
3. **Configure IIS**:
   - Open the IIS Manager on the VM.
   - Expand the server node and select "Sites."
   - Right-click "Default Web Site" and choose "Manage Website" > "Browse" to view the website.
   - Optionally, configure bindings, SSL, etc., if needed.

### Step 4: Open the Website to External Traffic
1. **Update Network Security Group (NSG) Rules**:
   - In the Azure Portal, go to your VM's Networking settings.
   - Update the NSG to allow inbound traffic on port 80 (HTTP) or port 443 (HTTPS).
2. **Test the Website**:
   - Open a browser and enter the public IP address of the VM.
   - Your website should now be accessible.

## Method 2: Publishing Using Azure App Service (PaaS)

### Step 1: Create an Azure App Service
1. **Sign in to Azure Portal**: Go to [Azure Portal](https://portal.azure.com) and sign in with your credentials.
2. **Create an App Service**:
   - Navigate to "App Services" from the left-hand menu.
   - Click on "Create" and fill in the required details such as resource group, app name, publish type, runtime stack, and region.
   - Review and create the App Service.

### Step 2: Deploy the Website Using Visual Studio
1. **Prepare the Project in Visual Studio**:
   - Open Visual Studio and load your web application project.
   - Ensure your project is set to use the same runtime stack as your App Service (e.g., .NET, Node.js).
2. **Publish to Azure**:
   - Right-click on the project in Solution Explorer and select "Publish."
   - Choose "Azure" as the target, then "Azure App Service (Windows)."
   - Sign in to your Azure account if prompted.
   - Select the existing App Service you created or create a new one directly from Visual Studio.
   - Configure any necessary deployment settings, then click "Publish."

### Step 3: Manage and Monitor Your App Service
1. **Monitor Your App**:
   - In Azure Portal, navigate to your App Service and view metrics such as CPU, memory, and HTTP requests.
   - Set up alerts if needed.
2. **Configure Custom Domain and SSL (Optional)**:
   - In your App Service, navigate to "Custom domains" and add a custom domain.
   - Add SSL binding if you have an SSL certificate.

### Step 4: Access Your Website
1. **Access via Default Domain**:
   - You can access your website using the default Azure-provided domain (`<your-app-name>.azurewebsites.net`).
2. **Access via Custom Domain** (if configured):
   - Use your custom domain to access the website.

