<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud with MFA for extra security(Azure)</h1>

This project outlines the implementation of Active Directory within Azure Virtual Machines and then adds MultiFactor Authentication through Microsoft Entra ID within Azure<br />


- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- Microsoft Entra ID

<h2>Operating Systems Used </h2>

- Windows Server 2022 Datacenter
- Windows 10 Enterprise LTSC 2021

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 Create VM server to house Active Directory (AD-1) and a VM (Client-1) for Utilization in a single network
- Step 2 Install Active Directory (AD) to the AD-1 and enable it as a Domain Controller (DC)
- Step 3 
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
<p>
Confirmed that Client-1 saw AD-1 as it's DNS server
</p>
<br />
<p>
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/cb02adf3-2ff8-4352-a096-d7d04575a420" />
</p>
<p>
On AD-1, Install Active Directory Services from the server manager. After it's installed click the flag at the top and promote server to new forest. Enter domain name, password and install for AD-1 to become a Domain Controller
</p>
<br />
<table>
  <tr>
    <td><img width="1522" height="854" alt="image" src="https://github.com/user-attachments/assets/2be330d7-0910-4d41-af97-80b371fc648b" />
</td>
    <td><img width="1426" height="762" alt="image" src="https://github.com/user-attachments/assets/95b3f15d-7b22-46ff-a0a4-e973aee5b465" />
</td>
    <td><img width="1437" height="750" alt="image" src="https://github.com/user-attachments/assets/737720e2-dbd6-4f6a-a696-7059e85def59" />
</td>
    <td><img width="796" height="573" alt="image" src="https://github.com/user-attachments/assets/ef727233-4532-445c-b69d-a4f7798ad406" />
</td>
    <td><img width="783" height="573" alt="image" src="https://github.com/user-attachments/assets/b1c37d9a-8db3-4cbe-a206-e47fa670b91b" />
</td>
  </tr>
  <tr>
    <td align="center">Add Roles</td>
    <td align="center">Active Directory Domain Services, click next and install</td>
    <td align="center">Promote this server to a domain controller</td>
    <td align="center">Make a new forest, and enter a root domain name. I chose company.com</td>
    <td align="center">Proceed through the windows and install</td>
  </tr>
</table>
