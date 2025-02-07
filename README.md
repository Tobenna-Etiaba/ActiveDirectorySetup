<p align="center">
<img src="https://i.imgur.com/aMMGyHQ.jpeg" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />

<h1>ActiveDirectory (Part 1 - Setup)</h1>
I will be outlining how I was able to install and deploy Active Directory on a windows server VM through the use of Azure & how I was able to join a windows 10 VM to the server to to make it a client to the server.

<h2>Tools Used</h2>

- Microsoft Azure
- Remote Desktop
- Powershell

<h2>Operating Systems Used</h2>

- Windows 10
- Windows Server 2022

<h2>Step By Step Process</h2>

- I started by creating a Windows server virtual machine in Azure with 2vcpus & 8GB of memory to ensure that the VM ran at a reasonable speed.

<img width="621" alt="Screenshot 2025-02-07 at 12 43 56" src="https://github.com/user-attachments/assets/20b1f8aa-c2fc-4ea8-81ff-eda4c9a18adc" />

<img width="803" alt="Screenshot 2025-02-07 at 12 45 23" src="https://github.com/user-attachments/assets/c3ac30ee-8433-4930-8022-df7ce6f8fe67" />

- After creating the VM I set the private IP address to be static so that it doesn't change if the VM were to restart.

<img width="1413" alt="Screenshot 2025-02-07 at 12 50 17" src="https://github.com/user-attachments/assets/368698ff-693c-420d-9f29-2507062cb6e9" />

<img width="874" alt="Screenshot 2025-02-07 at 12 50 47" src="https://github.com/user-attachments/assets/3c8c8786-f9aa-4ba8-bdc9-51ca6b037c85" />

<img width="585" alt="Screenshot 2025-02-07 at 12 51 09" src="https://github.com/user-attachments/assets/4d5a5478-5a6f-42d7-99c0-bdebb6185788" />

- Once that was done I took the public IP address and used it to log into the VM via remote desktop and named the VM "Server".

<img width="1148" alt="Screenshot 2025-02-07 at 12 54 13" src="https://github.com/user-attachments/assets/54ecf6cb-fcea-4b13-9c6a-105c032034b7" />

- After logging in I proceeded to disable windows firewall in order to test connectivity.

<img width="436" alt="Screenshot 2025-02-07 at 12 55 12" src="https://github.com/user-attachments/assets/b089a383-edf6-4677-8baf-eea7f03df69b" />

<img width="1046" alt="Screenshot 2025-02-07 at 12 55 27" src="https://github.com/user-attachments/assets/a53c7cf6-5e49-45e1-b291-9bede5ed9b65" />

<img width="398" alt="Screenshot 2025-02-07 at 12 56 53" src="https://github.com/user-attachments/assets/bea22a36-97c8-4f50-aeb4-40886bc8410e" />

<img width="401" alt="Screenshot 2025-02-07 at 12 57 02" src="https://github.com/user-attachments/assets/3bc88866-45d7-42b2-bc6d-c4ff010524da" />

<img width="397" alt="Screenshot 2025-02-07 at 12 57 11" src="https://github.com/user-attachments/assets/bcbe0593-fc4f-482e-9aea-6682f0eeda98" />

- Following up from here I proceeded to create a new VM within the same resource group and virtual network, but for windows 10 this time.

<img width="466" alt="Screenshot 2025-02-07 at 12 57 43" src="https://github.com/user-attachments/assets/54a39e46-4aac-45ed-9745-0c8fe07daffe" />

<img width="808" alt="Screenshot 2025-02-07 at 12 58 13" src="https://github.com/user-attachments/assets/ae43074a-d403-467c-8298-b2737fe8e4cb" />

- After the VM was created I then proceeded to set the windows 10 VMs DNS settings to the windows servers private IP address.

<img width="1412" alt="Screenshot 2025-02-07 at 13 03 22" src="https://github.com/user-attachments/assets/5c0166a4-f2fa-4584-84a3-a95801474627" />

<img width="723" alt="Screenshot 2025-02-07 at 13 03 49" src="https://github.com/user-attachments/assets/38634e1a-87f6-4ca0-9788-9be150b069f8" />

- From within Azure I restarted the windows 10 VM.

<img width="708" alt="Screenshot 2025-02-07 at 13 04 41" src="https://github.com/user-attachments/assets/0b0a728c-37f0-44ff-ae11-a89e3eb2071a" />

- I proceeded to take the public IP address of the windows 10 vm and used it to login the VM via remote desktop and named the VM "User".

<img width="1148" alt="Screenshot 2025-02-07 at 13 06 22" src="https://github.com/user-attachments/assets/c1fae4fd-44f3-4e61-8bea-40ebcb41acb6" />

- Once I logged in I attempted to ping the windows servers private IP address, and once the ping had succeeded I then ran the command *ipconfig /all* within powershell to ensure that the output for the DNS settings matched the windows servers private IP address.

<img width="856" alt="Screenshot 2025-02-07 at 13 09 23" src="https://github.com/user-attachments/assets/9ffa8972-a687-46d6-98a1-1bc5d3b671c9" />


