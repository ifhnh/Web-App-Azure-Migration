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

## Cost Management 
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

The total cost per month is less than 20,000 USD.

## Storage Accounts and Virtual Machines
