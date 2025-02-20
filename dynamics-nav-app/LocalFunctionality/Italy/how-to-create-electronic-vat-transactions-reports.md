---
    title: How to Create Electronic VAT Transactions Reports
    description: You must create a list of transactions that include VAT with amounts over the current threshold on or before the specified occurrence date. You submit this report to the tax authorities.

    documentationcenter: ''
    author: SorenGP

    ms.prod: "dynamics-nav-2018"
    ms.topic: article
    ms.devlang: na
    ms.tgt_pltfrm: na
    ms.workload: na
    ms.search.keywords:
    ms.date: 07/01/2017
    ms.author: edupont

---
# How to: Create Electronic VAT Transactions Reports
You must create a list of transactions that include VAT with amounts over the current threshold on or before the specified occurrence date. You submit this report to the tax authorities.  

## To create a VAT transactions report  

1.  Choose the ![Search for Page or Report](../../media/ui-search/search_small.png "Search for Page or Report icon") icon, enter **VAT Report**, and then choose the related link.  
2.  Fill in the fields as described in the following table.  

    |Field|Description|  
    |-------------------------------------|---------------------------------------|  
    |**Without Contract**|The VAT entries that resulted in this line are not associated with a contract.|  
    |**Contract**|The VAT entries that resulted in this line are associated with a contract.|  
    |**Other**|The VAT entries that resulted in this line are not associated with a special contract, such as ongoing maintenance or other exceptions.|  

    > [!TIP]  
    >  In [!INCLUDE[navnow](../../includes/navnow_md.md)], the contract that the tax authorities are looking for can be blanket orders or service contracts. To identify if the VAT report line belongs to a blanket order or service contract, you can drill down to see the underlying VAT entries from the **Amount** field.  

Credit memos are included in the VAT transaction report if the customer or vendor is from a country/region that is outside the EU. For more information, see [Italian VAT](italian-vat.md).  

Now that you have created the VAT report, you must submit it to the tax authorities. For more information, see [How to: Export VAT Transactions Reports](how-to-export-vat-transactions-reports.md).  

## See Also
[Dynamics 365 Business Central](/dynamics365/business-central/)  
[Italian VAT](italian-vat.md)
