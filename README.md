<h1>Deploying Active Directory</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022</b>


<h1>Here's a simple, step-by-step guide to deploying Active Directory and setting up a domain controller:</h1>

<h2>1. Install Active Directory Domain Services</h2>
Open Server Manager: Go to your Domain Controller and open Server Manager.<br>
Add Role: Click on Add roles and features.<br>
Install AD DS: Choose Active Directory Domain Services and follow the prompts to install it. This service is essential for managing network security and resources.
<img width="1512" alt="Install ADDS" src="https://github.com/user-attachments/assets/5721ceb4-050a-4ae5-b4d0-f9bd4b7fe592" />

<h2>2. Promote the Server to a Domain Controller</h2>
Promote to Domain Controller: Once the installation is complete, a message will appear in Server Manager to Promote this server to a domain controller. Click it.<br>
Create a New Forest: Choose to create a New Forest, then enter a Root Domain Name (e.g., example.com).<br>
Set Password: Set a Directory Services Restore Mode (DSRM) password and click Next to complete the process.<br>
Reboot: The server will restart automatically after the promotion is complete.
<img width="1512" alt="Forest" src="https://github.com/user-attachments/assets/b074bfc1-cc65-4379-ae6b-46a3424e587a" />

<h2>3. Log into the Domain Controller</h2>
Login to Domain Controller: After the server restarts, log in using DOMAIN\Administrator (replace DOMAIN with your domain name).<br>
Domain Context: When logging in, you must specify the domain and user account because the server is now a Domain Controller

<h2>4. Create Organizational Units (OUs)</h2>
Open ADUC: Open Active Directory Users and Computers (ADUC) from the Start menu.<br>
Create OUs: Right-click your domain (e.g., example.com), select New > Organizational Unit.<br>
Create two OUs: EMPLOYEES and ADMINS.<br>
<img width="198" alt="OU Creations" src="https://github.com/user-attachments/assets/f3e9666e-8fba-4027-8086-df5317918700" />

<h2>5. Create a Domain Admin User</h2>
Create User: Right-click on the ADMINS OU, select New > User. Follow the prompts to create a user (e.g., admin1).<br>
Add to Domain Admins: After creating the user, right-click the user account, select Properties, go to the Member Of tab, and add them to the Domain Admins group.
<img width="1512" alt="create admin user" src="https://github.com/user-attachments/assets/f719a071-fad6-4ae4-9cf6-f0d8c7bc62be" />
<img width="1512" alt="make user admin" src="https://github.com/user-attachments/assets/56baf90b-4fbc-4c1e-b816-a576cf89d7c2" />

<h2>6. Join the Client VM to the Domain</h2>
Client VM Setup: On the Client VM, go to Control Panel > System > Change settings.<br>
Join Domain: Click Change and enter the domain name (e.g., example.com). Enter domain admin credentials to join the machine to the domain.<br>
Restart: Restart the client machine when prompted.
<img width="1512" alt="client1 to domain" src="https://github.com/user-attachments/assets/9f49a2a0-2c01-4682-ba19-68ef3e140c48" />

<h2>7. Verify the Client VM in Active Directory</h2>
Check in ADUC: Go back to Active Directory Users and Computers. You should see the Client-1 machine listed under your domain.<br>
Create Client OU: Create a new OU named Clients by right-clicking the domain and selecting New > Organizational Unit.<br>
Move Client-1: Move Client-1 into the Clients OU.
<img width="1000" alt="add to CLIENTS OU" src="https://github.com/user-attachments/assets/93594ad6-bb8f-44d7-9211-8b7e1ae7b112" />

