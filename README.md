# Proxmox

## Objective

Proxmox is an open-source virtualization platform that combines KVM (Kernel-based Virtual Machine) and LXC (Linux Containers) to provide a comprehensive solution for managing virtual environments. It is a powerful tool for running multiple virtual machines and containers on a single physical server. Proxmox allows users to manage virtual machines, storage, networking, and clusters through an easy-to-use web-based interface. It also supports high availability, backups, and scaling, making it suitable for both small businesses and large enterprise environments.

### Skills Learned

Virtualization Management – I learned how to create and manage virtual machines and containers, which are essential for handling virtualized environments in real-world scenarios.

Linux System Administration – I gained hands-on experience with Linux, which improved my ability to work with Linux-based systems and perform administrative tasks in IT environments.

Networking Configuration – I developed skills in configuring networking for virtual machines, including setting up bridges, VLANs, and storage networking, which are critical for managing networked infrastructure.

Backup & Disaster Recovery – I became knowledgeable in managing VM backups, snapshots, and disaster recovery processes, ensuring data integrity and availability in case of failures.

Cloud Infrastructure Setup – I gained knowledge in setting up and managing cloud-like infrastructure using Proxmox’s clustering features, which enhanced my understanding of how to scale and manage virtualized resources in cloud environments.



#Steps Taken

First, I had to navigate to the Proxmox website located here < https://www.proxmox.com/en/downloads/proxmox-virtual-environment > 

![image](https://github.com/user-attachments/assets/7ee6029a-9a5c-4a1b-89ed-e8fb051c93e6)


Once I downloaded the image, I verified the hash to make sure they matched. 

![image](https://github.com/user-attachments/assets/770c2039-6720-4230-97b5-0a28898731b9)


Next, I took the .iso image and went to Rufus to create a bootable drive. 

![image](https://github.com/user-attachments/assets/9a98036f-2682-413f-823d-39394f990b86)



Once the drive was complete, I plugged this into my Dell server and booted to the drive. 

![image](https://github.com/user-attachments/assets/ad2e67e2-f856-485d-bd1e-e5fae825608e)


Once I booted and set everything up, I was finally met with a page the informed me on where to navigate to via my web browser and this is what the main dashboard looks like. 

![image](https://github.com/user-attachments/assets/271d3090-3114-41a4-8f17-a0c88ebbaab2)


From here, you will be advised that this Proxmox does not have a valid license. I went ahead and purchased one because I want security and patches applied to my server from Proxmox. Well worth it. Here is the Proxmox store to buy a license <https://shop.proxmox.com/index.php?rp=/store/proxmox-ve-community> & here is the link on how to apply the license to your Proxmox server <https://shop.proxmox.com/index.php?rp=/knowledgebase/4/How-do-I-upload-my-Proxmox-VE-subscription-key-to-my-Proxmox-VE-host.html> 


Once I purchased a valid license from Proxmox, its time to setup some VM's. In this case, I want to setup a Windows server 2022, but first, we need to set some actions up. Before I go on, just wanted to give credit to this channel as this helped me set everything up < https://www.youtube.com/watch?v=JrIDEH9jsPg&t=426s > 

Okay so first, I had to upload the Windows server 2022 ISO image to Proxmox. I got the ISO image from here < https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022 >

![image](https://github.com/user-attachments/assets/4e6f8ed4-8a82-417c-9229-8415ed522b8f)

Once you upload your ISO file, then you need to click on the "Download from URL" button at the top of the page. The link to the page is this < https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers > 

Once you navigate to the page, scroll down until you find the link to download the VirtIO files 

![image](https://github.com/user-attachments/assets/b73ac828-afe2-4790-80a2-6a76694505bf)

Copy that link and paste it back into the Download from URL in Proxmox. 

Once both images have been downloaded, you should see both iso's in there now 

![image](https://github.com/user-attachments/assets/8f13415a-1724-4742-bd58-9824f1ddd65a)


Next, create a VM. 

![image](https://github.com/user-attachments/assets/19ffcffe-5d3b-435e-baee-cc1c17c70707)

Copy what I have in the next few slides. My goal is to create a domain controller and have some space for any future updates or add-ins I want to add to it. 

Give your VM a name and ID. Also make sure to have "start at boot" checked. 

![image](https://github.com/user-attachments/assets/ee84badf-0161-43b7-b67e-2c738eb39717)


Make sure to select your ISO, then change the type to Windows and make sure to have the correct version as well 

![image](https://github.com/user-attachments/assets/f94ab794-2ba5-45af-aefc-3d3a3b5e50fa)

Next, change the storage to your storage you will have Proxmox on. I did RAID 5 for mine, so its all shared. Also select the TPM storage as well for the same location and change the SCSI controller to VirtIT SCSI 

![image](https://github.com/user-attachments/assets/07fc5633-99fa-40ec-a3e6-65cbb62578a8)

Next, give the VM an appropriate amount of space that you wish to have. Keep in mind for Windows updates and also change the Bus/Devcie to SCSI 

![image](https://github.com/user-attachments/assets/58238fa1-fc36-4c85-a253-296d69e08b7b)

Next, give the VM enough CPU power to work properly. I also changed teh Type to host to be the same as my physical server. 

![image](https://github.com/user-attachments/assets/30e15405-72bf-4154-a0ec-80fdc4c50fa4)

Next, give the amount of RAM you want. I did Max 8GB and min 4GB for mine. 

![image](https://github.com/user-attachments/assets/9aeef070-1db0-4a9a-8fe3-2c506c41f88a)

Make sure your Network bridge is set to what you wish. 

![image](https://github.com/user-attachments/assets/8ec883b5-663f-4a53-af5e-1fe0f582f4f6)

Now, review all your work you have done and make sure its correct. If so, then just click on finish. 

![image](https://github.com/user-attachments/assets/967c55e6-e9aa-4706-92c0-952a283bc72e)

Next, go to the VM you just created, navigate to hardware, then add, then CD/DVD drive 

![image](https://github.com/user-attachments/assets/dc781c6c-7655-409a-b349-c466fc19b67c)

Once you are here, add your VirtIO iso and select your location 

![image](https://github.com/user-attachments/assets/a3615402-64c1-4f58-99b7-efff8ee78efc)

Once you have added the VirtIO image, we can now start the VM. Click on Start at the top right and then go to console. If you failed to be fast enough to click in the screen, no worries. Just restart the VM and try again. 

![image](https://github.com/user-attachments/assets/d8732684-7293-4839-9732-055e983ce494)

Now once you past the inital few click setup for the Windows server, click on which ever version you want. I want the GUI so I will select the Desktop experience version. 

![image](https://github.com/user-attachments/assets/936c4912-631a-4ccd-84ad-929bd5f3a5f4)

Keep moving forward and you will then need to select where to install the OS on. Click on Load driver 

![image](https://github.com/user-attachments/assets/2e86e429-d49d-46fa-b56a-64f925637932)

Then click on Browse

![image](https://github.com/user-attachments/assets/54da909a-6310-4ffd-a429-02ecad895a12)

From here, navigate to the VirtIO CD, scroll down until you find VIOSCSI, then click on the version you have, since I am installing a windows server 2022, I will select the 2k22, then after that select the amd64 and click ok. 

![image](https://github.com/user-attachments/assets/0fd3504a-ba68-4a37-9e3a-b08689124477)

Then click Next to install the driver 

![image](https://github.com/user-attachments/assets/b4936edd-390d-4217-8cb0-d5dae3d55439)

Then click on Next again 

![image](https://github.com/user-attachments/assets/191b5e75-6b9e-4a18-8d54-050aed4fcde0)

Now the OS will be installed 

![image](https://github.com/user-attachments/assets/f2cb1c60-aa91-48b8-b368-1548ce9934cc)

Next, create a password for your admin account 

![image](https://github.com/user-attachments/assets/90c2a701-4404-47e2-87e6-55271ae324a1)

Click on Finish and you will now be taken to the main OS display 

![image](https://github.com/user-attachments/assets/f7300339-7311-43a3-9cc1-be25eddd999c)

From here, check the drivers to make sure everything installed correctly. 

![image](https://github.com/user-attachments/assets/b717e9a2-5583-4fbb-9dd9-d162b66160a6)


From here, right click and hit update driver and hit browser my computer for drivers 

![image](https://github.com/user-attachments/assets/772336fa-a76c-4717-8c29-f47225ac33f1)

Then click on browser again, select the virtio drive and click on OK. Then click next to scan for missing drivers. 

![image](https://github.com/user-attachments/assets/42f9da75-e990-46f7-b8ce-cb90a723a6d5)


Once done, everything should have been installed. 

![image](https://github.com/user-attachments/assets/4e6d5dd8-9029-4e65-9de7-83cf72c64b72)

Sometimes this does not fully install so the backup option is to navigate to the virtio drive > Ballon > 2k22 > amd64 then copy all the contents inside the folder 

![image](https://github.com/user-attachments/assets/1acdc834-f9bb-4592-b928-4e4fc6c04099)

Once you copy the contents, navigate to your C drive and create a folder called Ballon then paste the contents inside that folder. 

![image](https://github.com/user-attachments/assets/26a0dafd-984a-483c-bdfc-aa348324adf0)


Open CMD in the directory you are in and type in blnsvr.exe -i 

![image](https://github.com/user-attachments/assets/8f285cc6-7877-4ecd-9ef2-5d0762188d17)

Now that everything is checked, lets run a windows update to make sure everything is updated. 

![image](https://github.com/user-attachments/assets/97ac6522-8204-42bb-8a2d-331fa71e6ee5)

Thats it! We have successfully created a Windows server 2022 VM in Proxmox.
