<h1>Deploying Active Directory</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022</b>

<h2>1. Install Active Directory Domain Services on the Domain Controller</h2>
Open Server Manager: On your Domain Controller machine, open Server Manager (this should be on the desktop or in the Start menu).
Add Roles and Features:
In Server Manager, click on Add roles and features.
Choose Role-based or feature-based installation, then click Next.
Select the Active Directory Domain Services role, and click Next.
Follow the prompts to complete the installation, then click Install.
<h2>2. Promote the Domain Controller and Create a New Forest</h2>
Promote Server to Domain Controller:
After the installation is complete, you’ll see a notification to Promote this server to a domain controller. Click on this notification.
Create a New Forest:
Choose the option to Add a new forest.
Enter a Root Domain Name (e.g., example.com).
Click Next and follow the prompts to set the domain and forest functional levels, provide a Directory Services Restore Mode (DSRM) password, and proceed with the configuration.
Complete Setup:
Once done, the server will need to reboot. After reboot, the server will now be the Domain Controller for your new domain.
<h2>3. Login to the Domain Controller</h2>
When logging back in, since the server is now a domain controller, you’ll need to specify the domain name and user account.
For example, login as DOMAIN\Administrator or the account you created during setup.
<h2>4. Create Domain Admin User</h2>
Step 4.1: Create Organizational Units (OUs)
Open Active Directory Users and Computers (ADUC):
Open the ADUC console (type Active Directory Users and Computers in the Start menu search bar and open it).
Create OUs:
Right-click on your domain (e.g., example.com), and select New > Organizational Unit.
Create two Organizational Units (OUs):
EMPLOYEES
ADMINS
Step 4.2: Create a Domain Admin User
Create New User:
Right-click on the ADMINS OU, select New > User.
Provide a name for the user (e.g., admin1), and complete the steps to create the user.
Add to Domain Admins Group:
After creating the user, right-click on the user account, select Properties.
Go to the Member Of tab, and click Add.
Type Domain Admins, click Check Names, and then click OK to add the user to the Domain Admins group.
<h2>5. Join Client VM to the Domain</h2>
Configure Client VM:
On the client machine (Client-1), go to Control Panel > System > Change settings (under "Computer name, domain, and workgroup settings").
Click Change to join the machine to the domain.
Enter the Domain name (e.g., example.com), and provide the credentials of a domain administrator account.
Restart the client machine after the change.
<h2>6. Verify Client VM in ADUC and Create a New OU for Clients</h2>
Verify in ADUC:
Go back to Active Directory Users and Computers (ADUC).
You should now see the Client-1 computer listed under your domain.
Right-click on the domain and create a new Organizational Unit (OU) named Clients.
Move Client-1 into the Clients OU by dragging it from the domain container into the new Clients OU.


