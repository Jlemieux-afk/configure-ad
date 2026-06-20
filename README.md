<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed and Configured in the Cloud (Azure)</h1>

This project outlines the implementation of Active Directory within Azure Virtual Machines. The idea is to set up a back-end server to allow for adding computer resources as well as admin/employee users that have permission to use remote desktops for computing.<br />


- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- Microsoft Entra ID

<h2>Operating Systems Used </h2>

- Windows Server 2022 Datacenter
- Windows 10 Enterprise LTSC 2021

<h2>Deployment and Configuration Steps</h2>

- Step 1 Create VM server to house Active Directory (AD-1) and a VM (Client-1) for Utilization in a single network
- Step 2 Install Active Directory (AD) to the AD-1 and enable it as a Domain Controller (DC)
- Step 3 Create Users to utilize the domain through active remote desktops
- Step 4 Configure Active Directory with basic secruity permissions for a couple users

<h2>Deployment and Configuration Steps</h2>

Created 2 VM's in Azure, one useing a Win10 Server for Active Drectory Domain Controller, and the other using Win10 Enterprise for the EndUser
<p>
<img width="1424" height="283" alt="image" src="https://github.com/user-attachments/assets/5eaba60b-7eef-46d4-9192-ab7fffe56e35" />
</p>
</br>
<p>
Then configured the network for AD-1 to have a static 10.0.0.4 IP address to prevent random IP configuration errors. Also made Client-1's DNS server AD-1's IP address
</p>
<p>
<table>
  <tr>
    <td><img width="1690" height="839" alt="image" src="https://github.com/user-attachments/assets/196b1319-570f-4d3b-a9b4-ca7f15146798" />
</td>
    <td><img width="1627" height="776" alt="image" src="https://github.com/user-attachments/assets/91371958-fc35-4205-82a6-fb73326b92b3" />
</td>
  </tr>
  <tr>
    <td align="center">AD-1 IP address changed to 10.0.0.4 static</td>
    <td align="center">CLient-1 DNS server changed to AD-1 IP address</td>
  </tr>
</table>
</p>
</br>
<p>
Confirmed that Client-1 saw AD-1 as it's DNS server
</p>
<p>
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/cb02adf3-2ff8-4352-a096-d7d04575a420" />
</p>
</br>
<p>
On AD-1, Install Active Directory Services from the server manager. After it's installed click the flag at the top and promote server to new forest. Enter domain name, password and install for AD-1 to become a Domain Controller
</p>
<table>
  <tr>
    <td><img width="1426" height="762" alt="image" src="https://github.com/user-attachments/assets/95b3f15d-7b22-46ff-a0a4-e973aee5b465" />
</td>
     <td><img width="796" height="573" alt="image" src="https://github.com/user-attachments/assets/ef727233-4532-445c-b69d-a4f7798ad406" />
</td>

  </tr>
  <tr>
    <td align="center">Active Directory Domain Services, click next and install</td>
    <td align="center">Make a new forest, and enter a root domain name. I chose company.com</td>
  </tr>
</table>
</br>
<p>
Created an OU for admins and employees to organize users.
</p>
<p> <img width="790" height="532" alt="image" src="https://github.com/user-attachments/assets/57ef6d58-98b0-4045-88ec-385f738e2518" />
</p>
</br>
<p> Created an admin for myself and one other to test access. Logged into Client-1 with both my and John Doe. Tried to log in the first time and it failed due to cridentials. Through some troubleshooting: I didn't give admin privileges to either acount. Fixed the error by adding them to the domain admins group. I also realized I didn't join Client 1 to the domain, which is another reason why the accounts wouldn't log on to that machine.</p>
<table>
  <tr>
    <td><img width="754" height="527" alt="image" src="https://github.com/user-attachments/assets/897e3d2f-a9ad-4920-bf4f-e1d3e54989dd" />
</td>
     <td><img width="452" height="578" alt="image" src="https://github.com/user-attachments/assets/3ae99950-8420-4dae-927f-2276428810eb" />
</td>
<td><img width="440" height="525" alt="image" src="https://github.com/user-attachments/assets/e86c98ec-3da4-4a2c-8eb2-f6fedcc511c8" />
</td>
<td><img width="1193" height="896" alt="image" src="https://github.com/user-attachments/assets/a3d0e860-8792-408d-b25b-da572bcb4aba" />
</td>
  </tr>
  <tr>
    <td align="center">names listed as admin</td>
    <td align="center">logging in to client-1 using domain login. it failed</td>
    <td align="center">Added "domain users" to the "members of" to fix the issue</td>
    <td align="center">Logged onto Client 1, changed "member of" to domain "company.com"</td>
  </tr>
</table>
</br>
<p>Success!
</p>
<p><img width="791" height="541" alt="image" src="https://github.com/user-attachments/assets/76bc8303-63bc-42c0-a3ab-5ff1936ef4ea" />
</p>
</br>
<p>Logged in again with created accounts to Client-1. Access works with both admins. </p>
<p>
<table>
  <tr>
    <td><img width="453" height="578" alt="image" src="https://github.com/user-attachments/assets/c461dab0-8167-48dd-8a9d-bb4f8ab80046" />

</td>
     <td><img width="1217" height="796" alt="image" src="https://github.com/user-attachments/assets/4c780f12-04d7-4224-84ca-919691b3ee36" />
</td>

  </tr>
  <tr>
    <td align="center">Logging in again</td>
    <td align="center">success!</td>
  </tr>
</table>
</br>
<p> Created a new OU in AD for the computers being accessed. Created a GPO under _computers and edited it to allow users in the group to access the remote desktop. Then under user rights assignment added company\domain users to be allowed </p>
<p><table>
  <tr>
    <td><img width="728" height="493" alt="image" src="https://github.com/user-attachments/assets/0bceb664-fa53-4dde-8b25-53b818fc242b" />
</td>
     <td><img width="998" height="679" alt="image" src="https://github.com/user-attachments/assets/a4c9c4e0-661b-441b-9707-70f36c6c633c" />
</td>
    <td><img width="691" height="579" alt="image" src="https://github.com/user-attachments/assets/25c7fd23-95ce-45f2-88cd-2e2a58c8a83d" />
</td>
    <td><img width="864" height="735" alt="image" src="https://github.com/user-attachments/assets/2aaf4ae4-ebce-4a1d-9b8a-8b80e3b87993" />
</td>

  </tr>
  <tr>
    <td align="center">New OU for the computers being accessed</td>
    <td align="center">edited the rule to enable "allow users to connect remotely"</td>
    <td align="center">Added "remote desktop users" with members of Domain Users</td>
    <td align="center">gpupdate /force on the client to update policy, check for localgroup "remote desktop users" "members COMPANY/Domain Users"</td>
  </tr>
</table></p>
</br>
<p>Attmpted to log back into John Doe account with the updated policy, and it worked! To make sure it works for new hires, I added one more account to the employees folder </p>

<p>
  <table>
  <tr>
    <td><img width="942" height="781" alt="image" src="https://github.com/user-attachments/assets/7ecdb208-0ebc-48a6-bc67-7de23548fc71" />
</td>
     <td><img width="883" height="353" alt="image" src="https://github.com/user-attachments/assets/17335a70-4d5b-4f9e-ab0e-c0c93335f1d4" />
</td>

  </tr>
  <tr>
    <td align="center">Logging in as Tim Ward</td>
    <td align="center">success!</td>
  </tr>
</table>
</br>
<h2> Summary </h2>
<p>With the new AD DC configured, a company or group can now add users/admins to be able to log into local machines through remote desktop protocol. Anyone added to the Domain Admins group is able to configure or add people for the entire domain; anyone added as Domain Users will have access to the local machines for computing. Admins, users and computers are organized into 3 folders for a quick glance at available users as well as machines that are avialable on the network. </p>
