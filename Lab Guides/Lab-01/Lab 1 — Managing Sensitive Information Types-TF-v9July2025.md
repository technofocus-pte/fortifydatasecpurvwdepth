# **Lab 1 — Managing Sensitive Information Types​**

## Introduction

Contoso Ltd. previously had issues with employees accidentally sending
out personal information from customers when working on support tickets
in the ticketing solution.

To educate users in the future, a custom sensitive information type is
required to identify employee IDs in emails and documents, which consist
of three uppercase characters and six numbers, using Sensitive info
types. To lower the false positive rate, the keywords "Employee" and
"IDs" will be used.

## Objectives

- Create a **custom sensitive information type** using regular
  expressions and keyword lists.

- Configure and define an **EDM-based sensitive info type** using
  structured employee data.

- Hash and upload employee data to the **EDM Upload Agent** for
  classification.

- Build a **keyword dictionary-based sensitive info type** to identify
  confidential health-related terms.

- Test and validate custom sensitive info types for accuracy before
  applying them in policies.

## Exercise 1 – Creating Custom Sensitive Information Types

In this exercise, you will use the **Security & Compliance Center
PowerShell** module to create a new custom sensitive information type
that recognizes the pattern of employee IDs near the keywords "Employee"
and "ID".

1.  In **Microsoft Edge**, open a **New InPrivate Window**, navigate
    to ++**https://**purview**.microsoft.com**++ and log in as
    **Patti Fernandez** using the
    username **PattiF@WWLxXXXXXX.onmicrosoft.com** and the User Password
    given on your resources tab.

2.  From the left navigation, select **Solutions** \> **Data Loss
    Prevention**.

![](./media/image1.png)

3.  Select **Classifiers** from the left pane. Select **Sensitive info
    types** from the sub-navigation pane. Select **+Create sensitive
    info type** to open the wizard for a new sensitive information type.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

4.  On the **Name your sensitive info type** page, enter the following
    information:

    - **Name**: ++**Contoso Employee IDs**++

    - **Description**: **+++Pattern for Contosoemployee IDs+++.**

5.  Select **Next**.

![Graphical user interface, application Description automatically
generated](./media/image3.png)

6.  On the **Define patterns for this sensitive info type** page,
    select **Create pattern**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

7.  In the **New pattern** pane that appears on the right side,
    select **Add primary element** and select **Regular expression**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image5.png)

8.  In the new right-side pane **Add a regular expression**, enter the
    following:

    - **ID**: **+++Contoso IDs+++**

    - **Regular expression**: **+++\s\[A-Z\]{3}\[0-9\]{6}\s+++**

    - Select **String match**

9.  Select **Done**.

![Graphical user interface, application Description automatically
generated](./media/image6.png)

10. In the New pattern pane, decrease the **Character proximity** value
    to ***100*** characters.

![](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. Navigate to **Supporting elements** heading, click on **+ Add
    supporting elements or group of elements** drop-down menu and
    select **Keyword list**.

![Graphical user interface, application Description automatically
generated](./media/image9.png)

12. In the **Add a keyword list** pane, enter the following:

    - **ID**: **+++Employee ID keywords+++**

    - **Case insensitive**:**+++Employee** **ID+++**

> ![](./media/image10.png)

13. Scroll down and select the radio button beside **Word match**. Then,
    click on the **Done** button. 

![](./media/image11.png)

14. Now, click on the **Create** button.

![](./media/image12.png)

15. Back on the **Define patterns for this sensitive info type** page
    select **Next**.

![Graphical user interface, text, application, Teams Description
automatically generated](./media/image13.png)

16. On the **Choose the recommended confidence level to show in
    compliance policies** page, use the default value and
    select **Next** button.

![](./media/image14.png)

17. On the **Review settings and finish** page review the settings and
    select **Create**. When successfully created select **Done**.

![](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

18. Leave the browser window open.

You have successfully created a new sensitive information type to
identify employee IDs in the pattern of three uppercase characters, six
numbers, and the keywords 'Employee' or 'IDs' within a range of 100
characters.

## Exercise 2 – Creating EDM-based classification information type

As an extra search pattern, you will create an EDM-based classification
with a database schema of employee data. The database source file will
be formatted with the following data fields of employees: Name,
Birthdate, StreetAddress, and EmployeeID.

1.  Click on Solutions, then select **Data Loss Prevention**
    ![](./media/image17.png)

2.  Click on **Classifiers**, then select **EDM classifiers**. In the
    EDM classifiers page, click on the toggle button beside **New EDM
    experience** to turn it **Off**

![](./media/image18.png)

3.  Then, click on **Create** **EDM schema**

![](./media/image19.png)

4.  In the **Name** field, enter **+++employeedb+++**.

5.  In the **Description** field,
    enter **+++Employee Database schema.+++**.  
    Uncheck **Ignore delimiters and punctuation for all schema fields**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

6.  In the first Schema field name, enter **+++Name+++** and mark
    the **Field is searchable** box.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

7.  Click the dropdown for **Choose delimiters and punctuation to
    ignore** and select **Hyphen**, **Period**, **Space**, **Open
    parenthesis** and **Close parenthesis**.

![Graphical user interface, application Description automatically
generated](./media/image23.png)

8.  Select **+ Add schema data field** from the lower end.

![](./media/image24.png)

9.  In **Schema field name**, below **Schema field \#2**,
    enter **+++Birthdate+++**.

10. Select **+ Add schema data field** from the lower end again.

11. In **Schema field name**, below **Schema field \#3**,
    enter **+++StreetAddress+++**.

12. Select **+ Add schema data field** from the lower end a last time.

13. In **Schema field name**, below **Schema field \#4**,
    enter **+++EmployeeID+++**.

14. Select **Field is searchable**.

15. Select **Save**.

![Graphical user interface, application Description automatically
generated](./media/image25.png)

16. Select **EDM sensitive info types** from the left pane and
    select **+ Create EDM sensitive info type** to open the **EDM rule
    package** wizard.

![](./media/image26.png)

17. On the **Define data store schema** page, select **Choose an
    existing EDM schema**.

![Graphical user interface, application Description automatically
generated](./media/image27.png)

18. Select **employeedb** and select **Add**.

![Graphical user interface, text, application Description automatically
generated](./media/image28.png)

19. Review the data store schema and select **Next**.

![Graphical user interface, application Description automatically
generated](./media/image29.png)

20. On the **Define patterns for this EDM sensitive info type** page,
    select **+ Create pattern**.

![Graphical user interface, application Description automatically
generated](./media/image30.png)

21. On the **New pattern** pane on the right-side, in the **Primary
    element** field, select ***EmployeeID***.

22. Below **Primary element's sensitive info type**, select **Choose
    sensitive info type**.

![A screenshot of a pattern Description automatically
generated](./media/image31.png)

23. In the **Search** bar, enter ***Contoso*** and press the enter key.

24. Select **Contoso Employee IDs** and select **Done**.

25. Select **Done**.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

26. Select **Next** in the *Define patterns for this EDM sensitive info
    type* screen.

![Graphical user interface, text, application Description automatically
generated](./media/image33.png)

27. In the **Choose the recommended confidence level and character
    proximity** let the default value persist and select **Next**.

![Graphical user interface, text, application, Word Description
automatically generated](./media/image34.png)

28. In the **Name and describe your EDM sensitive info type** page,
    enter **+++Contoso Employee EDM+++** for the name.

29. In the **Description for admins** field, enter **+++EDM-based
    sensitive information type for employee personal information.+++**.
    Select **Next.**

![Graphical user interface, text, application Description automatically
generated](./media/image35.png)

30. Review the settings and select **Submit**.

![Graphical user interface, application Description automatically
generated](./media/image36.png)

31. On the **Your EDM sensitive info type was created** page,
    select **Done**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

32. Leave the browser open with the Microsoft Purview portal.

You have successfully created a new EDM-based classification sensitive
information type for identifying employee data from a database file
source.

## Exercise 3 – Creating EDM-based classification data source

To associate the EDM-based classification with a database containing
sensitive data, hashing and uploading the actual data for the sensitive
information type via the EDM Upload Agent tool is required next.

1.  In **Microsoft Edge**, navigate
    to **+++**https://go.microsoft.com/fwlink/?linkid=2088639**+++** to
    download the EDM download agent.

2.  Click on **Open file** link to access **EdmUploadAgent.msi**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image38.png)

3.  On **Welcome to the Microsoft Exact Data Match Upload Agent Setup
    Wizard** dialog box, click on the **Next** button.

![](./media/image39.png)

4.  In the **Microsoft Exact Data Match Upload Agent Setup** wizard,
    select **Next**.

    - Select **I accept the terms in the License Agreement** and
      select **Next**.

    - Do not change the default **Destination Folder** path and
      select **Next**.

    - Select **Install** to perform the installation.

    - When the **User Account Control** window opens, select **Yes**.

    - If asked to log in, log in via **Patti’s** account.

    - When the installation finishes, select **Finish**.

5\. Now, right click on the Windows icon, navigate and click **Run**. In
the **Run** dialog box, type +++notepad+++ then click on the **OK**
button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

6\. Enter the following text to the first line in the notepad window:

**+++Name,Birthdate,StreetAddress,EmployeeID**

**Patti Fernandez,01.06.1980,1Main Street,CSO123456**

**Christie Cline,31.01.1985,2Secondary Street,CSO654321+++**

7.  Select File and Save As: **+++EmployeeData.csv+++**

8.  Select the dropdown at **Save as type:** and select **All Files
    (*.*)**.

9.  In the **Encoding** field, ensure that **UTF-8** is selected, then
    click on the **Save** button.

![](./media/image42.png)

10. Close the Notepad window.

11. Right-click the Windows icon on the taskbar and select Windows
    PowerShell (Admin) to run it as administrator.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image43.png)

12. On the **User Account Control** dialog box, click on the **Yes**
    button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

13. Navigate to the EDM Upload Agent directory:

**+++cd "C:\Program Files\Microsoft\EdmUploadAgent"+++**

![Text Description automatically generated](./media/image45.png)

14. Authorize with your Account to upload the database to your tenant by
    running the following cmdlet:

**+++.\EdmUploadAgent.exe /Authorize+++**

![](./media/image46.png)

15. When the **Pick an account** window is displayed, log in as **Patti
    Fernandez** using the username **PattiF@WWLxXXXXXX.onmicrosoft.com**
    and the User Password given on your resources tab. (Or the new
    password you reset.)

> ![A computer screen with a sign in box AI-generated content may be
> incorrect.](./media/image47.png)
>
> ![A screenshot of a login box AI-generated content may be
> incorrect.](./media/image48.png)

16. Download the database schema definition of the EDM-based
    classification sensitive information type by running the following
    script in PowerShell:

**+++.\EdmUploadAgent.exe /SaveSchema /DataStoreNameemployeedb /OutputDirC:\Users\Admin\Documents\\++**

**Note**: If the last command fails, it possibly takes more time until
the **EDM_DataUploaders** group membership is applied. It can take up to
one hour until it is possible to download the schema file. If it fails
proceed to the next task and return to this step later. Or check the
path the documents folder on your VM.

![](./media/image49.png)

17. Hash the database file and upload it to the EDM-based classification
    sensitive information type by running the following script in
    PowerShell:

**+++.\EdmUploadAgent.exe /UploadData/DataStoreName employeedb /DataFileC:\Users\Admin\Documents\EmployeeData.csv /HashLocation C:\Users\Admin\Documents\\/SchemaC:\Users\Admin\Documents\employeedb.xml+++**

![](./media/image50.png)

**Note:** If you get the following errors

Error Type: System.IO.FileNotFoundException

Error Message: Unable to find the specified file.

Check the path where you saved the file EmployeeData.csv

![Text Description automatically generated](./media/image51.png)

18. Check the upload progress until the state changes to completed then
    run the following PowerShell command:

**+++.\EdmUploadAgent.exe /GetSession /DataStoreNameemployeedb+++**

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image52.png)

You have successfully hashed and uploaded a database file for a
EDM-based classification sensitive information type.

## Exercise 4 – Creating Keyword Dictionary

Several violations of personal information leakage happened when users
sent out emails after colleagues reported on sick leave. When that
happened the reason for illness or disease was sent out. We do not want
that to happen.

1.  In **Microsoft Edge**, open a **New InPrivate Window**, navigate
    to **+++https://purview.microsoft.com+++** and log in as **Patti
    Fernandez** using the username **PattiF@WWLxXXXXXX.onmicrosoft.com**
    and the User Password given on your resources tab.

2.  From the left navigation, select **Solutions** \> **Data Loss
    Prevention**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

3.  Select **Classifiers** from the left pane. Select **Sensitive info
    types** from the sub-navigation pane. Select **+Create sensitive
    info type** to open the wizard for a new sensitive information type.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

4.  On the **Name your sensitive info type** page, enter the following:

    - Name: **+++Contoso Diseases List+++**

    - Description: **+++List of possible diseases of employees.+++**

![Graphical user interface, application, Teams Description automatically
generated](./media/image55.png)

5.  Select **Next**.

6.  On the **Define patterns for this sensitive info type** page,
    select **+ Create pattern**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image56.png)

7.  Select the dropdown field below **Primary element** and
    select **Keyword dictionary**.

![Graphical user interface, application Description automatically
generated](./media/image57.png)

8.  In the **Add a keyword dictionary** page enter the
    name **!!*Diseases Dictionary*!!**.

9.  In the **Keywords** area enter the following keywords, each into a
    separate line:

**+++flu**

**influenza**

**cold**

**bronchitis**

**otitis+++**

![](./media/image58.png)

10. Select **Done**.

11. Below **Supporting elements**, select **+ Add supporting elements or
    group of elements** drop-down and select **keyword list** to add
    additional support for the keyword dictionary.

![Graphical user interface, application Description automatically
generated](./media/image59.png)

12. In the **Add a keyword list** page enter **Employee **in
    the **ID** field. In the **Case insensitive** box, enter the
    following keywords, each into a separate line, then click on the
    **Done** button:

**+++EmployeeID**

**absence**

**reason+++**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

13. In the **New pattern** page, review the configuration and
    select **Create**.

![Graphical user interface, application Description automatically
generated](./media/image61.png)

14. In the **Define patterns for this sensitive info
    type** select **Next**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image62.png)

15. In the **Choose the recommended confidence level to show in
    compliance policies** let the default value persist and
    select **Next**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

16. In the **Review settings and finish** page, review your settings and
    select **Create**. When the process is complete select **Done**.

![](./media/image64.png)

17. Leave the browser window in the Microsoft Purview portal open.

You have successfully created a new sensitive information type based on
a keyword dictionary and added more keywords to decrease the false
positive rate. Proceed with the next task.

## Exercise 5 – Working with custom Sensitive Information Types

Custom Sensitive information types should always be tested before using
them in policies otherwise data loss or leakage may occur due to a
malfunctioning custom search pattern.

1.  Right click on the Windows icon, navigate and click **Run**. In the
    **Run** dialog box, type +++notepad+++ then click on the **OK**
    button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

2.  Enter the following text to the notepad window:

**+++Employee Patti Fernandez with EmployeeID HR-255801 is on absence
because of the flu/influenza+++**

3.  Select **File** and Save As **SickTestData** and select **Save**.

4.  Close the Notepad window.

5.  In **Microsoft Edge**, the Microsoft Purview portal tab should still
    be open. If so, select it and proceed to the next step. If you
    closed it, then in a new tab, navigate
    to **+++https://purview.microsoft.com+++**. Log in as **Patti
    Fernandez** using the username **PattiF@WWLxXXXXXX.onmicrosoft.com**
    and the User Password given on your resources tab.

6.  In the left navigation pane select **Solutions** \> **Data Loss
    Prevention**, then select the **Sensitive info types** under
    **Classifiers**. In the **Search** box from the upper right side and
    enter ***Contoso*** and press Enter. Click on **Contoso Employee
    IDs** to open the right side pane.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

7.  Select **Test** from the right-side pane.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

8.  On the **Upload file to test** page, select **Upload file**.

![](./media/image67.png)

9.  Select **Documents** from the left pane, select the file with the
    name **SickTestData** and select **Open**.

![Graphical user interface, text, application Description automatically
generated](./media/image68.png)

10. Select **Test** to start the analysis.

![Graphical user interface, text, application Description automatically
generated](./media/image69.png)

11. On the **Match results** page, review the found match.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

12. Select **Finish** and close the test page by clicking
    the **X** button.

![](./media/image71.png)

13. Back on the **Data classification** page, select the Sensitive
    Information Type with the name **Contoso Diseases List**.

14. In the right side pane, select **Test**.

![](./media/image72.png)

15. On the **Upload file to test** page, select **Upload file**.

![](./media/image73.png)

16. Select **Documents** from the left pane, select the file with the
    name *SickTestData* and select **Open**.

17. Select **Test** to start the analysis.

![Graphical user interface, text, application Description automatically
generated](./media/image74.png)

18. On the **Match results** page, review the found match. When done
    review select **Finish**.

## Summary:

In this lab, you’ve learned how to create and test custom Sensitive
Information Types (SITs) in Microsoft Purview using regular expressions,
keyword dictionaries, and Exact Data Match (EDM) techniques to enhance
data loss prevention capabilities.
