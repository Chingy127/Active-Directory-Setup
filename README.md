<h2>
<img width="120" alt="Active Directory Logo" src="images/AD.png">
Active Directory Lab – Installing Active Directory Domain Services (AD DS)
</h2>

<p>
With the lab environment fully configured and connectivity verified, the next step is installing 
<strong>Active Directory Domain Services (AD DS)</strong> on the Domain Controller. 
Active Directory provides centralized authentication, authorization, and directory management for users, computers, and other resources within a Windows network.
</p>

<p>
In this section, the Domain Controller virtual machine (<strong>DC-01</strong>) will be prepared for Active Directory installation using the Server Manager role installation wizard.
</p>

<br>

<h3>Opening Server Manager</h3>

<p>
Begin by opening the Start menu on the Domain Controller and launching <strong>Server Manager</strong>.
Server Manager is the primary administrative console used to manage roles, features, and server configurations within Windows Server environments.
</p>

<p>
<img width="1400" alt="Opening Server Manager from Start Menu" src="images/01-ADSetup.png">
</p>

<br>

<h3>Adding Roles and Features</h3>

<p>
Within the Server Manager dashboard, select <strong>Add roles and features</strong>.
This option launches the Add Roles and Features Wizard, which allows administrators to install services such as Active Directory, DNS, DHCP, and other server roles.
</p>

<p>
<img width="1400" alt="Selecting Add Roles and Features in Server Manager" src="images/02-ADSetup.png">
</p>

<br>

<h3>Selecting the Destination Server</h3>

<p>
When the Add Roles and Features Wizard opens, navigate to the <strong>Server Selection</strong> step.
Ensure that the Domain Controller virtual machine (<strong>DC-01</strong>) is selected as the destination server for the installation.
</p>

<p>
<img width="1400" alt="Selecting DC-01 as the destination server" src="images/03-ADSetup.png">
</p>

<br>

<h3>Selecting the Active Directory Domain Services Role</h3>

<p>
In the <strong>Server Roles</strong> section, locate and select <strong>Active Directory Domain Services</strong>.
This role installs the core services required to create and manage an Active Directory domain.
</p>

<p>
<img width="1400" alt="Selecting Active Directory Domain Services role" src="images/04-ADSetup.png">
</p>

<p>
When prompted, choose <strong>Add Features</strong> to install the additional management tools required for Active Directory administration.
These tools include utilities such as the Active Directory Administrative Center, PowerShell modules, and management consoles used to administer domain objects.
</p>

<br>

<h3>Confirming Required Features</h3>

<p>
The wizard will display the features that will be installed alongside Active Directory Domain Services.
These supporting tools are necessary for managing domain controllers, users, organizational units, and group policies.
</p>

<p>
<img width="1400" alt="Reviewing required Active Directory features" src="images/05-ADSetup.png">
</p>

<p>
After reviewing the required features, select <strong>Next</strong> to proceed through the remaining configuration steps.
</p>

<p>
The installation wizard will continue with additional configuration screens before the Active Directory Domain Services role is installed on the server.
</p>

<br>

<h3>Confirming Installation of Active Directory Domain Services</h3>

<p>
Before the role installation begins, the Add Roles and Features Wizard displays a summary of the selected components that will be installed on the server.
</p>

<p>
<img width="1400" alt="Confirm installation selections for AD DS role" src="images/06-ADSetup.png">
</p>

<p>
Review the listed components, which include Active Directory Domain Services along with the required administrative tools. 
Once the configuration is confirmed, select <strong>Install</strong> to begin installing the role on the Domain Controller.
</p>

<br>

<h3>Active Directory Domain Services Installation Progress</h3>

<p>
The wizard will begin installing the selected role and required features on the server.
</p>

<p>
<img width="1400" alt="AD DS installation progress window" src="images/07-ADSetup.png">
</p>

<p>
Once the installation finishes successfully, the wizard indicates that additional configuration is required before the server can function as a Domain Controller.
At this point, the server must be promoted to a domain controller.
</p>

<br>

<h3>Promoting the Server to a Domain Controller</h3>

<p>
After installation completes, Server Manager displays a notification indicating that post-deployment configuration is required.
Select <strong>Promote this server to a domain controller</strong> to launch the Active Directory Domain Services Configuration Wizard.
</p>

<p>
<img width="1400" alt="Server Manager notification to promote server to domain controller" src="images/08-ADSetup.png">
</p>

<br>

<h3>Creating a New Active Directory Forest</h3>

<p>
Within the Deployment Configuration step, choose <strong>Add a new forest</strong>.
This option creates a completely new Active Directory environment.
</p>

<p>
<img width="1400" alt="Creating new Active Directory forest" src="images/09-ADSetup.png">
</p>

<p>
Enter a root domain name for the environment. In this lab, the domain name <strong>mydomain.com</strong> is used to represent the internal Active Directory domain.
</p>

<br>

<h3>Configuring Domain Controller Options</h3>

<p>
Next, configure the domain controller settings for the new forest.
</p>

<p>
<img width="1400" alt="Domain controller options configuration" src="images/10-ADSetup.png">
</p>

<p>
The forest and domain functional levels are set to <strong>Windows Server 2025</strong>, allowing the environment to use the latest Active Directory features available for this server version.
</p>

<p>
A <strong>Directory Services Restore Mode (DSRM) password</strong> must also be configured. 
This password is used for recovery and maintenance tasks if the Active Directory database ever needs to be restored.
</p>

<br>

<h3>DNS Configuration Warning</h3>

<p>
During the DNS Options step, a warning may appear indicating that a delegation for the DNS server cannot be created.
</p>

<p>
<img width="1400" alt="DNS delegation warning during AD DS setup" src="images/11-ADSetup.png">
</p>

<p>
This warning is expected in a new lab environment because there is no existing parent DNS infrastructure.
Since this is the first domain controller in a new forest, the system will automatically install and configure the DNS service for the new domain.
</p>

<p>
Select <strong>Next</strong> to continue with the remaining configuration steps.
</p>

<br>

<h3>Configuring the NetBIOS Domain Name</h3>

<p>
During the Additional Options step, the wizard automatically assigns a NetBIOS name to the domain based on the root domain name that was previously configured.
</p>

<p>
<img width="1400" alt="NetBIOS domain name configuration" src="images/12-ADSetup.png">
</p>

<p>
The NetBIOS domain name is used for compatibility with legacy systems and older authentication methods. In this lab, the NetBIOS name <strong>MYDOMAIN</strong> is automatically generated from the root domain <strong>mydomain.com</strong>. The default value is accepted and the configuration proceeds by selecting <strong>Next</strong>.
</p>

<br>

<h3>Running Active Directory Prerequisite Checks</h3>

<p>
Before the domain controller promotion begins, the system performs a set of prerequisite checks to validate the configuration.
</p>

<p>
<img width="1400" alt="Active Directory prerequisite validation checks" src="images/13-ADSetup.png">
</p>

<p>
These checks verify that the server environment is prepared for Active Directory Domain Services installation. Warnings may appear regarding DNS delegation or static IP configuration. In a new lab environment, these warnings are expected and do not prevent installation.
</p>

<p>
After confirming that all required checks have passed, select <strong>Install</strong> to begin the domain controller promotion process.
</p>

<br>

<h3>Domain Controller Installation and Automatic Restart</h3>

<p>
Once installation begins, the server configures the Active Directory database, DNS services, and domain controller functionality.
</p>

<p>
<img width="1400" alt="Server restarting after AD DS installation" src="images/14-ADSetup.png">
</p>

<p>
After the installation completes, the system automatically restarts the server to finalize the configuration of Active Directory Domain Services.
</p>

<br>

<h3>Logging Back Into the Domain Controller</h3>

<p>
After the reboot, the administrator reconnects to the server using domain credentials.
</p>

<p>
<img width="1400" alt="Remote login using domain credentials" src="images/15-ADSetup.png">
</p>

<p>
Instead of using the local administrator account, the login now uses the newly created domain account format:
<strong>mydomain\user#1</strong>. This confirms that the server is now operating as a domain controller within the Active Directory environment.
</p>

<br>

<h3>Opening Active Directory Users and Computers</h3>

<p>
With Active Directory successfully installed, administrative tools become available on the server. The Active Directory Users and Computers console can be opened through the Windows search menu.
</p>

<p>
<img width="1400" alt="Searching for Active Directory Users and Computers" src="images/17-ADSetup.png">
</p>

<p>
This management console is used to create and manage users, groups, computers, and organizational units within the Active Directory domain.
</p>

<br>

<h3>Verifying the Active Directory Domain</h3>

<p>
Opening the Active Directory Users and Computers console confirms that the domain environment has been successfully created.
</p>

<p>
<img width="1400" alt="Active Directory Users and Computers console showing new domain" src="images/18-ADSetup.png">
</p>

<p>
The domain <strong>mydomain.com</strong> now appears within the directory structure. From this interface, administrators can begin managing domain resources, creating user accounts, and organizing directory objects for the enterprise environment.
</p>

<br>

<h3>Active Directory Deployment Complete</h3>

<p>
At this stage, the domain controller is fully configured and the Active Directory environment is operational. The server now provides centralized authentication, directory services, and policy management for systems that join the domain.
</p>
