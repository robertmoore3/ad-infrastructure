<p align="center">
<img src="https://github.com/user-attachments/assets/2a666083-7f44-48eb-ab51-728daafd40dd" />
</p>

<h1>Preparing Active Directory Infrastructure in Azure</h1>
This tutorial outlines how to set up the required infrastructure to use Active Directory within Microsoft Azure.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022


<h2>Setup Domain Controller in Azure</h2>
<p>
<img src="https://github.com/user-attachments/assets/bf1293fb-e49f-4ab1-afcf-a8b590e06b27"/>
</p>
<ol>
  <li>Within Microsoft Azure, create a Domain Controller virtual machine named 'dc-1'. The virtual machine's operating system should be Windows Server 2022. Equip it with an unique Resource Group, Virtual Network, and subnet. </li>
  <li>Set Domain Controller’s NIC Private IP address to be static</li>
  <b> dc-1 → Networking → Network settings → Network interface / IP Configuration → [name] → static </b>
  <li>Log into the VM and disable the Windows Firewall (for testing connectivity)</li>
  <b> task bar search "firewall" → firewall and network protection → private network → off</b>
</ol>
<br />

<h2>Setup Client-1 in Azure</h2>
<p>
<img src="https://github.com/user-attachments/assets/20c05bb2-dd4c-4205-80a7-976a9aa35c23"/>
</p>
<ol>
  <li>Create the Client Virtual Machine(Windows 10) named 'client-1'</li>
  <li>Attach it to the same region and Virtual Network as DC-1</li>
  <li>After VM is created, set Client-1’s DNS settings to DC-1’s Private IP address</li>
  <b>client-1 → Networking → Network settings → Network interface / IP Configuration → DNS Settings → custom</b>
  <li>From the Azure Portal, restart Client-1</li>
  <li>Login to Client-1</li>
  <li>Attempt to ping DC-1’s private IP address. Ensure the ping succeeded</li>
  <li>From Client-1, open PowerShell and run 'ipconfig /all'. The output for the DNS settings should show DC-1’s private IP Address
</li>
</ol>
<br />
