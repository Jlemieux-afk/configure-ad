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
- Step 2 Install active directory to the AD-1 and enable it as a Domain Controller
- Step 3 
- Step 4 Configure Active Directory with basic secruity permissions for a couple users

<h2>Deployment and Configuration Steps</h2>

Created 2 VM's in Azure, one useing a Win10 Server for Active Drectory Domain Controller, and the other using Win10 Enterprise for the EndUser
<p>
<table>
  <tr>
    <td><img width="864" height="770" alt="image" src="https://github.com/user-attachments/assets/ba08ce62-9fd1-4769-9388-87fa5eb51810" />
</td>
    <td><img width="861" height="464" alt="image" src="https://github.com/user-attachments/assets/473fbd79-c4e9-46a3-87a5-153eb5da5e86" />
</td>
    <td><img width="789" height="541" alt="image" src="https://github.com/user-attachments/assets/ddb889d8-b4f5-4690-9f14-b428c382f321" />
</td>
    <td><img width="831" height="737" alt="image" src="https://github.com/user-attachments/assets/2fd736a3-3646-4df3-b73a-6a55e05c8855" />
</td>
  </tr>
  <tr>
    <td align="center">Active Directory Server setup</td>
    <td align="center">Network for Active Directory</td>
    <td align="center">Client 1 set up</td>
    <td align="center">Client 2 also on the same network</td>
  </tr>
</table>

</p>

<p>
Then configured the network for AD-1 to have a static 10.0.0.4 IP address to prevent random IP configuration errors.
</p>
<br />

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
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
