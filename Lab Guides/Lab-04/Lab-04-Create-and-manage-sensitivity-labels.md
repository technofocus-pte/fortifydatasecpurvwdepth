<!--
lab:
  title: Lab 4 — Protect high-value data with encrypted sensitivity labels, label groups, content marking and dynamic watermarking, client-side and service-side auto-labeling, and Defender for Cloud Apps integration
  description: In this lab we created and published encrypted sensitivity labels with content marking and watermarking, configured auto-labeling, and integrated labeling with Defender for Cloud Apps.
  duration: 30 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Information Protection
-->

# Lab 4 — Protect high-value data with encrypted sensitivity labels, label groups, content marking and dynamic watermarking, client-side and service-side auto-labeling, and Defender for Cloud Apps integration

Contoso Pharmaceuticals now has classifiers that detect its regulated data, but detection isn't protection. To actually protect the formulation intellectual property behind compound CX-2087 (Project Falcon), the personal and health information of trial participants, and the pre-publication trial results that are material non-public information, Contoso applies sensitivity labels that encrypt content, mark it visibly, and restrict who can open it. In this lab, acting as Allan Deyoung, you build a four-tier label taxonomy inside a label group, publish it, apply labels automatically through both client-side and service-side auto-labeling driven by the classifiers from Lab 2, prove that the encryption denies unauthorized access, and extend label protection to cloud-stored files through Microsoft Defender for Cloud Apps.

You build the most feature-rich label — the research label with scoped encryption and dynamic watermarking — in the portal to learn the full wizard, then create the rest of the taxonomy and its publishing policy with PowerShell, the way an administrator manages labels at scale. Every protection is then verified by exercising it.

**Learning outcomes.** After this lab you can:
- Enable sensitivity labels for files in SharePoint and OneDrive.
- Create a label group and a label with scoped encryption, content marking, and dynamic watermarking in the portal.
- Create the rest of a label taxonomy and its publishing policy with PowerShell.
- Configure client-side auto-labeling (in Office apps) and service-side auto-labeling (at rest) driven by custom classifiers.
- Prove that label encryption denies unauthorized access and permits authorized access.


**Tasks**:

1. Enable support for sensitivity labels
1. Create the label group and the crown-jewel label in the portal
1. Build the rest of the taxonomy with PowerShell
1. Publish the labels with a label policy
1. Configure client-side auto-labeling
1. Configure service-side auto-labeling
1. Apply the label and prove encryption denies unauthorized access


### Task 1 – Enable support for sensitivity labels

In this task, you'll enable co-authoring for files with sensitivity labels, which also turns on sensitivity labels for files stored in SharePoint and OneDrive so that labeled and encrypted Office files can be opened and co-authored there.

> [!Note]
>If you have followed Lab 0 thoroughly, please proceed to the next task.

1. In **Microsoft Edge**, navigate to +++https://purview.microsoft.com+++ and sign in as **Allan Deyoung**, `AllanD@TenantName` (the Tenant Name and account password are provided in the Resources tab).

1. In the upper-right corner, select **Settings**, then in the left navigation select **Information Protection**.

1. On the **Information Protection settings** page, select the **Co-authoring for files with sensitivity labels** tab.

1. Select the checkbox for **Turn on co-authoring for files with sensitivity labels**.

1. Select **Apply**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image1.png)

    > [!Note]
    > This setting is tenant-wide and can take a short time to take effect across SharePoint and OneDrive. It is a prerequisite for opening and co-authoring encrypted, labeled Office files in those services.

    You have successfully enabled support for sensitivity labels for files in SharePoint and OneDrive.


### Task 2 – Create the label group and a label in the portal

Contoso's most sensitive research content — the formulation and process intellectual property behind compound CX-2087 (Project Falcon) — requires the strongest everyday protection: encryption that only research staff can decrypt, content markings, and a dynamic watermark that stamps each viewer's identity onto the content. In this task, you'll create a label group and, inside it, the `Highly Confidential – Research` label with these settings, using the portal to learn the full configuration. In Task 3 you'll build the rest with PowerShell.

1. In the Microsoft Purview portal as **Allan Deyoung**, select **Solutions** > **Information Protection** > **Sensitivity labels**.

1. On the **Sensitivity labels** page, select **+ Create** > **Label group**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image2.png)

1. On the **Provide basic details for this label group** page, enter the following, then select **Next**:

    - **Name**:

        `Contoso Data Classification`

    - **Display name**:

        `Contoso Data Classification`

    - **Description for users**:

        `Contoso data classification labels.`

    - **Description for admins**:

        `Label group containing Contoso Pharmaceuticals data classification labels.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image3.png)


1. On the **Review your settings and finish** page, select **Create label group**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image4.png)

1. On the confirmation page, select **Create a label in this group** and then **Done** to start the new sensitivity label wizard within the group.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image5.png)

1. On the **Provide basic details for this label** page, enter the following, then select **Next**:

    - **Name**:

        `Highly Confidential - Research`

    - **Display name**:

        `Highly Confidential – Research`

    - **Description for users**:

        `Highly confidential research data, including drug formulation and process intellectual property. Restricted to research staff.`

    - **Description for admins**:

        `Encryption scoped to research staff, dynamic watermarking, content marking. Applied to CX-series compound IP.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image6.png)


1. On the **Define the scope for this label** page, select **Files & other data assets** and **Emails**. If **Meetings** is selected, deselect it. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image7.png)

1. On the **Choose protection settings for labeled items** page, select **Control access** and **Apply content marking**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image8.png)

1. On the **Access control** page, select **Configure access control settings**, then set:

    - **Assign permissions now or let users decide?**: **Assign permissions now**
    - **User access to content expires**: **Never**
    - **Allow offline access**: **Only for a number of days**
    - **Users have offline access to the content for this many days**:

        `15`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image9.png)


1. Select the **Assign permissions** link. On the **Assign permissions** flyout, select **+ Add users or groups**, search for and select the **Project Falcon** group and **Lynne Robbins**, then select **Add**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image10.png)

1. Set the permission level for both to **Editor**, then select **Save**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image11.png)

1. Select **Save** again on the **Assign permissions** pane.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image12.png)

    > [!Important]
    > The scoped permissions you set here are what make the encryption verifiable in Task 7. Only these research identities will be able to open the labeled document; any other user will be denied. Do not add "any authenticated users," or the denial test will not work.

1. Back on the **Access control** page, select the checkbox for **Use dynamic watermarking**. Select **Customize text (optional)**, enter `CONTOSO RESTRICTED`, select **UPN** and **Timestamp** so each viewer's identity and access time are stamped on the content, then select **Save**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image13.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image14.png)

1. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image15.png)

1. On the **Content marking** page, select the toggle to enable content marking. For each marking type below, select the checkbox, select the edit icon, and enter the text, then select **Next**:

    | Marking type    | Text                              |
    | --------------- | --------------------------------- |
    | Add a watermark | `HIGHLY CONFIDENTIAL – RESEARCH`  |
    | Add a header    | `Contoso Research – Restricted`   |
    | Add a footer    | `Do not distribute`               |

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image16.png)

1. On the **Auto-labeling for files and emails** page, select **Next** (client-side auto-labeling is configured in Task 5).

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image17.png)

1. On the **Define protection settings for groups and sites** page, select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image18.png)

1. On the **Review your settings and finish** page, select **Create label**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image19.png)

1. On the confirmation page, select **Don't create a policy yet**, then select **Done** (the policy is created for the whole taxonomy in Task 4).

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image20.png)

    You have successfully created the `Highly Confidential – Research` label with scoped encryption, content marking, and dynamic watermarking, inside the `Contoso Data Classification` group.


### Task 3 – Build the rest of the taxonomy with PowerShell

An administrator rarely clicks through the label wizard repeatedly. In this task, you'll create the remaining three tiers of the taxonomy — `General – Internal`, `Confidential – Clinical`, and `Restricted – Trial Data` — with the `New-Label` cmdlet, then confirm the full set. DO NOT forget to replace TenantName with the value in your environment.

1. On the client VM, open an elevated terminal: right-click the **Start** button and select **Terminal (Administrator)**. Select **Yes** on the User Account Control prompt.

1. Connect to Security & Compliance PowerShell. When the sign-in window appears, sign in as **Allan Deyoung**:

    ```powershell
    Import-Module ExchangeOnlineManagement
    Connect-IPPSSession -UserPrincipalName AllanD@TenantName
    ```

1. Create the `General – Internal` label — content marking only, no encryption:

    +++New-Label -Name "General - Internal" -DisplayName "General – Internal" ` -Tooltip "Internal Contoso content. Not for public release." ` -Comment "Everyday internal tier. Content marking only, no encryption." ` -ContentType "File, Email" ` -ApplyContentMarkingFooterEnabled $true ` -ApplyContentMarkingFooterText "Contoso Internal" ` -ApplyContentMarkingFooterFontSize 10+++

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image21.png)

1. Create the `Confidential – Clinical` label — encryption scoped to clinical staff:

    +++New-Label -Name "Confidential - Clinical" -DisplayName "Confidential – Clinical" ` -Tooltip "Confidential clinical content. Restricted to clinical staff." ` -Comment "Encryption scoped to the clinical function." ` -ContentType "File, Email" ` -EncryptionEnabled $true ` -EncryptionProtectionType "Template" ` -EncryptionRightsDefinitions "Operations@TenantName:VIEW,VIEWRIGHTSDATA,DOCEDIT,EDIT,PRINT,EXTRACT,REPLY,REPLYALL,FORWARD" ` -EncryptionOfflineAccessDays 7 ` -ApplyContentMarkingHeaderEnabled $true ` -ApplyContentMarkingHeaderText "Contoso Clinical – Confidential" ` -ApplyContentMarkingHeaderFontSize 10+++

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image22.png)

1. Create the `Restricted – Trial Data` label — the top tier for pre-publication trial results, with encryption scoped to the smallest authorized group and the strictest settings:

    +++New-Label -Name "Restricted - Trial Data" -DisplayName "Restricted – Trial Data" ` -Tooltip "Pre-publication trial results and material non-public information. Highest restriction." ` -Comment "Top tier. Encryption scoped to Leadership." ` -ContentType "File, Email" ` -EncryptionEnabled $true ` -EncryptionProtectionType "Template" ` -EncryptionRightsDefinitions "Leadership@TenantName:VIEW,VIEWRIGHTSDATA,DOCEDIT,EDIT,PRINT,REPLY,REPLYALL" ` -EncryptionOfflineAccessDays 0 ` -ApplyContentMarkingHeaderEnabled $true ` -ApplyContentMarkingHeaderText "RESTRICTED – TRIAL DATA" ` -ApplyContentMarkingHeaderFontSize 12 ` -ApplyContentMarkingFooterEnabled $true ` -ApplyContentMarkingFooterText "Material non-public information – do not distribute"+++

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image23.png)

1. Confirm all four labels exist and review their encryption status. Confirm `EncryptionEnabled` is `True` for the three protected tiers and `False` or blank for `General – Internal`:

    `Get-Label | Format-Table DisplayName, Name, EncryptionEnabled, ContentType`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image24.png)

    > [!Note]
    > The group names in the encryption rights (`Operations@TenantName`, `Leadership@TenantName`) map to Contoso's clinical and leadership functions in the tenant. Newly created labels can take up to 24 hours to fully replicate to all apps and services, though they appear in PowerShell immediately.

    You have successfully built the remaining three tiers, completing the four-label `Contoso Data Classification` taxonomy.


### Task 4 – Publish the labels with a label policy

Labels are invisible to users until a policy publishes them. In this task, you'll create and configure the publishing policy with PowerShell, scoping the labels to all staff, setting a default label, and requiring justification when a user lowers a classification.

1. In the elevated terminal, still connected to Security & Compliance PowerShell, create the label policy and publish all four labels to all staff:

    ```powershell
    New-LabelPolicy -Name "Contoso Data Classification policy" `
      -Labels "General - Internal","Confidential - Clinical","Highly Confidential - Research","Restricted - Trial Data" `
      -ExchangeLocation "All"
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image25.png)

1. Configure the policy: set `General – Internal` as the default label and require justification to lower a label:

    ```powershell
    Set-LabelPolicy -Identity "Contoso Data Classification policy" `
      -AdvancedSettings @{ requiredowngradejustification = "true"; defaultlabelid = (Get-Label -Identity "General - Internal").Guid }
    ```

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image26.png)

1. Confirm the policy exists and lists the four labels:

    `Get-LabelPolicy -Identity "Contoso Data Classification policy" | Format-List Name, Labels, ExchangeLocation`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image27.png)

    > [!Important]
    > Allow up to 24 hours for the label policy to propagate before the labels appear in users' Office apps. In some cases this completes within an hour, but do not troubleshoot missing labels until the 24-hour window has passed. This timing is indicative, not guaranteed.

    You have successfully published the four-label taxonomy to all staff, with a default label and mandatory downgrade justification.


### Task 5 – Configure client-side auto-labeling

There are two distinct ways to apply labels automatically, and this task covers the first: client-side auto-labeling, which runs inside the Office apps (Word, Excel, PowerPoint, Outlook) and recommends or applies a label as the user creates or edits content. In this task, you'll configure the `Highly Confidential – Research` label to recommend itself when a user's document contains a Contoso compound identifier.

1. In **Microsoft Edge**, in the Microsoft Purview portal, select **Solutions** > **Information Protection** > **Sensitivity labels**.

1. Select the **Highly Confidential – Research** label under **Contoso Data Classification**, then select **Edit label**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image28.png)

1. Select **Next** through the wizard until you reach the **Auto-labeling for files and emails** page.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image29.png)

1. Select the toggle to turn on **Auto-labeling for files and emails**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image30.png)

1. Select **+ Add condition**, then select **Content contains** > **Sensitive info types**. Search for and select **Contoso Compound ID** (the classifier from Lab 2), then select **Add**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image31.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image32.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image33.png)

1. Under the labeling behavior, select **Recommend that users apply the label** (rather than apply automatically). In the policy tip text box, enter +++This document appears to contain a Contoso compound identifier. Apply the Highly Confidential – Research label to protect it.+++

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image34.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image35.png)

1. Select **Next** through the remaining pages, then on the review page select **Save label**, and select **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image36.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image37.png)

    > [!Note]
    > Recommending the label first, rather than applying it silently, is the Microsoft-recommended deployment pattern: run in recommendation mode to observe accuracy and false positives before switching the behavior to apply automatically. Client-side auto-labeling takes effect when users create or edit content in the Office apps after the setting propagates, which can take up to 24 hours. This timing is indicative, not guaranteed.

    You have successfully configured client-side auto-labeling so the research label is recommended when compound identifiers are present in Office documents.


### Task 6 – Configure service-side auto-labeling

The second method, service-side auto-labeling, is different: it runs in the service, scanning existing content at rest in SharePoint, OneDrive, and Exchange and applying labels to content that already exists — including content created before labels were deployed. In this task, you'll create a service-side auto-labeling policy that applies `Highly Confidential – Research` to content matching the Compound ID SIT or the trial-subject EDM classifier, running it in simulation first.

1. In the Microsoft Purview portal, select **Solutions** > **Information Protection** > **Policies** > **Auto-labeling policies**.

1. On the **Auto-labeling** page, select **+ Create auto-labeling policy**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image38.png)

1. On the **What type of auto-labeling policy do you want to create?** dialogue-box, choose **Automatically apply labels only**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image39.png)

1. On the **Choose info you want this label applied to** page, select **Custom** > **Custom policy**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image40.png)

1. On the **Name your auto-labeling policy** page, enter the following, then select **Next**:

    - **Name**:

        `Auto-label research IP at rest`

    - **Description**:

        `Applies Highly Confidential – Research to stored content containing Contoso compound IDs or exact trial-subject records.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image41.png)


1. On the **Choose a label to auto-apply** page, select **+ Choose a label**. From the **Choose a sensitivity label** pane, select **Contoso Data Classification/Highly Confidential – Research**  and choose **Add**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image42.png)

1. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image43.png)

1. On the **Assign admin units** page, select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image44.png)

1. On the **Choose locations** page, enable **SharePoint sites**, **OneDrive accounts**, and **Exchange email**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image45.png)

1. On the **Set up common or advanced rules** page, select **Common rules**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image46.png)

1. On the rules page, select **+ New rule**, name it `Research IP match`, then select **+ Add condition** > **Content contains** > **Sensitive info types**. Search for and select **Contoso Compound ID** and **Contoso Clinical Trial Subjects**, set the logic to **Any of these**, then select **Save** and **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image47.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image48.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image49.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image50.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image51.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image52.png)

1. On the additional-settings page, leave the defaults and select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image53.png)

1. On the policy-mode page, select **Run policy in simulation mode**, select the checkbox for **Automatically turn on policy if not modified after 7 days in simulation**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image54.png)

1. On the review page, select **Create policy**, then select **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image55.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image56.png)

1. On the **Auto-labeling** page, select the **Auto-label research IP at rest** policy and confirm its status shows **In simulation**.

    > [!Note]
    > Service-side auto-labeling evaluates existing content on a schedule, so simulation results are not immediate — allow several hours, and up to 24–48 hours for a first pass over existing SharePoint and OneDrive content. Always review simulation results to confirm accuracy before letting the policy turn on. This is the key difference from client-side labeling, which acts on content as users edit it. These timings are indicative, not guaranteed.

    You have successfully configured service-side auto-labeling in simulation, applying the research label to matching content at rest.


### Task 7 – Apply the label and prove encryption denies unauthorized access

A label that claims to encrypt is only trustworthy if unauthorized access is actually denied. In this task, you'll apply `Highly Confidential – Research` to the provided drug-IP document, then prove the protection: an authorized research user can open it, and an unauthorized user cannot.

1. Sign in to the client VM (or a browser session) and open `https://word.cloud.microsoft/` in a browser as **Lynne Robbins** (`LynneR@TenantName`), a research user authorized by the label. Lynne Robbins's password is provided in the Resources tab.

1. Upload the provided `CX-2087 Formulation Process.docx` file from **C:\Lab Files** in **Microsoft Word**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image57.png)

1. On the ribbon, select the **Sensitivity** button, then select **Highly Confidential – Research**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image58.png)

1. If prompted to justify, select **Other** and then add a comment `This is a confidential file`. Then select **Change**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image59.png)

1. Confirm the label is applied: the **Sensitivity** button shows **Highly Confidential – Research**, the header reads **Contoso Research – Restricted**, the footer reads **Do not distribute**, and a dynamic watermark showing Lynne Robbins's UPN and a timestamp appears. Save and close the document.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image60.png)

1. Still as Lynne Robbins (authorized), re-open the document and confirm it opens with no access prompt and the content is fully readable. This confirms authorized access works.

1. Now prove that an unauthorized user is denied. Select **Share** > **Share** from the right hand top corner.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image61.png)

1. Search for and select **Grady Archie**. Then select **Send**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image62.png)

1. Sign in to Outlook at `https://outlook.cloud.microsoft/mail/` as **Grady Archie** (`GradyA@TenantName`), a user who is **not** in the research group the label authorizes. User's password is provided in the Resources tab.

1. Select the mail from **Lynne Robbins** and select **Open**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image63.png)

1. Confirm access is **denied**: Word states that Grady does not have permission to open the document because it is protected by the `Highly Confidential – Research` label, and the content is not shown. This is the proof that the encryption enforces access control, not merely marking.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-04/media/image64.png)

    > [!Note]
    > If a second-user sign-in isn't available in your environment, verify protection through step 5 together with the scoped `EncryptionRightsDefinitions` output shown in the Script notes: the applied label, the dynamic watermark showing the viewer's identity, and the scoped `EncryptionRightsDefinitions` confirm only the listed identities can decrypt. The behavioral denial in steps 7–11 is the stronger proof where a second user is available. Newly applied encryption can take a few minutes to take effect for a user.

    You have successfully proven that the label encrypts the document and denies access to unauthorized users while permitting authorized research staff.


## Summary

In this lab, you built Contoso Pharmaceuticals' four-tier sensitivity-label taxonomy inside the `Contoso Data Classification` group — creating the crown-jewel `Highly Confidential – Research` label with scoped encryption, content marking, and dynamic watermarking in the portal, and the `General – Internal`, `Confidential – Clinical`, and `Restricted – Trial Data` tiers with PowerShell. You published the taxonomy with a policy, then configured both methods of automatic labeling: client-side labeling that recommends the research label in Office apps, and service-side labeling that applies it to matching content at rest, both driven by the classifiers from Lab 2. You proved the encryption denies unauthorized access while permitting authorized research staff. These labels are the protection layer that the DLP, insider-risk, Fabric, and AI labs build on.

## Script notes

*Plain-English explanations of every command used in this lab, for verification by a non-technical reader. The code itself lives in the task steps; this section only explains it.*

### Task 3 — creating labels with PowerShell

```powershell
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName AllanD@TenantName
```

- **What it does:** Loads the management toolset and signs you in to Security & Compliance PowerShell, where labels are managed.
- **To substitute:** replace `TenantName` with the tenant name from the Resources tab. Sign in as Allan Deyoung when the window appears.
- **What you should see:** the prompt returns with no red error text.

```powershell
New-Label -Name "General - Internal" -DisplayName "General – Internal" `
  -Tooltip "..." -Comment "..." -ContentType "File, Email" `
  -ApplyContentMarkingFooterEnabled $true `
  -ApplyContentMarkingFooterText "Contoso Internal" `
  -ApplyContentMarkingFooterFontSize 10
```

- **What it does:** Creates a sensitivity label. `New-Label` is the command; each `-Parameter` sets one aspect.
- **The parameters, in plain English:** `-Name` is the internal name; `-DisplayName` is what users see (it can contain the en-dash "–"). `-Tooltip` is the user hover text; `-Comment` is an admin-only note. `-ContentType "File, Email"` means it applies to documents and emails. The `ApplyContentMarking…` parameters add a footer with the given text and size. This label has no encryption parameters, so it only marks content.
- **The backtick `` ` `` at line ends** is PowerShell's line-continuation character — it lets one long command span several lines. It runs as a single command.
- **To substitute:** nothing for the lab.
- **What you should see:** the new label's details with no red error text.


+++New-Label -Name "Confidential - Clinical" ... ` -EncryptionEnabled $true ` -EncryptionProtectionType "Template" ` -EncryptionRightsDefinitions "Operations@TenantName:VIEW,VIEWRIGHTSDATA,DOCEDIT,EDIT,PRINT,EXTRACT,REPLY,REPLYALL,FORWARD" ` -EncryptionOfflineAccessDays 7 ...+++

- **What the encryption parameters mean:** `-EncryptionEnabled $true` turns encryption on. `-EncryptionProtectionType "Template"` means the label carries a fixed set of permissions you define here. `-EncryptionRightsDefinitions` lists **who** can do **what**, in the form `identity:rights` — here the `Operations` group is granted view, edit, print, copy, and reply/forward rights. Anyone not listed cannot decrypt the content. `-EncryptionOfflineAccessDays 7` allows an authorized user to open the content offline for up to 7 days before reconnecting.
- **To substitute:** replace `TenantName` so the group address resolves (for example `Operations@contoso.onmicrosoft.com`). The `Restricted – Trial Data` label uses the same parameters with a smaller group (`Leadership`) and `-EncryptionOfflineAccessDays 0` (no offline access — strictest).
- **What you should see:** the label's details with no error.


`Get-Label | Format-Table DisplayName, Name, EncryptionEnabled, ContentType`

- **What it does:** Lists every label with its display name, internal name, whether encryption is on, and where it applies.
- **What you should see:** all four Contoso labels, `EncryptionEnabled` `True` for the three protected tiers and `False`/blank for `General – Internal`.


### Task 4 — publishing labels with a policy

```powershell
New-LabelPolicy -Name "Contoso Data Classification policy" `
  -Labels "General - Internal","Confidential - Clinical","Highly Confidential - Research","Restricted - Trial Data" `
  -ExchangeLocation "All"
```

- **What it does:** Creates the policy that makes labels visible to users and publishes all four (listed by internal name). `-ExchangeLocation "All"` publishes them to all mailboxes.
- **What you should see:** the new policy's details with no error.

```powershell
Set-LabelPolicy -Identity "Contoso Data Classification policy" `
  -AdvancedSettings @{ requiredowngradejustification = "true"; defaultlabelid = (Get-Label -Identity "General - Internal").Guid }
```

- **What it does:** Adjusts the policy's behavior. `requiredowngradejustification = "true"` forces users to give a reason when lowering a label. `defaultlabelid = ...` sets the default label for new content — the `(Get-Label -Identity "General - Internal").Guid` piece looks up that label's unique ID and uses it (labels are referenced by ID here to avoid ambiguity).
- **`@{ key = value; key = value }`** is PowerShell's way of passing several settings as one set of key/value pairs.
- **What you should see:** the command completes with no error.


`Get-LabelPolicy -Identity "Contoso Data Classification policy" | Format-List Name, Labels, ExchangeLocation`

- **What it does:** Displays the policy so you can confirm its name, the labels it publishes, and its location.
- **What you should see:** the policy name, all four labels, and `ExchangeLocation` of `All`.


### Task 7 — inspecting label encryption

`Get-Label -Identity "Highly Confidential - Research" | Format-List DisplayName, EncryptionEnabled, EncryptionProtectionType, EncryptionRightsDefinitions`

- **What it does:** Shows the encryption configuration of the research label so you can confirm the scoped rights that produced the denial in Task 7.
- **What you should see:** `EncryptionEnabled : True` and an `EncryptionRightsDefinitions` value listing the research identities — and not Finance or Pradeep Gupta, which is why he was denied.
- **To substitute:** nothing needs changing.
