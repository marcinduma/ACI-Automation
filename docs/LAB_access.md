# Connectivity Check


## 1. Lab access general description

The lab is based on dCloud session *Started with Cisco ACI 5.2 v1*:

You will have access to Cisco dCloud User Interface, where you will be able to login to necessary resources. Each dCloud session contain Windows Workstation, Centos server tool and ACI Simulator. You will work on your dedicated session - details will be provided by instructor.
During the training you will use only dCloud resources, no need to install additional applications at your PC.

## 2. Cisco dCloud dashboard

The entire lab for the session is built using Cisco dCloud environment.
Access to the Session will be provided by the proctor assigned to you.

You will get credentials for your individual session provided by teacher.

### Access session with webRDP

Once logged to the dCloud session, you will see dashboard like on the following picture:


<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/master/images/dCloud-dashboard.PNG" width = 800>

To open WebRDP follow the procedure from the figures:

1) Click on the blue triangle highlighted on figure below

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/master/images/dCloud-rdp-1.PNG" width = 800>

2) Follow to "Remote Desktop" by using link in red frame on the figure:

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/master/images/dCloud-rdp-2.PNG" width = 800>


When you click on "Remote Desktop button, browser will open new TAB with access to Windows desktop. The webRDP has installed Chrome as web browser, from where you get access to Cisco Intersight page.
To access CSR router and Linux jumphost, use Putty installed - shortcut is on Desktop.

!!! info
	Please do not use "Remote Desktop" for other devices from the list at **Network** tab. ONLY win2k16 can be accessed that way.

!!! tip
	When you use webRDP you are still able to copy/paste between your 'main PC' and webRDP interface. You can use Guacamole interface - explained in Appendix: Guacamole.


## 3. Accessing Linux Jumphost

Open PuTTY client on webRDP taskbar.

PuTTY has pre-defined session to CSR router as well as to ubuntu-terminal. Use predefined ubuntu-terminal session by selecting it and click Open button.

Username:
	
	dcloud

User password:
	
	C1sco12345



## 4. Accessing vCenter for Lab

Whole setup is done on ESXi in Cisco dCloud environment. During the lab you don't need to perform actions on vCenter itself. However for case of troubleshooting or exploration, credentials to your vCenter below.

URL:
	
	https://vc1.dcloud.cisco.com/ui
User name:
	
	administrator@vsphere.local
User password:
	
	C1sco12345!


!!! warning
	Do not delete configuration nor VM machines already existing on the vCenter.

