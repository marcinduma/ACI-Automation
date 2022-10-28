# Cisco ACI rest API

In this lab section you will create and execute list of API calls to configure ACI managed objects as well as read data from existing polices and devices. After this section you will feel comfortable with runing simple automation tasks and build your own tasks for further customizations. You will be familiar with Postman dashboard and general idea of runing request individualy or as a collection defined. 

## 1 Define restAPI calls under Collection

Now is a time to work with our requests to GET or POST restAPI. You will define couple of them during the LAB. Figure below shows where to navigate to create new request in your collection.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-request-1.PNG" width = 800>

Every API command have predefined structure. Administrator needs to specify URI for correct object are you going to work with. Everything is described in details under the following link:
[Cisco ACI API Configuration guide](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/2-x/rest_cfg/2_1_x/b_Cisco_APIC_REST_API_Configuration_Guide/b_Cisco_APIC_REST_API_Configuration_Guide_chapter_01.html){target=_blank}.

The figure below shows structure of every API call:

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/349945.png" width = 800>



### 1.1 Create ACI login request

First request when working with ACI must be authentication. Without having your session authenticated, no API calls can be successfully executed. Information about Authentication request structure can be found here:

[Cisco ACI Authentication API](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/2-x/rest_cfg/2_1_x/b_Cisco_APIC_REST_API_Configuration_Guide/b_Cisco_APIC_REST_API_Configuration_Guide_chapter_01.html#concept_D16AC6DC9CCD4351A4A40287487F061A){target=_blank}.

Define it in Postman:

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-aaalogin-1.png" width = 800>

In New Request section specify:

1) Name of Request

		ACI Login

2) Select Method to be **POST**

3) Enter request URL

		https://{{apic}}/api/aaaLogin.json

4) Move to **Body** section for further work with your request


Once you open Body section, you need to select type of data to be **RAW** and coding to **json**.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-aaalogin-2.png" width = 800>

Now you can copy code defined below to body section of your request.

```json title="aaaLogin" hl_lines="4 5"
{
  "aaaUser" : {
    "attributes" : {
      "name" : "{{user}}",
      "pwd" : "{{password}}"
    }
  }
}
```
**==Yellow==** highlighted text in the json code above will use variables you defined in **Environment** at the beginning of the Lab.

Now your Request should looks like on the figure below.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-aaalogin-3.png" width = 800>

<span style="color:blue">**It's time to TEST it!**</span>.


<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-aaalogin-4.png" width = 800>

Click on **Send** button. Make sure your environment **ACI-dcloud** is selected - above the Send button.

When works as expected you will be authenticated to APIC. Responce from the APIC is visible in the section at your screen.
Let's go together across results you see on the screen. First is a Status ** 200 OK ** - means APIC server accepted your request, execute it and responce with data. In the REPLY Body you see JSON structure data. You can see **token** which is your authentication token. **RefreshTimeoutSeconds** set to 600 seconds = 10 minutes. Token is valid for 10 minutes and after that period will expire.

Please scroll down across the response body yourself.  Look for such information:

- userName
- sessionId
- aaaWriteRoles

Write them down to notepad.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-aaalogin-5.png" width = 800>

### 1.2 Get Information About a Node

POST is not only one request type. You can configure your ACI fabric, but you can use restAPI to pull data you are interest to analyse. This excercise is about writing a **GET** Request under already created ACI collection. As an example you will pull information about Leaf node-101 system in *json*.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/postman-get-node101-1.PNG" width = 800>

Name your new Request

		Node-101-topsystem check
		
Copy the URI to GET request:

		https://{{apic}}/api/mo/topology/pod-1/node-101/sys.json


Save new Request and Click **Send** .

!!! Note
	It may happen that your API Token expired - remember its valid only 10 minutes. If you experience it, go to *ACI Login* Request and Send it again to re-authenticate.
	


In te Body responce you can verify topsystem information about Leaf in your Fabric.
You can pull data about AccessPolices, Interfaces as well as Logical construct - Tenant, EPGs, VRFs etc. The idea is always same - specify correct URL. Another test will be quering information about APIC node and current firmware version running on it.


Please Create another Request under your Collection with following setup:

Name of Request:

		Get Running Firmware
		
GET request URI:

		https://{{apic}}/api/mo/topology/pod-1/node-1/sys/ctrlrfwstatuscont.json?query-target=subtree&target-subtree-class=firmwareCtrlrRunning

Please observe that current query is composed with parameters. Before we pulled data directly from top-system of our ACI Leaf. Now you are narrowing the output to only sub-class you are intrested about.
Try to delete part of URI ==**?query-target=subtree&target-subtree-class=firmwareCtrlrRunning**== and do Send again.



## 2 Create ACI Access Polices

1 tutaj potrzebujemy stworzyc request ktory zrobi nam cala strukture VLAN-pool, VLAN-range, Domain, AAEP.
2 Drugi bedzie o Interface PRofile, Leaf-profile, interface-selector, Switch-profile i przypięciu leaf-profilu pod konkretny box.

## 3 Create ACI Tenant

1 stworzenie tenantu, VRF, BD
2 stworzenie EPG, przypisanie domeny i dodanie kilku static-bindingow

## 4 Read Data

1 uzycie VLANpoolu? ktore VLANy są uzywane z pooli?
2 ktore interfejsy sa wolne?
3 cos jeszcze?