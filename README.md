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

Okay so first, I had to...

