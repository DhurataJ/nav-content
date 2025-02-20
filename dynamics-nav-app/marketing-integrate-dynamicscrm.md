---
title: Manage Customers Using Dynamics 365 for Sales
description: You can use Dynamics 365 for Sales from inside Dynamics NAV to map data and have seamless integration and synchronization in the lead-to-cash process.
documentationcenter: ''
author: edupont04

ms.prod: "dynamics-nav-2018"
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: integration, synchronize, map
ms.date: 06/06/2017
ms.author: edupont
---
# Managing Customers and Sales Created in Dynamics 365 for Sales
If you use Dynamics 365 for Sales for customer engagement, you can use [!INCLUDE[d365fin](includes/d365fin_md.md)] for order processing and finances and have seamless integration in the lead-to-cash process.

When your application is set up to integrate with Dynamics 365 for Sales, you have access to Sales data from [!INCLUDE[d365fin](includes/d365fin_md.md)] and the other way around in some cases. This integration enables you to work with and synchronize data types that are common to both services, such as customers, contacts, and sales information, and keep the data up to date in both locations.  

For example, the sales person in Dynamics 365 for Sales can use the price lists from [!INCLUDE[d365fin](includes/d365fin_md.md)] when they create a sales order. When they add the item to the sales order line in Dynamics 365 for Sales, they are also able to see the inventory level (availability) of the item from [!INCLUDE[d365fin](includes/d365fin_md.md)].

Conversely, order processors in [!INCLUDE[d365fin](includes/d365fin_md.md)] can handle the special characteristics of sales orders transferred automatically or manually from Dynamics 365 for Sales, such as automatically create and post valid sales order lines for items or resources that were entered in Sales as write-in products. For more information, see the "Handling Special Sales Order Data" section.  

> [!NOTE]
> Before you can integrate with Dynamics 365 for Sales, you must make various technical preparations. For more information, see [Setting Up Dynamics 365 for Sales Integration](/dynamics-nav/Setting-Up-Dynamics-CRM-Integration) in the Developer and IT-pro help.

## Setting Up the Connection
From Home, you can access the **Dynamics 365 for Sales Connection Setup** assisted setup guide that helps you set up the connection. Once that is done, you will have a seamless coupling of Dynamics 365 for Sales records with [!INCLUDE[d365fin](includes/d365fin_md.md)] records.  

> [!NOTE]  
> The following explains the assisted setup, but you can perform the same tasks manually in the **Dynamics 365 for Sales Connection Setup** window.

In the assisted setup guide, you can choose which data to synchronize between the two services. You can also specify that you want to import your existing Dynamics 365 for Sales solution. In that case, you must specify an administrative user account.

### Setting Up the User Account for Importing the Solution
To import an existing Dynamics 365 for Sales solution, the setup guide uses an administrative account. This account must be a valid user in Dynamics 365 for Sales with the following security roles:

* System Administrator  
* Solution Customizer  

For more information, see [Create users and assign Microsoft Dynamics NAV (online) security roles](https://technet.microsoft.com/library/jj191623.aspx) on techNet and [How to: Manage Users and Permissions](ui-how-users-permissions.md).  

This account is only used during the setup. Once the solution is imported into [!INCLUDE[d365fin](includes/d365fin_md.md)], the account is no longer needed.

### Setting Up the User Account for Synchronization
The integration relies on a shared user account. So in your Microsoft 365 subscription, you must create a dedicated user that will be used for synchronization between the two services. This account must already be a valid user in Dynamics 365 for Sales, but you do not have to assign security roles to the account because the setup guide will do that for you. You must specify this user account one or more times in the setup guide, depending how much synchronization you want to enable. For more information, see [Create users and assign Microsoft Dynamics NAV (online) security roles](https://technet.microsoft.com/library/jj191623.aspx) on techNet.

If you choose to enable *item availability*, the integration user account must have a web services access key. This is a two-step thing in the [!INCLUDE[d365fin](includes/d365fin_md.md)] page for that user account, you must choose the **Change Web Service Key** button; and in the Dynamics 365 Connection Setup guide, you must specify that user as the OData web service user.

If you choose to enable *sales order integration*, you must specify a user that can handle this synchronization - the integration user or another user account.

### Coupling Records
In the assisted setup guide, you can choose to synchronize between the two services. But later, you can also set up synchronization of specific types of data. This is referred to as *coupling*, and this section provides recommendations for what you must take into consideration.

For example, if you want to see Dynamics 365 for Sales accounts as customers in [!INCLUDE[d365fin](includes/d365fin_md.md)], you must couple the two types of records. It is not very complicated - you open the **Customer List** window in [!INCLUDE[d365fin](includes/d365fin_md.md)], and there is an action in the ribbon to couple this data with Dynamics 365 for Sales. Then you specify which [!INCLUDE[d365fin](includes/d365fin_md.md)] customers match which accounts in Dynamics 365 for Sales.

In certain areas, the functionality relies on you couple certain sets of data before other sets of data as shown in the following list:

* Customers and accounts  
  * Couple salespeople with Dynamics 365 for Sales users first  
* Items and resources  
  * Couple units of measure with Dynamics 365 for Sales unit groups first  
* Items and resource prices  
  * Couple customer price groups with Dynamics 365 for Sales prices first  

> [!NOTE]  
>   If you are using prices in foreign currencies, make sure that you couple currencies to Dynamics 365 for Sales transaction currencies.

Dynamics 365 for Sales sales orders depends on additional information like customers, units of measure, currencies, customer price groups, items and/or resources. In order for Dynamics 365 for Sales sales orders to work seamlessly, you must couple customers, units of measure, currencies, customer price groups, items and/or resources first.

### Synchronizing Records Fully
At the end of the assisted setup guide, you can choose the **Run Full Synchronization** action to start synchronizing all [!INCLUDE[d365fin](includes/d365fin_md.md)] records with all related records in the connected Dynamics 365 for Sales solution. In the **CRM Full Synch. Review** window, you choose the **Start** action. The synchronization then begins to execute jobs according to dependencies. For example, currency records are synchronized before customer records. The full synchronization may take a long time and will therefore run in the background so that you can continue to work in [!INCLUDE[d365fin](includes/d365fin_md.md)].

To check the progress of individual jobs in a full synchronization, drill down on the **Job Queue Entry Status**, **To Int. Table Job Status**, or **From Int. Table Job Status** field in the **CRM Full Synch. Review** window.

From the **Dynamics 365 Connection Setup** window, you can get details about full synchronization at any time. From here, you can also open the **Integration Table Mappings** window to see details about the tables in Dynamics NAV and in the Dynamics 365 for Sales solution that must be synchronized.

## Handling Special Sales Order Data
Sales orders in Dynamics 365 for Sales will be transferred to [!INCLUDE[d365fin](includes/d365fin_md.md)] automatically if you select the **Automatically Create Sales Orders** check box in the **Microsoft Dynamics 365 for Sales Connection Setup** window. On such sales orders, the **Name** field on the original order is transferred and mapped to the **External Document Number** field on the sales order in [!INCLUDE[d365fin](includes/d365fin_md.md)].

This can also work if the original sales order contains write-in products, meaning items or resources that are not registered in either product. In that case, you must fill in the **Write-in Product Type** and **Write-in Product No.** fields in the **Sales & Receivables Setup** window, so that such non-registered product sales are mapped to a specified item/resource number for financial analysis.

If the item description on the original sales order is very long, then an additional sales order line of type Comment is created to hold the full text on the sales order in [!INCLUDE[d365fin](includes/d365fin_md.md)].

## See Also
[Dynamics 365 Business Central](https://docs.microsoft.com/dynamics365/business-central/)  
[Relationship Management](marketing-relationship-management.md)  
[Working with [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)  
[Customizing [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-customizing-overview.md)  
[How to: Manage Users and Permissions](ui-how-users-permissions.md)
