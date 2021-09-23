# Distributed SAP Cloud Integration Scenarios
Artifacts and SAP Community blog reference supporting failover and high availability examples for SAP Cloud Integration (formerly SCP Cloud Platform Integration) using Azure PaaS Services

## 1. Failover with routing-based solution using Azure FrontDoor and API Management and cross-azure-region deployments
Find more details on the SAP community [blog](https://blogs.sap.com/2020/11/23/how-to-crash-your-iflows-and-watch-them-failover-beautifully/) 

The zip file "DRDemo.zip" contains the iFlows used in the blog.

This is useful to avoid the regular SAP CPI maintenance window for instance.

## 2. Failover with DNS-based solution using Azure Traffic Manager
Find more details on the SAP community [blog](https://blogs.sap.com/2021/01/18/second-round-of-crashing-iflows-in-cpi-and-failing-over-with-azure-even-simpler) 

The zip file "FailoverOnboarding.zip" contains the iFlows used in the blog.

## 3. High availability concepts within same BTP and Azure region
Find more details on the SAP community [blog]()

SAP Docs for CPI API runtime setup can be found [here](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/20e26a837a8449c4b8b934b07f71cb76.html). Required APIs to interact with CPI API runtime are described on the [SAP API Business Hub](https://api.sap.com/package/CloudIntegrationAPI?section=Artifacts).

SecretSynchLogicApp.json contains the LogicApp template that integrates with Azure Event Grid. Find more detais on the required config and the Azure portal driven setup flow from your KeyVault on [Azure Docs](https://docs.microsoft.com/en-us/azure/key-vault/general/event-grid-logicapps). In order to use the template as is you need to fill the placeholders marked with "<<<>>>" and pre-provision Event Grid and KeyVault. I might provide a "deploy to Azure" button at a later point in time.

The LogicApp relies on a "secret" naming convention to pull the credentials for the CPI API call. <cpi domain>-usr or -pwd. That eases some of the configuration required and decouples the setting on the LogicApp.

In my example I am running two CPI instances. The first under domain dr-primary and the second under cpi-dr-secondary.

![Secret list](/keyvault-secret-list.png)

The zip file "ShowSharedSecret.zip" contains an iFlow that reads the CPI credential "CPI-AUTH-SHARED" during runtime. I used to verify the approach and correct setup.


Reach out through the GitHub Issues or the comments section on blogs.sap.com.

Cheers
Martin