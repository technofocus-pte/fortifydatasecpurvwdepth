# Lab 4 - Create and manage sensitivity labels

## Introduction

Patti Fernandez, an Information Security Administrator at Contoso Ltd., is deploying a modern sensitivity labeling framework to strengthen data protection across the organization. Patti create and publish sensitivity label groups and labels to classify and protect content, including encryption, auto-labeling, and Double Key Encryption (DKE). Patti will also integrate Microsoft Purview with Microsoft Defender for Cloud Apps to extend data protection controls to files stored in cloud locations.

**Tasks**:

- Enable support for sensitivity labels

- Create a label group

- Create a child label

- Publish labels

- Configure auto-labeling

- Create and publish a DKE label for confidential content

- Enable Microsoft Purview integration in Defender for Cloud Apps

- Create a file policy to label externally shared files

## Exercise 1 – Enable support for sensitivity labels

In this task, you'll enable co-authoring for sensitivity labels, which also enables sensitivity labels for files in SharePoint and OneDrive.

1. You should still be logged into the VM using **admin** account.

1. Open **Microsoft Edge**, then navigate to `https://purview.microsoft.com` and log into Microsoft Purview as Patti Fernandes.

1. In the left navigation, select **Settings** > **Information Protection**.

	![](./media/Image1.png)

1. On the **Information Protection settings** page, ensure you're on the **Co-authoring for files with sensitivity labels** tab.

1. Select the checkbox for **Turn on co-authoring for files with sensitivity labels**.

	![](./media/Image2.png)

1. Select **Apply** at the bottom of the screen.

	![](./media/Image3.png)

You have successfully enabled support for sensitivity labels for files in SharePoint and OneDrive.
  
<!--

### Task 2 – Migrate to the modern label scheme

With sensitivity label support enabled, you'll confirm that the tenant uses the modern label scheme. If it still uses the classic scheme, you'll migrate to the modern one to ensure new labels and policies use the latest configuration model.

1. In the left navigation, select **Information Protection** > **Sensitivity labels**.

1. On the **Sensitivity labels** page, review the information box for **Migrate to the modern label scheme**, then select **Get started**.

1. In the **Migrate to the modern label scheme** flyout, review the summary to understand how existing labels and policies will be affected.

1. At the bottom of the flyout, select **Migrate**.

1. In the **Confirm migration to modern label scheme** dialog box, select **Confirm migration**.

    > [!Note] **Note**: The migration process might take a few minutes to complete.

You've successfully migrated your tenant to the modern sensitivity label scheme. New labels and policies you create will now use the modern configuration experience.

-->

## Exercise 2 - Working with Sensitivity lables

### Task 1 – Create a label group

In this task, you'll create a label group to organize internal sensitivity labels. Label groups act as containers for related labels, like department or business unit classifications.

1. In **Microsoft Edge**, navigate to `https://purview.microsoft.com`.

1. In the Microsoft Purview portal, select **Solutions** from the left sidebar, then select **Information Protection**.

	![](./media/Image4.png)

1. On the **Microsoft Information Protection** page, on the left sidebar, select **Sensitivity labels**.

	![](./media/Image5.png)

1. On the **Sensitivity labels** page select **+ Create** > **Label group**.

	![](./media/Image6.png)

1. The **New label group** configuration will start. On the **Provide basic details for this label group**, enter:

    - **Name**: `Internal`
    - **Display name**: `Internal`
    - **Description for users**: `Internal sensitivity label.`
    - **Description for admins**: `Internal sensitivity label group for Contoso.`

1. Select **Next**.

	![](./media/Image7.png)

1. On the **Review your settings and finish** page, select **Create label group**.

	![](./media/Image8.png)

1. On the **Your label group was created successfully** page, select **Don't create a label yet**, then select **Done**.

	![](./media/Image9.png)

You've created a label group for internal use. This group helps you manage related labels for specific departments or data categories.

### Task 2 – Create a child label

Now that you've created a label group, you'll add a child label for HR-related content. This label enforces encryption and content markings to protect HR data from unauthorized access.

1. On the **Sensitivity labels** page, find the **Internal** sensitivity label group. Select the vertical ellipsis (**...**) next to it, then select **+ Create label in group** from the dropdown menu.

	![](./media/Image10.png)

1. The **New sensitivity label** wizard will start. On the **Provide basic details for this label** page enter:

   - **Name**: `Employee data (HR)`
   - **Display name**: `Employee data (HR)`
   - **Description for users**: `This HR label is the default label for all specified documents in the HR Department.`
   - **Description for admins**: `This label is created in consultation with Ms. Jones (Head of the HR department). Contact her if you need to change the label settings.`

1. Select **Next**.

	![](./media/Image11.png)

1. On the **Define the scope for this label** page, select **Files** and **Emails**. If the checkbox for **Meetings** is selected, make sure it's deselected.

1. Select **Next**.

	![](./media/Image12.png)

1. On the **Choose protection settings for labeled items** page, select the **Control access** and **Apply content marking** options, then select **Next**.

	![](./media/Image13.png)

1. On the **Access control** page, select **Configure access control settings**.

1. Configure the encryption settings with these options:

   - **Assign permissions now or let users decide?**: Assign permissions now
   - **User access to content expires**: Never
   - **Allow offline access**: Only for a number of days
   - **Users have offline access to the content for this many days**: 15
     ![](./media/Image15.png)
   - Select the **Assign permissions** link. On the **Assign permissions** flyout panel, select **+ Add any authenticated users**, then select **Save** to apply this setting.
     ![](./media/Image15.png)
     ![](./media/Image16.png)

1. On the **Access control** page, select **Next**.

	![](./media/Image17.png)

1. On the **Content marking** page, select the toggle to enable **Content marking**.

	![](./media/Image18.png)

1. For each of the following marking types, select the checkbox, then select the edit icon to enter the text:

   |Marking type|Text|
   |:---|:---|
   |Add a watermark|`INTERNAL USE ONLY`|
   |Add a header|`Internal Document`|
   |Add a footer|`Contoso Confidential`|

1. Select **Next**.

	![](./media/Image19.png)

1. On the **Auto-labeling for files and emails** page, select **Next**.

	![](./media/Image20.png)

1. On the **Define protection settings for groups and sites** page, select **Next**.

	![](./media/Image21.png)

1. On the **Review your settings and finish** page, select **Create label**.

	![](./media/Image22.png)

1. On the **Your sensitivity label was created** page, select **Don't create a policy yet**, then select **Done**.

	![](./media/Image23.png)

You've created a child label within the Internal label group. The label applies encryption and content markings to HR documents, making sensitive data easy to identify and protected by policy.

### Task 3 – Publish labels

Next, you'll publish the HR label from the Internal label group so users in the HR department can apply it to their documents.

1. In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If not, navigate to `https://purview.microsoft.com` > **Solutions** > **Information Protection** > **Sensitivity labels**.

1. On the **Sensitivity labels** page select **Publish labels**.

	![](./media/Image24.png)

1. The publish sensitivity labels configuration will start.

1. On the **Choose sensitivity labels to publish** page, select the **Choose sensitivity labels to publish** link.

	![](./media/Image25.png)

1. On the **Sensitivity labels to publish** flyout panel, select the  **Internal/Employee data (HR)** checkbox, then select **Add** at the bottom of the flyout page.

	![](./media/Image26.png)

1. Back on the **Choose sensitivity labels to publish** page, select **Next**.

	![](./media/Image27.png)

1. On the **Assign admin units** page, select **Next**

	![](./media/Image28.png)

1. On the **Publish to users and groups** page, select **Next**.

	![](./media/Image29.png)

1. On the **Policy settings** page, select **Next**.

	![](./media/Image30.png)

1. On the **Default settings for documents** select **Next**.

	![](./media/Image31.png)

1. On the **Default settings for emails** select **Next**.

	![](./media/Image32.png)

1. On the **Default settings for meetings and calendar events** select **Next**.

	![](./media/Image33.png)

1. On the **Default settings for Fabric and Power BI content** page, select **Next**.

	![](./media/Image34.png)

1. On the **Name your policy** page, enter:

   - **Name**: `Internal HR employee data`

   - **Enter a description for your sensitivity label policy**: `This HR label is to be applied to internal HR employee data.`

1. Select **Next**.

	![](./media/Image35.png)

1. On the **Review and finish** page, select **Submit**.

	![](./media/Image36.png)

1. On the **New policy created** page, select **Done** to finish publishing your label policy.

	![](./media/Image37.png)

You've published the Internal label group and its HR label so users can apply them to HR documents. It might take up to 24 hours for the policy to propagate across services.

### Task 4 – Configure auto-labeling

1. In the Microsoft Purview portal, select **Solutions** > **Information Protection** > **Sensitivity labels**.

1. On the **Sensitivity labels** page, find the **Internal** sensitivity label. Select the vertical ellipsis (**...**), then select **+ Create label in group** from the dropdown menu.

	![](./media/Image38.png)

1. On the **Provide basic details for this label** page, enter:

   |Details|Text|
   |---|---|
   |**Name**|`Financial Data`|
   |**Display name**|`Financial Data`|
   |**Description for users**|`This content contains financial data that must be labeled and protected.`|
   |**Description for admins**|`This label is used for content that includes sensitive financial identifiers.`|

1. Select **Next**.

	![](./media/Image39.png)

1. On the **Define the scope for this label** page, select **Files** and **Emails**. If the checkbox for **Meetings** is selected, make sure it's deselected.

1. Select **Next**.

	![](./media/Image40.png)

1. On the **Choose protection settings for labeled items** page, select **Next**.

	![](./media/Image41.png)

1. On the **Auto-labeling for files and emails** page, set the **Auto-labeling for files and emails** to enabled.

	![](./media/Image42.png)

1. In the **Detect content that matches these conditions** section, select **+ Add condition** > **Content contains**.

	![](./media/Image43.png)

1. In the **Content contains** section, select the **Add** > **Sensitive info types**.

	![](./media/Image44.png)

1. In the **Sensitive info types** flyout page, search for and select these sensitive info types:

   - `Credit Card Number`
   - `ABA Routing Number`
   - `SWIFT Code`

1. Select **Add**.

	![](./media/Image45.png)

1. Back on the **Auto-labeling for files and emails** page, select **Next**.

	![](./media/Image46.png)

1. On the **Define protection settings for groups and sites** page, select **Next**.

	![](./media/Image47.png)

1. On the **Review your settings and finish** page, select **Create label**.

	![](./media/Image48.png)

1. On the **Your sensitivity label was created** page, select **Automatically apply label to sensitive content**, then select **Done**.

	![](./media/Image49.png)

1. On the **Create auto-labeling policy** flyout page, select **Review policy**.

	![](./media/Image50.png)

1. On the **Name your auto-labeling policy** page, leave the default, then select **Next**.

	![](./media/Image51.png)

1. On the **Choose a label to auto-apply** page, review to ensure the _Internal/Financial Data_ label is selected, then select **Next**.

	![](./media/Image52.png)

1. On the **Assign admin units** page, select **Next**.

	![](./media/Image53.png)

1. On the **Choose locations where you want to apply the label** page, select the options for:

   - Exchange email
   - SharePoint sites
   - OneDrive accounts

1. Select **Next**.

	![](./media/Image54.png)

1. On the **Set up common or advanced rules** page, leave the default **Common rules** selected, then select **Next**.

	![](./media/Image55.png)

1. On the **Define rules for content in all locations** page, expand the rules for _Financial Data rule_ to ensure the expected rules are defined, then select **Next**.

	![](./media/Image56.png)

1. On the **Additional settings for email** page, select **Next**.

	![](./media/Image57.png)

1. On the **Decide if you want to test out the policy now or later** page, select **Run policy in simulation mode**, and select the checkbox for **Automatically turn on policy if not modified after 7 days in simulation.**

	![](./media/Image58.png)

1. Select **Next**.

	![](./media/Image59.png)

1. On the **Review and finish** page, select **Create policy**.

	![](./media/Image60.png)

1. On the **Your auto-labeling policy was created** page, select **Done**.

You've created a child label for financial data and configured an auto-labeling policy that detects and labels content containing financial information.

### Task 5 – Create and publish a DKE label for confidential content

Next, you'll create a child label in the Internal group that uses Double Key Encryption (DKE) and dynamic watermarking to protect confidential legal content.

1. In **Microsoft Edge**, navigate to `https://purview.microsoft.com` and log into the Microsoft Purview portal as **Patti Fernandes**.

1. In the Microsoft Purview portal, select **Solutions** > **Information Protection** > **Sensitivity labels**.

1. On the **Sensitivity labels** page, find the **Internal** sensitivity label group. Select the vertical ellipsis (**...**), then select **+ Create label in group** from the dropdown menu.

	![](./media/Image61.png)

1. On the **Provide basic details for this label** page, enter:

   |Details|Text|
   |---|---|
   |**Name**|`Confidential Legal`|
   |**Display name**|`Confidential Legal`|
   |**Description for users**|`Use this label for highly sensitive legal content that must be encrypted using Double Key Encryption.`|
   |**Description for admins**|`Label configured with DKE and dynamic watermarking for highly sensitive legal content.`|

1. Select **Next**.

	![](./media/Image62.png)

1. On the **Define the scope for this label** page, select **Files** and **Emails**. If the checkbox for **Meetings** is selected, make sure it's deselected, then select **Next**.

	![](./media/Image63.png)

1. On the **Choose protection settings for the types of items you selected** page, select **Control access**, then select **Next**.

	![](./media/Image64.png)

1. On the **Access control** page, select **Configure access control settings**.

	![](./media/Image65.png)

1. Configure the encryption settings with these options:

   - **Assign permissions now or let users decide?**: Assign permissions now

   - **User access to content expires**: A number of days after label is applied

   - **Access expires this many days after the label is applied**: 5

   - **Allow offline access**: Never

   - Select the **Assign permissions** link. On the **Assign permissions** flyout panel, select the **+ Add users or groups**.

     ![](./media/Image66.png)

   - On the **Add users or groups** flyout page, search for and select `Legal Team` and `Patti Fernandes`, and select **Add**.

     ![](./media/Image67.png)

   - On the **Assign permissions** page, select **Save**.

     ![](./media/Image68.png)

1. Back on the **Access control** page, select the checkbox for **Use dynamic watermarking**, then select **Customize text (optional)**.

	![](./media/Image69.png)

1. On the **Add custom text to watermark (optional)** page, enter `Confidential`, then select **UPN** and **Timestamp**.

1. Select **Save** at the bottom of the flyout page.

	![](./media/Image70.png)

1. Back on the **Access control** page, select the checkbox for **Use Double Key Encryption**, and enter `https://testingdke1.azurewebsites.net/Test` as the URL for the Double Key Encryption service.

1. Select **Next**.

	![](./media/Image71.png)

1. On the **Auto-labeling for files and emails** page, select **Next**.

	![](./media/Image72.png)

1. On the **Define protection settings for groups and sites** page, select **Next**.

	![](./media/Image73.png)

1. On the **Review your settings and finish** page, select **Create label**.

	![](./media/Image74.png)

1. On the **Your sensitivity label was created** page, select **Publish label to users' apps**, then select **Done**.

	![](./media/Image75.png)

1. On the **Publish label** flyout page, select **Create new label policy**.

	![](./media/Image76.png)

1. On the **Choose sensitivity labels to publish** page, select **Choose sensitivity labels to publish** and add the **Internal/Confidential Legal** label, then select **Add**.

	![](./media/Image77.png)

1. Select **Next**.

	![](./media/Image78.png)

1. On the **Assign admin units** page, select **Next**.

	![](./media/Image79.png)

1. On the **Publish to users and groups** page, leave the default selected, then select **Next**.

	![](./media/Image80.png)

1. On the **Policy settings** page, select the checkbox for **Users must provide a justification to remove a label or lower its classification**, then select **Next**.

	![](./media/Image81.png)

1. On the **Default settings for documents​** page, select **Next**.

	![](./media/Image82.png)

1. On the **Default settings for emails​** page, select **Next**.

	![](./media/Image83.png)

1. On the **Default settings for meetings and calendar events​** page, select **Next**.

	![](./media/Image84.png)

1. On the **Default settings for Fabric and Power BI content​** page, select **Next**.

	![](./media/Image85.png)

1. On the **Name your policy** page, enter:

   - **Name**: `Confidential Legal`

   - **Description**: `Enables manual use of the DKE label for confidential content accessible by Legal.`

1. Select **Next**.

	![](./media/Image86.png)

1. On the **Review and finish** page, select **Submit**.

	![](./media/Image87.png)

1. On the **New policy created** page, select **Done**.

	![](./media/Image88.png)

You've created and published a child label using Double Key Encryption and dynamic watermarking. This label restricts access to authorized users and enforces justification for downgrading classifications.

## Exercise 3 - File policy using lables with Microsoft Purview

### Task 1 – Enable Microsoft Purview integration in Defender for Cloud Apps

With your sensitivity labels created and published, you'll now integrate Microsoft Purview with Microsoft Defender for Cloud Apps. This integration allows Defender to scan files for sensitivity labels and apply file monitoring.

1. Open **Microsoft Edge**, then go to **Microsoft Defender** by navigating to `https://security.microsoft.com`.

1. In the left navigation, select **Settings**, then select **Cloud Apps**.

	![](./media/Image89.png)

1. Under the **Information Protection** section in the left pane, select **Microsoft Information Protection**.

	![](./media/Image90.png)

1. On the **Microsoft Information Protection** page, select both checkboxes available on the page.

   - **Automatically scan new files for Microsoft Information Protection sensitivity labels and content inspection warnings**

      Enables Defender for Cloud Apps to automatically scan new or modified files for sensitivity labels and content inspection warnings from Microsoft Purview.

   - **Only scan files for Microsoft Information Protection sensitivity labels and content inspection warnings from this tenant**

      Limits scanning to labels and warnings created in your own organization. Labels applied by external tenants will be ignored.

1. Select **Save** to apply the settings.

	![](./media/Image91.png)

1. Under the **Information Protection** section in the left pane, select **Files**.

	![](./media/Image92.png)

1. On the **Files** page, select **Enable file monitoring**.

	![](./media/Image93.png)

1. Select **Save** to apply the settings.

	![](./media/Image94.png)

You've enabled Microsoft Purview integration in Defender for Cloud Apps. Defender can now detect sensitivity labels and monitor files for policy evaluation and governance actions.

<!---

NOTE - Reworking task 8 due to tenant issue

### Task 2 – Create a file policy to auto-label externally shared files

Now that label scanning is enabled, you'll create a file policy that applies the **Highly Confidential - Project - Falcon** sensitivity label to files in the Mark 8 Project folders that are shared outside your organization. This policy is categorized as DLP because it protects sensitive data from unintended exposure.

1. In **Microsoft Defender**, navigate to **Cloud apps** > **Policies** > **Policy management**.

1. Select the **Information protection** tab, then select **Create policy** > **File policy**.

1. On the **Create file policy** page, configure:

   - **Policy name**: `Auto-label external sharing for Project Falcon files`

   - **Policy severity**: **High**

   - **Category**: **DLP**

   - **Apply to**: **Selected folders**

      - Select **Add folder(s)**, then search for `Project` in the **File name** field.

      - Select the checkbox for the **Mark 8 Project Team Notebook** and **Mark 8 Project team** SharePoint folders.

      - Select **Done** to close the **Select a folder** window.

   - In the **Files matching all of the following section**:

      - For the first filter, configure the dropdowns to: **Access level equals external**

      - For the second filter, configure the dropdowns to: **Last modified after (date)** and use today's date

   - Under **Governance actions**, expand **Microsoft OneDrive for Business**:

      - Select the checkbox for **Apply sensitivity label**

      - In the dropdown select **Highly Confidential-Project - Falcon**

   - Repeat the same process for **Microsoft SharePoint Online**

      - Select the checkbox for **Apply sensitivity label**

      - Select **Highly Confidential-Project - Falcon** from the dropdown

1. Select **Create** to finish creating the file policy.

You've created a file policy that applies a highly confidential sensitivity label to externally shared files located in the Mark 8 Project folders in SharePoint and OneDrive. Once a matching file is detected, Defender for Cloud Apps will apply the label automatically.
-->

### Task 2 – Create a file policy to label externally shared files

Finally, you'll create a file policy that automatically applies a sensitivity label to files shared externally. This ensures sensitive content remains protected even when shared outside the organization.

1. In **Microsoft Defender**, navigate to **Cloud apps** > **Policies** > **Policy management**.

	![](./media/Image95.png)

1. Select the **Information protection** tab, then select **Create policy** > **File policy**.

	![](./media/Image96.png)

1. On the **Create file policy** page, configure:

   - **Policy name**: `Auto-label externally shared files`

   - **Policy severity**: **High**

   - **Category**: **DLP**

   - In the **Files matching all of the following section**:

      - For the first filter, configure the dropdowns to: **Access level equals external**

      - For the second filter, configure the dropdowns to: **Last modified after (date)** and use today's date

        ![](./media/Image97.png)

   - Under **Governance actions**, expand **Microsoft OneDrive for Business**:

      - Select the checkbox for **Apply sensitivity label**

      - In the dropdown select **Highly Confidential-Specified People**

        ![](./media/Image98.png)

   - Repeat the same process for **Microsoft SharePoint Online**

      - Select the checkbox for **Apply sensitivity label**

      - Select **Highly Confidential-Specified People** from the dropdown

        ![](./media/Image99.png)

1. Select **Create** to finish creating the file policy.

	![](./media/Image100.png)

You've created a file policy that applies sensitivity labels to externally shared files. This policy extends your information protection strategy to cloud-stored content.

## Summary

In this lab, you assumed the role of Patti Fernandez, a system administrator at Contoso Ltd., and implemented information protection using Microsoft Purview Sensitivity Labels. You enabled sensitivity label support in SharePoint and Teams using PowerShell, created and published an Internal label and an HR-specific sublabel, and applied these labels in Word documents and Outlook emails. You also created and published an auto-labeling sensitivity label for GDPR-related content specific to Germany. These steps ensure HR and regulatory documents are properly classified and protected within the organization.

