### Enterprise-Style Home Lab: Virtualized Active Directory Environment Using VirtualBox

This project showcases my ability to setup and configure Active Directory within a virtual environment. 

### Environments & Operating Systems Used: 
- Oracle VirtualBox
- Windows Server 2019
- Windows 10

### Technologies Used:
- Powershell
- Remote Desktop 
- Active Directory Domain Services
- DHCP Server

### Configuration & Deployment Steps

- Create the VM that will run Windows Server 2019 and act as the domain controller. Ensure that it has sufficient RAM, Storage and CPU cores allocated. Also, enable two Network Adapters: one for NAT to connect to the outside internet and one for the Internal Network.

![Image](https://github.com/user-attachments/assets/226f682f-d5b8-423a-ae42-a0fb287b44c7)

![Image](https://github.com/user-attachments/assets/f518e118-4374-4671-910f-c06fa3f6fe05)


- Once the VM setup is finished, install the Windows Server 2019 and use the generic admin account to login. Once the desktop is on your screen, open up the "Change Adapter Settings" and rename the Network Cards for clarity throughout the project.

![Image](https://github.com/user-attachments/assets/0e1cdb7a-217b-4902-8c51-f6e85c8e48bb)

![Image](https://github.com/user-attachments/assets/98550071-b277-41ab-88de-d6b1d5aed2b4)


- Next, set up the Internal Network Interface Card IP Address. 

![Image](https://github.com/user-attachments/assets/8b34f32b-0105-4f62-9ec1-bc12b94b23d2)


- Install and Configure Active Directory Services. 

![Image](https://github.com/user-attachments/assets/3ed1280a-22a6-45ce-996b-509fde2c62b0)

![Image](https://github.com/user-attachments/assets/a74a212c-7de8-498e-be00-c8500ec2ec69)

![Image](https://github.com/user-attachments/assets/9613ec2c-4b03-42a4-9ae0-098f0d0a3ffb)


- Do the Post Deployment configuration to create the domain; in this lab it is named mydomain.com.

![Image](https://github.com/user-attachments/assets/e85c0371-b53e-41dd-8faf-9a4877998540)

![Image](https://github.com/user-attachments/assets/ece71b82-aedb-4f42-833c-e41df9e6d9db)


- To start the Custom Admin account creation process, start by creating an Organizational Unit to put the custom Admin Account in. 

![Image](https://github.com/user-attachments/assets/284dbe17-c367-4867-a0c8-9690fe4e3fcb)


- Create a new User; user logon name will be "a-blastname" which is just "a-" for admin, first initial and the lastname of the user.

![Image](https://github.com/user-attachments/assets/e7d7348d-2ef3-4737-9fdb-a4898d6c517a)


- Create a password for the Admin Account and then click finish. 

![Image](https://github.com/user-attachments/assets/325a4621-600e-4ee2-8a72-de9dc35b48d1)

![Image](https://github.com/user-attachments/assets/055e687e-4ad2-4df7-bd2a-d46192021716)


- Add the newly created Admin Account to Domain Admin group. (You can now see that it was successfully added and is a part of the Domain Admin Group).

![Image](https://github.com/user-attachments/assets/974d8c34-3874-421a-ba39-a3b17bb0f281)

![Image](https://github.com/user-attachments/assets/1174e6b8-6769-4a5b-a459-80010986bb38)


- Install Remote Access Server w/ Routing so that the client can access the internet through the domain controller having it act as a VPN.

![Image](https://github.com/user-attachments/assets/5367bbd1-0d84-4d1d-b14d-5e11af544f46)

![Image](https://github.com/user-attachments/assets/8941c66b-34e0-4ec0-80f6-e4d74115d246)


- Configure the Remote Access Server w/ Routing.

![Image](https://github.com/user-attachments/assets/b95688b1-1e1e-4758-92d2-2cdff84fd2de)


- Select the NAT option.

![Image](https://github.com/user-attachments/assets/92029244-fd9b-4b44-a3c0-9bdcc0faa3bd)


- Select the External Network adapter created earlier.

![Image](https://github.com/user-attachments/assets/bf590d2d-658d-469c-8ba6-9c9a14a4481e)


- Remote Access and Routing is now configured.

![Image](https://github.com/user-attachments/assets/2a6f700a-6d40-4acd-8053-21dd70ebbe8d)


- Install the DHCP Server. 

![Image](https://github.com/user-attachments/assets/8b73aba8-1a46-470d-b0e5-80dc15240001)

![Image](https://github.com/user-attachments/assets/2f2e7b63-fe9c-452e-a015-39cc2294ee5e)


- Create a New Scope for IPv4 in the DHCP Server Configuration settings. This will allow the Windows 10 Client machine to lease an IP address so that it will have access to the internet.

![Image](https://github.com/user-attachments/assets/3a4027f0-5722-4c6c-a4e9-754bf6264df5)


- The scope will be named after the IP Range.

![Image](https://github.com/user-attachments/assets/3e387c6c-9a7a-4a1f-bc2e-c8a99c43d0e0)


- Configure the Start and End IP Addresses along with the Subnet Mask. No exclusions for the IP range for now. And leave the lease duration on default for the sake of this lab.

![Image](https://github.com/user-attachments/assets/ff0ee6b8-a74e-4b92-a9eb-bd12e80b9e69)

![Image](https://github.com/user-attachments/assets/951d63de-c516-4738-8972-4d5700014745)

![Image](https://github.com/user-attachments/assets/bdfd3f31-eacd-4fd7-bf81-f74057b0426f)


- Since I configured NAT on the domain controller, the clients are going to use the internal NIC on the domain controller as their default gateway/router.

![Image](https://github.com/user-attachments/assets/6c35ff45-0b23-4477-839b-0191f7ad913d)


- Since installing Active Directory on the Domain Controller, it automatically installed DNS as well. So, I will just use that for the DNS.

![Image](https://github.com/user-attachments/assets/36a75997-f033-4538-9bbd-9acc1a7231b8)


- Activate the scope and finish. 

![Image](https://github.com/user-attachments/assets/286822c0-e1b4-4be1-ad9b-ba954cd722a8)


- DHCP Scope is now active.

![Image](https://github.com/user-attachments/assets/b782da79-9f25-4487-abb1-078c31e13a78)


- Use a PowerShell Script to automatically create 1000 new random Users (all with their own logins).

![Image](https://github.com/user-attachments/assets/852205fc-2463-4f36-918d-674935c412c9)


- Users were created successfully.

![Image](https://github.com/user-attachments/assets/0b9c0c8c-cb98-4298-9097-bb16f2d8f6a8)


- Create VM for the Client.

![Image](https://github.com/user-attachments/assets/11db1200-8dbd-4e07-9131-c30d1aa587da)


- Set up the Network adapter to the Internal Network so that it can get a DHCP address from the Domain Controller to simulate a real-world network setup.

![Image](https://github.com/user-attachments/assets/1d3a1019-d905-452f-9b02-150761b8bd69)


- Run ipconfig to make sure the Client Machine is connected to the Internal NIC.

![Image](https://github.com/user-attachments/assets/7c306172-a750-49e2-89ca-50f4a97244cc)


- Run ping www.google.com to make sure the Client Machine can connect to the external internet.

![Image](https://github.com/user-attachments/assets/ffe6f02c-0190-406a-866c-e089d1660e94)


- Rename the machine to Client1 for this lab and Join the Domain using either the Admin Account login or one of the created User Accounts.

![Image](https://github.com/user-attachments/assets/b9a4f0d9-d519-4160-90f2-b21243e4601e)


- Successful login to the Domain.

![Image](https://github.com/user-attachments/assets/8e3345b9-4d48-4ab6-98d9-aaef96b4e8d2)


- Check the Domain Controller to see the Client Machine connection and it's DHCP Address Lease.

![Image](https://github.com/user-attachments/assets/480c1d2e-08d2-495b-ac57-7454f7066eab)


- Check the Active Directory Users and Computers to ensure the Client Machine is connected.

![Image](https://github.com/user-attachments/assets/d9508c19-5dcc-4042-b295-7db9aa0e7adf)


- Check to make sure the logins are working by going back to the client machine and using one of the user account logins created earlier. I am going to use the account created for myself "blastname" to login to MYDOMAIN.

![Image](https://github.com/user-attachments/assets/84fb25f7-2399-4594-a5a5-4010df273213)


- You are now done, thanks for reading!
