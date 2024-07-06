# Web-App-Azure-Migration
This is a case study on migrating a book recommendation application to Azure. Cost Management, Resource Creation, Storage Accounts, VMs, Management and Monitoring Tools.

## Project Overview
AppSculpt is a dynamic web application company experiencing rapid growth. As AppSculpt expands into new markets and products while enhancing existing offerings, they have chosen Azure for its scalability and flexibility. The focus is on migrating ReadRadar, a book recommendation application, to Azure to leverage its robust cloud capabilities.

## Project Objectives
- Capturing business requirements, with ReadRadar app's functionality and user needs for book recommendations. Utilizing pricing calculator to forecast costs for transitioning to Azure.
- Azure resources creation with setting up storage account for managing books dataset and deploying a data science virtual machine to support the recommendation model. Ensuring proper resource tagging to facilitate efficient management and cost allocation.
- Security, data integrity and system performance with implementing tag policy enforced compliance, troubleshooting RBAC permissions to address operational errors. Monitoring storage account performance with a metrics workbook and setting up alerts ensured timely response to potential service disruptions.

## Project Methodology - ReadRadar Workflow in Azure

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/a5bc6823-b718-482b-9d3d-eeca7a2a6da8)


### Setting Up Azure, Check for Azure Subscription Status
Make sure Azure is set up correctly and have active subscription. 

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/35d66370-70ea-425e-996b-c6f235f04a9d)

### Cost Management 
AppSculpt aims to expand ReadRadar globally and support multiple languages, along with other data-driven apps. Starting with a basic setup in this case study, future plans involve leveraging Azure extensively. The proposed solution involves Azure Databricks and Azure Machine Learning for advanced analytics, similar to the 'Advanced Analytics on Big Data' scenario in the Pricing Calculator but without Power BI integration.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/4f2f8ae7-7d8f-4d73-8505-82e3fdf6e002)

Go to Cost Management, find Control and optimize costs and open the Pricing Calculator.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/09cd3b02-dc3a-41f5-94df-b8d6f29fc0c5)

In Example scenarios, add the Advanced analytics on big data scenario to the estimate. The instructions received from the data architects have to be adjusted : 

- Remove Power BI embedded, Azure Analysis Services and Azure Synapse.
- Add Azure Databricks and Azure Machine Learning from the Products tab
- Check the final estimate and look up the total cost per month.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/fc964f99-ef3a-492a-9c6b-d11e3b57301d)
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/b8a60d62-ccc6-4bc6-96ab-ee7cb0638a32)
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/82cb163c-7294-467f-96e3-c51e30563312)
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/a9c62d02-5748-4fd1-a64e-85085e464cb9)

The total cost per month is less than 20,000 USD.

### Setting Up Storage Account

A storage account is needed for data ingestion, enabling storage and processing of book data. Necessary data for the recommendation model is collected and stored. These data include for example book metadata, user read history, book reviews, and ratings. The data are cleaned and prepared for the next step. A virtual machine will host and run the recommendation model, providing a secure environment for the data science team to conduct testing and development.

Storage accounts are used to store data in the cloud securely. With storage account, data can be managed and shared for the ReadRadar app in Azure.
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/157b2d79-b591-4b94-be02-a1036f4c3723)

For this project, a text file containing book data which is stored in Azure using Blob storage. It is best suited for cost-efficient storage of text data. 

Extra Note : 
- Blob storage can store vast amounts of unstructured data like images, videos, and text files.
- File storage is the best solution if there is a need for file sharing and collaboration across platforms.
- Table storage is suited for structured data where the data needs to be queried.
- Queue storage is a special type of storage used for cases where requests or tasks need to be managed in sequence, like queuing sales orders. 

Data architect has given specific requirements for creation of the storage account to upload the file with book data :
- All resources should be assigned to a resource group
- Standard performance should be set
- Locally redundant storage is needed
- All resources need to be assigned to the East US Region

### Uploading Dataset
Created a new container and uploaded the csv file (book dataset) to the container.
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/d6999f6c-285a-4ce3-a15a-1cb6168527dc)

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/47d55170-d11b-458d-8526-48919e1353ca)

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/871a11af-684a-47b4-a93b-a5daea288f5a)

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/b3a4821f-750f-4dd1-aa93-c116cbb2d1c5)

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/22633955-121f-4698-b110-c0f4f0f0b161)

### Setting Up Virtual Machine
The virtual machine that needed to be set up is the data science virtual machine (DSVM). Data science team will make use of the DSVM to run and test the recommendation model. In addition, the data architect informed the DSVM needs to comply with specific security and management requirements.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/c6be3c25-edcf-45cc-9eea-5fafaa3f2bdb)

Set the image, as it will change which settings are available. 
The DSVM is not one of the default images. 
Use See all images and find the right one. 

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/c25c3300-8400-4bc4-80ba-6a3bd69cdff2)

Choose the correct size in the resource creation window. Take into account the specifications of the data science team:
-The DSVM version needs to be Windows Server 2022 x64 Gen 1
-Size needs to be DS1 v2 (1 vCPU, 3.5 GiB memory)
-Go to the right tab to change disk size to 128 GiB
-Also make sure disk type is set to standard locally-redundant storage

Configure the virtual machine according to the requirements specified by the data architect:
-Assign the VM to a resource group
-Give the resource a suitable name
-Set the Region to East US

Set the required security settings:
-Set security type to Standard
-Set a username and password combination of your choice
-Go to the right tab to set the public IP setting to 'None'
-Create the VM.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/2190be9e-a176-4f63-bfdc-025005b72077)
The data science team would like to make use of the Auto-shutdown feature during development and testing of the recommendation model. This feature automatically stops the VM when it is not needed (e.g. outside of office hours) to help reduce costs. Can find the Auto-shutdown setting in the Overview screen, in the Properties tab, right column.

## Resources Tracking with Tagging
To keep track of the resources for the ReadRadar project when other projects are also added to Azure, add tags to all resources related to the project. In addition, the DSVM will be managed by the data science team, need to add a tag specifically to the DSVM to identify the data science team as the resource owner.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/6c88f3ca-e49e-4230-aa40-76936e9abacc)

Go to Resource groups.
Select the resource group starting with 'student-' and assign the following tag: "Project":"ReadRadar". 
Go back to Home and navigate to overview screen of the DSVM.
Assign the tag "Team":"Data Science" to the DSVM. 
Navigate to Tags from the Home screen and check to which resources the Project:ReadRadar tag was applied to. 
Do the same for the tag starting with costID.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/8567156d-d78c-4553-8ffd-04dc751228e4)

### Management and Monitoring Tools
Optimizing security and performance for the ReadRadar app by making use of the management and monitoring tools in Azure. Tools in Azure such as role-based access, Policy, and Monitor are used to ensure appropriate security and data protection is in place, and also make sure the app performance is optimized.

### Setting Up Policy 
Azure Policy is the tool for defining and enforcing policies across Azure resources. It is especially useful to ensure adherence to the standards of AppSculpt, ReadRadar's company, and the applicable regulatory requirements. Azure Policy has a different purpose than RBAC. While Azure Policy is used to define rules for resources, RBAC is used to define rules for user roles.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/e4288f3c-ecbd-47c5-acfa-97a651d975aa)
Go to the right service to create policies. Find the policy assignment that requires tags on resource groups.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/9f7d7ad4-b8e1-40da-9db4-25913fd75a2e)
Assign the student- resource group to the scope. Set up the policy parameters to make sure a "project" tag is alway set . Leave all other settings to their default value. Create the policy.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/bc546623-a4b3-4764-9f00-b188c5eee2e4)
Error : Microsoft.Authorization/PolicyAssignments/write 
Don't have the right permission to create policy assignments. Remedy is to look up RBAC permissions.

## RBAC Permission
Weren't able to set up a policy due to a permission error. This is a common problem with RBAC and the principle of least privilege: assigned role and permissions need to be in line with actual role and responsibilities. Best to check assigned role and its associated permissions to make sure consistent with tasks, or if there is need to apply for a new role.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/bf3bb954-3f42-44cf-8083-45d1143b33b4)

Go to the resource group starting with student-. View level of access to the resource. View the list of permissions for the Contributor role.
Search for "policy assignment" and check the list of permissions under Microsoft.Authorization.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/da0bb5e4-125d-4a2c-929d-4aa37403aa35)

Permissions under _Type_ for Microsoft.Authorization_ is contributor and the role does not have the right permissions to set up policies. 
1) Ask admin to set up policies.
2) Have to ask admin to set up the right role, delegate the task to someone with the right role.

### Creating Metrics Workbook
Custom metrics workbook needed to be set up to keep track of its performance, for example how much storage space is used up over time.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/e5c3a7e0-41f0-42b8-ab24-1210004bafbc)

Go to Monitor and open the gallery with workbook templates.
Find and open the Storage accounts Overview template.
Open the workbook for your storage account specifically. If you don't have a storage account anymore, you'll need to recreate it.
Make sure the workbook only shows the data for the Last 24 hours.
Go to editing mode to customize the workbook to only show data for your storage account only instead of any storage account.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/62062b9c-7358-4c7e-8b6d-a855731aa56b)

For example, in the Availability graph, there is no drops or peaks in the last 24 hours.

### Setting Up An Alert for Storage Availability

Metrics workbook helps to report on the performance of the storage account using the metrics workbook, butthere is  also need to be able to remediate issues in a timely manner. This is where alerts come in.

It is important that the storage account maintains high availability, so that it is able to keep processing requests successfully. Therefore, need tp set up an alert to trigger if the average availability of the storage account is lower than 50%.

Go to the right service to create alerts and create a new alert.
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/2fd02257-b39d-46ab-a720-e35963a926c7)

Assign the storage account you created previously to the scope. 
Configure the alert condition to trigger whenever the average availability is less than 50%. 
Leave other settings at their default recommended value.

![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/901a83a6-9e7b-40df-9251-74f7ef8c2ec5)

Look up a list of all created alerts in the Alert rules screen of Monitor. Signal type is one of the columns in that list.
![image](https://github.com/ifhnh/Web-App-Azure-Migration/assets/119716158/3e0796f8-43eb-4190-9da2-d672ec18fe6a)


