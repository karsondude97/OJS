# OJS

**_Okta-Jamf Sync_**

The intent of OJS is to automatically update static Jamf Computer or Mobile groups whenever a user is added to an Okta group. The most common use case scenario would be; if you have an application in Okta with group access associated to it, you could use this to scope that software to the group of devices with Jamf.

## Prerequisites

Follow Okta's steps [here](https://help.okta.com/wf/en-us/content/topics/workflows/learn/about-workflowsconsole.htm) to access the Workflows console.

### Add the [Jamf Pro Classic API Connector](https://help.okta.com/wf/en-us/content/topics/workflows/connector-reference/jamf/jamf.htm)
_Pulled from Okta's documentation._

#### Before you Begin:
Make sure that your Jamf Pro Classic API account has the following settings:

- **Type**: Standard User
- **Access Level**: Full Access
- **Privileges**: Administrator

Make sure that your Jamf Pro Classic API account has access to the */JSSResource/activationcode* endpoint.

#### Create a Jamf Pro Classic API connection

To set up a new connection in Jamf Pro Classic API:

1. Click **New Connection**.
2. Enter a connection **Name**. This is useful if you plan to create multiple connections to share with your team.
3. Optional. Enter a **Description** for the connection with any extra information about your connection.
4. In the **Username** field, enter your username.
5. In the **Password** field, enter your password.
6. In the **Full Instance URL** field, enter the URL. For example, *https://instance.jamfcloud.com*.
7. Click **Create** to launch a pop-up window where you can sign into your Jamf Pro Classic API account. This action also saves your connection.

## [Create Static Jamf Computer and/or Mobile Device Groups](https://learn.jamf.com/en-US/bundle/jamf-pro-documentation-current/page/Static_Groups.html#:~:text=Creating%20a%20Static%20Group,Click%20New.)
I recommend naming this something obvious like, Okta_*usage*. For example if you are creating a group to scope office apps to those who have access to **Microsoft Office** apps in Okta, you could name it *Okta\_Office*

Once created, note the group ID for later. You can get the ID from the URL.

Example: 

- *https://yourinstance.jamfcloud.com/staticComputerGroups.html?id=69&o=r*

Would have an ID of *69*<!-- nice -->.

## Download, Import, and Setup the Workflow Template

Download the Workflow template from the main branch [here](insert URL here)

### Import the flow into your workflows console
*Pulled from Okta's Documentation (Edited Slightly).*

The imported flows appear as new flows. They don't preserve any application connections, so you need to reconnect the Jamf Pro Classic API in the **Jamf\_ComputerGroup\_Add** *and* **Jamf\_ComputerGroup\_Remove** and/or the **Jamf\_MobileDeviceGroup\_Add** *and* **Jamf\_MobileDeviceGroup\_Remove** helper flows.

To import an Okta Workflows.folder file, complete the following steps:

1. In the Workflows Console, select the folder where you want to place the imported flows.
2. In the **Actions** dropdown menu, click **Import**.
3. Drag and drop your file into the dialog, or click the link to browse your local file system for the file.

Okta imports the content to the current folder, unless the import action would exceed the maximum folder depth of five levels. In this scenario, Okta provides the option to import the contents as a top-level folder instead.

