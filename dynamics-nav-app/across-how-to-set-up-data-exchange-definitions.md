---
    title: Define how data is exchanged electronically
    description: You can use an external provider of OCR services to have PDF or image files turned into electronic documents.
    author: SorenGP

    ms.prod: "dynamics-nav-2018"
    ms.topic: article
    ms.devlang: na
    ms.tgt_pltfrm: na
    ms.workload: na
    ms.search.keywords:
    ms.date: 08/21/2017
    ms.author: edupont

---
# How to: Set Up Data Exchange Definitions
You can set up [!INCLUDE[d365fin](includes/d365fin_md.md)] to exchange data in specific tables with data on external files, for example to send and receive electronic documents, import and export bank data or other data, such as payroll, currency exchange rates, and item catalogues. For more information, see [Exchanging Data Electronically](across-data-exchange.md).  

As preparation for creating a data exchange definition for a data file or stream, you can use the related XML schema to define which data elements to include on the **Column Definitions** FastTab. See step 6 in the “To describe the formatting of lines and columns in the file” section. For more information, see the [How to: Use XML Schemas to Prepare Data Exchange Definitions](across-how-to-use-xml-schemas-to-prepare-data-exchange-definitions.md).  

You normally set up data exchange definitions in the **Data Exchange Definition** window. However, when you set up a data exchange definition for the service of refreshing currency exchange rates, you start the process in the simplified **Exch. Rate Update Setup Card** window.  

> [!NOTE]  
>  If the file that is being converted is in XML format, the term *“column”* in this topic should be interpreted as *“XML element containing data”*.  

This topic includes the following procedures:  

* To create a data exchange definition  
* To export a data exchange definition as an XML file for use by others  
* To import an XML file for an existing data exchange definition  

## To create a data exchange definition  
Creating a data exchange definition involves two tasks:  

1. In the **Data Exchange Definition** window, describe the formatting of lines and columns in the file.  
2. In the **Data Exchange Mapping** window, map columns in the data file to fields in [!INCLUDE[d365fin](includes/d365fin_md.md)].  

     This is described in the following procedures.  

#### To describe the formatting of lines and columns in the file  
1. In the **Search** box, enter **Data Exchange Definitions**, and then choose the related link.  
2. Choose the **New** action.  
3. On the **General** FastTab, describe the data exchange definition and the data file type by filling the fields as described in the following table.  


   |              Field              |                                                                                                                                                                                                                                                               Definition                                                                                                                                                                                                                                                                |
   |---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **Code**             |                                                                                                                                                                                                                                         Enter a code to identify the data exchange definition.                                                                                                                                                                                                                                          |
   |            **Name**             |                                                                                                                                                                                                                                             Enter a name for the data exchange definition.                                                                                                                                                                                                                                              |
   |          **File Type**          | Specify what type of file that the data exchange definition is used for. You can select between three file types:<br /><br /> -   **XML**: Layered strings of content and markup surrounded by tags indicating function.<br />-   **Variable Text**: Records have variable length and are separated by a character, such as comma or semi\-colon. Also known as *delimited file*.<br />-   **Fixed Text**: Records have the same length, using pad characters, and each record is on a separate line. Also known as *fixed-width file*. |
   |            **Type**             |                                                                                                                                                                                                              Specify what type of business activity the data exchange definition is used for, such as **Payment Export**.                                                                                                                                                                                                               |
   |   **Data Handling Codeunit**    |                                                                                                                                                                                                              Specify the codeunit that transfers data in and out of tables in [!INCLUDE[d365fin](includes/d365fin_md.md)].                                                                                                                                                                                                              |
   |     **Validation Codeunit**     |                                                                                                                                                                                                                         Specify the codeunit that is used to validate data against pre-defined business rules.                                                                                                                                                                                                                          |
   |  **Reading/Writing Codeunit**   |                                                                                                                                                                                                                   Specify the codeunit that processes imported data prior to mapping and exported data after mapping.                                                                                                                                                                                                                   |
   |   **Reading/Writing XMLport**   |                                                                                                                                                                      Specify the XMLport through which an imported data file or service enters prior to mapping and through which exported data exits when it is written to a data file or service after mapping.                                                                                                                                                                       |
   | **Ext. Data Handling Codeunit** |                                                                                                                                                                                                                      Specify the codeunit that transfers external data in and out of the data exchange framework.                                                                                                                                                                                                                       |
   |   **User Feedback Codeunit**    |                                                                                                                                                                                                    Specify the codeunit that does various clean-up after mapping, such as marks the lines as exported and deletes temporary records.                                                                                                                                                                                                    |
   |        **File Encoding**        |                                                                                                                                                                                                                          Specify the encoding of the file. **Note:**  This field is only relevant for import.                                                                                                                                                                                                                           |
   |      **Column Separator**       |                                                                                                                                                                                                                      Specify how columns in the data file are separated, if the file is of type **Variable Text**.                                                                                                                                                                                                                      |
   |        **Header Lines**         |                                                                                                                                                                                  Specify how many header lines exist in the file.<br /><br /> This makes sure that the header data is not imported. **Note:**  This field is only relevant for import.                                                                                                                                                                                  |
   |         **Header Tag**          |                                                                                                                                                  If a header line exists in several positions in the file, enter the text of the first column on the header line.<br /><br /> This makes sure that the header data is not imported. **Note:**  This field is only relevant for import.                                                                                                                                                  |
   |         **Footer Tag**          |                                                                                                                                                  If a footer line exists in several positions in the file, enter the text of the first column on the footer line.<br /><br /> This makes sure that the footer data is not imported. **Note:**  This field is only relevant for import.                                                                                                                                                  |


4. On the **Line Definitions** FastTab, describe the formatting of lines in the data file by filling the fields as described in the following table.  

    > [!NOTE]  
    >  For import of bank statements, you only create one line for the single format of the bank statement file that you want to import.  
    >   
    >  For export of payments, you can create a line for each payment type that you want to export. In that case, the **Column Definitions** FastTab shows different columns for each payment type.  

   |       Field       |                                                                              Description                                                                              |
   |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **Code**      |                                                            Enter a code to identify the line in the file.                                                             |
   |     **Name**      |                                                           Enter a name that describes the line in the file.                                                           |
   | **Column Count**  |                                Specify how many columns the line in data file has. **Note:**  This field is only relevant for import.                                 |
   | **Data Line Tag** |   Specify the position in the related XML schema of the element that represents the main entry of the data file. **Note:**  This field is only relevant for import.   |
   |   **Namespace**   | Specify the namespace that is expected in the file, to enable namespace validation. You can leave this field blank if you do not want to enable namespace validation. |


5. Repeat step 4 to create a line for every type of file data that you want to export.  

     Proceed to describe the formatting of columns in the data file by filling the fields on the **Column Definitions** FastTab as described in the table below. You can use the structure file, such as an .XSD file, for the data file to prefill the FastTab with the relevant elements. For more information, see [How to: Use XML Schemas to Prepare Data Exchange Definitions](across-how-to-use-xml-schemas-to-prepare-data-exchange-definitions.md).  

6. On the **Column Definitions** FastTab, choose **Get File Structure**.  
7. In the **Get File Structure** window, select the related structure file, and then choose the **OK** button. The lines on the **Column Definitions** FastTab are filled according to the structure of the data file.  
8. On the **Column Definitions** FastTab, edit or fill the fields as described in the following table.  


   |            Field             |                                                                                                                                                                                            Description                                                                                                                                                                                            |
   |------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        **Column No.**        |                                                                                                Specify the number that reflects the column’s position on the line in the file.<br /><br /> For XML files, specify the number that reflects the type of element in the file that contains the data.                                                                                                |
   |           **Name**           |                                                                                                                                        Specify the name of the column.<br /><br /> For XML files, specify the markup that marks the data to be exchanged.                                                                                                                                         |
   |        **Data Type**         |                                                                                                                                                        Specify if the data to be exchanged is of type **Text**, **Date**, or **Decimal**.                                                                                                                                                         |
   |       **Data Format**        | Specify the format of the data, if any. For example, **MM-dd-yyyy** if the data type is **Date**. **Note:**  For export, specify the data format according to [!INCLUDE[d365fin](includes/d365fin_md.md)]. For import, specify the data format according to the .NET Framework. For more information, see [Standard Date and Time Format Strings](https://go.microsoft.com/fwlink/?LinkID=323466). |
   | **Data Formatting Culture**  |                  Specify the culture of the data format, if any. For example, **en-US** if the data type is **Decimal** to make sure that comma is used as the .000 separator, according to the US format. For more information, see [Standard Date and Time Format Strings](https://go.microsoft.com/fwlink/?LinkID=323466). **Note:**  This field is only relevant for import.                   |
   |          **Length**          |                                                                                                                                           Specify the length of the fixed-width line that holds the column if the data file is of type **Fixed Text**.                                                                                                                                            |
   |       **Description**        |                                                                                                                                                                        Enter a description of the column, for information.                                                                                                                                                                        |
   |           **Path**           |                                                                                                                                                                  Specify the position of the element in the related XML schema.                                                                                                                                                                   |
   | **Negative-Sign Identifier** |                                                         Enter the value that is used in the data file to identify negative amounts, in data files that cannot contain negative signs. This identifier is then used to reverse the identified amounts to negative signs during import. **Note:**  This field is only relevant for import.                                                          |
   |         **Constant**         |                                                                                                                   Specify any data that you want to export in this column, such as extra information about the payment type. **Note:**  This field is only relevant for export.                                                                                                                   |


9. Repeat step 8 for every column or XML element in the data file that has data that you want to exchange with [!INCLUDE[d365fin](includes/d365fin_md.md)].  

   The next step in creating a data exchange definition is to decide which columns or XML elements in the data file map to which fields in [!INCLUDE[d365fin](includes/d365fin_md.md)].  

> [!NOTE]  
>  The specific mapping depends on the business purpose of the data file to be exchanged and on local variations. Even the SEPA bank standard has local variations. [!INCLUDE[d365fin](includes/d365fin_md.md)] supports import of SEPA CAMT bank statement files out\-of\-the\-box. This is represented by the **SEPA CAMT** data exchange definition record code in the **Data Exchange Definitions** window. For information about the specific field mapping of this SEPA CAMT support, see [Field Mapping When Importing SEPA CAMT Files](across-field-mapping-when-importing-sepa-camt-files.md).  

#### To map columns in the data file to fields in [!INCLUDE[d365fin](includes/d365fin_md.md)]  
1. On the **Line Definitions** FastTab, select the line for which you want to map columns to fields, and then choose **Field Mapping**. The **Data Exchange Mapping** window opens.  
2. On the **General** FastTab, specify the mapping setup by filling the fields as described in the following table.  


   |             Field             |                                                                                                                                                                                                                                           Description                                                                                                                                                                                                                                            |
   |-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |         **Table ID**          |                                                                                                                                                                                               Specify the table that holds the fields to or from which data is exchanged according to the mapping.                                                                                                                                                                                               |
   | **Use as Intermediate Table** | Specify if the table that you select in the **Table ID** field is an intermediate table where the imported data is stored before it is mapped to the target table.<br /><br /> You typically use an intermediate table when the data exchange definition is used to import and convert electronic documents, such as vendor invoices into purchase invoices in [!INCLUDE[d365fin](includes/d365fin_md.md)]. For more information, see [Exchanging Data Electronically](across-data-exchange.md). |
   |           **Name**            |                                                                                                                                                                                                                               Enter a name for the mapping setup.                                                                                                                                                                                                                                |
   |   **Pre-Mapping Codeunit**    |                                                                                                                                                                                 Specify the codeunit that prepares the mapping between fields in [!INCLUDE[d365fin](includes/d365fin_md.md)] and external data.                                                                                                                                                                                  |
   |     **Mapping Codeunit**      |                                                                                                                                                                          Specify the codeunit that is used to map the specified columns or XML data elements to fields in [!INCLUDE[d365fin](includes/d365fin_md.md)].                                                                                                                                                                           |
   |   **Post-Mapping Codeunit**   |            Specify the codeunit that completes the mapping between fields in [!INCLUDE[d365fin](includes/d365fin_md.md)] and external data. **Note:**  When using the Bank Data Conversion Service feature, the codeunit converts exported data from [!INCLUDE[d365fin](includes/d365fin_md.md)] to a generic format that is ready for export. For import, the codeunit converts external data to a format that is ready for import into [!INCLUDE[d365fin](includes/d365fin_md.md)].            |


3. On the **Field Mapping** FastTab, specify which columns map to which fields in [!INCLUDE[d365fin](includes/d365fin_md.md)] by filling the fields as described in the following table.  

   |Field|Description|  
   |---------------------------------|---------------------------------------|  
   |**Column No.**|Specify which column in the data file that you want to define a map for.<br /><br /> You can only select columns that are represented by lines on the **Column Definitions** FastTab in the **Data Exchange Definition** window.|  
   |**Field ID**|Specify which field the column in the **Column No.** field maps to.<br /><br /> You can only select from fields that exist in the table that you specified in the **Table** field on the **General** FastTab.|  
   |**Optional**|Specify that the map will be skipped if the field is empty. **Note:**  If you do not select this check box, an export error will occur if the field is empty. **Note:**  This field is only relevant for export.|  
   |**Target Table ID**|Only visible when the **Use as Intermediate Table** check box is selected.<br /><br /> Specify the table that the value in the **Column Caption** field is mapped to, when you are using an intermediate table for data import.|  
   |**Target Table Caption**|Only visible when the **Use as Intermediate Table** check box is selected.<br /><br /> Specify the name of the table in the **Target Table ID** field, which is the table that the value in the **Column Caption** field is mapped to, when you are using an intermediate table for data import.|  
   |**Target Field ID**|Only visible when the **Use as Intermediate Table** check box is selected.<br /><br /> Specify the field in the target table that the value in the **Column Caption** field is mapped to, when you are using an intermediate table for data import.|  
   |**Target Field Caption**|Only visible when the **Use as Intermediate Table** check box is selected.<br /><br /> Specify the name of the field in the target table that the value in the **Column Caption** field is mapped to, when you are using an intermediate table for data import.|  
   |**Optional**|Only visible when the **Use as Intermediate Table** check box is selected.<br /><br /> Specify if the map should be skipped if the field is empty. If you do not select this check box, then an export error will occur if the field is empty.|  

   The data exchange definition is now ready to be enabled for users. For more information, see [How to: Set Up Electronic Document Sending and Receiving](across-how-to-set-up-electronic-document-sending-and-receiving.md), [How to: Set Up SEPA Credit Transfer](finance-how-to-set-up-sepa-credit-transfer.md), [How to: Set Up SEPA Direct Debit](finance-how-to-set-up-sepa-direct-debit.md), and [Make Payments with Bank Data Conversion Service or SEPA Credit Transfer](finance-make-payments-with-bank-data-conversion-service-or-sepa-credit-transfer.md).  

   When you have created the data exchange definition for a specific data file, you can export the data exchange definition as an XML file that can be used to quickly enable import of the data file in question. This is described in the following procedure.  

### To export a data exchange definition as an XML file for use by others  
1. In the **Search** box, enter **Data Exchange Definitions**, and then choose the related link.  
2. Select the data exchange definition that you want to export.  
3. Choose the **Export Data Exchange Definition** action.  
4. Save the XML file that represents the data exchange definition in an appropriate location.  

    If a data exchange definition has already been created, you just have to import the XML file into the Data Exchange Framework. This is described in the following procedure.  

### To import an existing data exchange definition  
1. Save the XML file that represents the data exchange definition in an appropriate location.  
2. In the **Search** box, enter **Data Exchange Definitions**, and then choose the related link.  
3. Choose the **New** action. The **Data Exchange Definitio** window opens.  
4. Choose the **Import Data Exchange Definition** action.  
5. Choose the file that you saved in step 1.  

## See Also
[Dynamics 365 Business Central](https://docs.microsoft.com/dynamics365/business-central/)  
[Setting Up Data Exchange](across-set-up-data-exchange.md)  
[How to: Set Up Electronic Document Sending and Receiving](across-how-to-set-up-electronic-document-sending-and-receiving.md)  
[How to: Set Up SEPA Credit Transfer](finance-how-to-set-up-sepa-credit-transfer.md)  
[How to: Set Up SEPA Direct Debit](finance-how-to-set-up-sepa-direct-debit.md)  
[Make Payments with Bank Data Conversion Service or SEPA Credit Transfer](finance-make-payments-with-bank-data-conversion-service-or-sepa-credit-transfer.md)  
[Incoming Documents](across-income-documents.md)  
[General Business Functionality](ui-across-business-areas.md)  
