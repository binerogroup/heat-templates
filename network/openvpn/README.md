This service sets up a pfSense instance and configures it as an OpenVPN server



Deployment output will be a URL to the pfSense WebUI.
You will be able to log on there using admin / pfsense, after which we suggest you change the administrator password.
From the WebUI, you can download the credentials for OpenVPN access by browsing to VPN->OpenVPN->Client Export and then scrolling down to "OpenVPN Clients" and downloading the appropriate installer/configurations for your OpenVPN client of choice.

Additional client certificates can be created by browsing to System->Cert. Manager->Certificates in the WebUI.
