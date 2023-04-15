Deploys nfs-kernel-server or samba or both on ubuntu instance


This template will deploy one ubuntu instance that will have samba-server or NFS-kernel-server or both installed on it.

You will be able to choose the desired amount of disk that can easily be extended in the future.
This disk space will be accessible over samba protocol which windows mainly uses, or NFS protocol that linux mainly uses.

There will be no password or user requirements to access these shares,  the shared storage will be accessible on your local network and not open publicly to the internet.

If you wish to add external IP to the server we do recommend you lock down the security groups for nfs and samba so only the desired IP addresses can reach the shared space.

The output of deployment will be:
1. samba mount instruction
2. nfs mount instruction
3. Ubuntu User Password - To login to the server
