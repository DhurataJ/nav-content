---
    title: How to Replan or Refresh Production Orders Directly
    description: The production order lines contain the items that are to be produced in the production order.

    documentationcenter: ''
    author: SorenGP

    ms.prod: "dynamics-nav-2018"
    ms.topic: article
    ms.devlang: na
    ms.tgt_pltfrm: na
    ms.workload: na
    ms.search.keywords:
    ms.date: 09/06/2017
    ms.author: edupont

---
# How to: Replan or Refresh Production Orders Directly
The **Replan** function on production orders is typically used after you have added or changed components that constitute underlying production orders. The function calculates changes made to components and routings lines, and it includes items on lower production BOM levels for which it may generate new production orders.  

Based on the changes you have made to the components and routing lines, the Replan function calculates and plans for any new demand for the production order.  

The **Refresh** function on production orders is typically used after you have done one of the following:

- Created a production order header manually to calculate and create line data for the first time.
- Made changes to the production order header to recalculate all the line data.

The Refresh function calculates changes made to a production order header and does not involve production BOM levels. The function calculates and initiates the values of the component lines and routing lines based on the master data defined in the assigned production BOM and routing, according to the order quantity and due date on the production order’s header.

You can either insert the production order lines manually or use the function that calculates the production order lines from the header.  

> [!NOTE]
>  If you use the Refresh function to recalculate production order lines, the old production order lines are deleted and new lines are calculated.  

## To replan a production order  
1.  Choose the ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon") icon, enter **Firm Planned Prod. Orders**, and then choose the related link.  
2.  Open the production order you want to replan.  
3.  On the **Lines** FastTab, choose the **Lines** action, and then choose the **Components** action.  
4.  Add a component, which is a produced item or subassembly.  
5.  From the production order, choose the **Replan** action.  

    In the **Replan Production Order** window, proceed to define how and what to replan.  
6.  In the **Scheduling Direction** field, select one of the following options.  

    |Option|Description|  
    |----------------------------------|---------------------------------------|  
    |**Back**|Calculates the operation sequence backwards from the earliest possible ending date, defined by due date and/or other scheduled orders, to the latest possible starting date. **Note:**  This default option is relevant in the majority of situations.|  
    |**Forward**|Calculates the operation sequence forward from the earliest latest possible starting date, defined by due date and/or other scheduled orders, to the earliest possible ending date. **Note:**  This option is only relevant for expedite orders.|  

7.  In the **Plan** field, select whether to calculate production requirements for produced items on the production BOM, as follows.  

    |Option|Description|  
    |----------------------------------|---------------------------------------|  
    |**No Levels**|Do not consider lower level production. This only updates the item’s schedule, like refresh.|  
    |**One Level**|Plan for first-level production demand. First-level production orders may be created.|  
    |**All Levels**|Plan for all-level production demand. All-level production orders may be created.|  

8.  Select **One Level**, and choose the **OK** button to replan the production order, and calculate and create a new underlying production order for the introduced subassembly, if it is not fully available.  

> [!NOTE]  
>  Changes implemented with the **Replan** function are very likely to change the capacity need of the production order and you may therefore have to reschedule operations afterwards.  

## To refresh a production order  
If you have amended production order lines, components, or routing lines, you must also refresh the information on the production order. In the following procedure, the components are calculated for a firm planned production order. The steps are similar for routing lines.

1. Choose the ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon") icon, enter **Firm Planned Prod. Order**, and then choose the related link.  
2. Choose the **New** action. For more information, see [How to: Create Production orders](production-how-to-create-production-orders.md).  
3. Choose the **Refresh** action.
4. In the **Refresh Production Order** window, select one of the following options:


   |          Option          |        Description         |
   |--------------------------|----------------------------|
   | **Scheduling Direction** |        **Forward**         |
   |                          |        **Backward**        |
   |      **Calculate**       |         **Lines**          |
   |                          |        **Routings**        |
   |                          |     **Component Need**     |
   |      **Warehouse**       | **Create Inbound Request** |


5. Choose the **OK** button to confirm your selection. Now the production order lines are calculated.

> [!NOTE]  
>  Calculating production order components deletes previous changes in the components.

## See Also
[Dynamics 365 Business Central](https://docs.microsoft.com/dynamics365/business-central/)  
[Planning](production-planning.md)  
[Setting Up Manufacturing](production-configure-production-processes.md)  
[Manufacturing](production-manage-manufacturing.md)    
[Inventory](inventory-manage-inventory.md)  
[Purchasing](purchasing-manage-purchasing.md)  
[Design Details: Supply Planning](design-details-supply-planning.md)   
[Setup Best Practices: Supply Planning](setup-best-practices-supply-planning.md)  
[Working with [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)
