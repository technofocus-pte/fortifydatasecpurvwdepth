<!--
lab:
  title: Lab 13 — Meet regulatory retention and records obligations with retention labels and policies, auto-apply policies, file plan and records management, event-based retention, disposition review, and retention precedence
  description: In this lab we implemented the full retention and records lifecycle, including retention labels, auto-apply policies, records management, event-based retention, and disposition review.
  duration: 30 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Data Lifecycle Management
-->

# Lab 13 — Meet regulatory retention and records obligations with retention labels and policies, auto-apply policies, file plan and records management, event-based retention, disposition review, and retention precedence

Contoso Pharmaceuticals must keep some data for years and delete other data promptly, and getting either wrong creates risk. Clinical-trial records must be retained for a regulatory period after a study closes (FDA 21 CFR Part 11 and GxP obligations), declared as unalterable records, and disposed of only after documented review. Routine content should be deleted on schedule to limit exposure. Microsoft Purview's retention and records management capabilities enforce all of this. In this lab, acting as Allan Deyoung, you'll build the full retention lifecycle: retention labels that retain and delete, auto-apply policies driven by Contoso's classifiers, records declared through a file plan, retention that starts when a study closes, disposition review before regulated records are deleted, and the precedence rules that decide what wins when policies overlap.

This is the most comprehensive lab in the course. It reuses the classifiers from Lab 2 and reflects how a regulated pharmaceutical company actually manages the lifecycle of its records.

**Learning outcomes.** After this lab you can:
- Create retention labels that retain then delete, and that retain then trigger disposition review.
- Publish retention labels and auto-apply them using sensitive information types.
- Create static and adaptive-scope retention policies.
- Use file plan and declare content as records.
- Configure event-based retention that starts when a study closes.
- Conduct a disposition review, and explain retention precedence.


**Tasks**:

1. Create a retention label for trial records
1. Publish the retention label
1. Auto-apply a retention label using Contoso classifiers
1. Create a static retention policy for Teams
1. Create an adaptive scope and adaptive retention policy
1. Declare records using a file plan
1. Configure event-based retention for study closure
1. Conduct a disposition review
1. Understand retention precedence
1. Recover deleted SharePoint content


### Task 1 – Create a retention label for trial records

In this task, you'll create a retention label for clinical-trial records that must be retained for a regulatory period. You'll configure it to retain then delete; a records-declaring label with disposition review is created later.

1. In **Microsoft Edge**, navigate to +++https://purview.microsoft.com+++ and sign in as **Allan Deyoung**, `AllanD@TenantName` (the Tenant Name and password are provided in the Resources tab).

1. Select **Solutions** > **Data Lifecycle Management**, then select **Retention labels**.

1. On the **Labels** page, select **Create a label**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image1.png)

1. On the **Name your retention label** page, enter:

    - **Name**:

        `Clinical Trial Records`

    - **Description for users**:

        `Use for clinical-trial records that must be retained to meet regulatory obligations.`

    - **Description for admins**:

        `Retains clinical-trial records for the regulatory period, then deletes them.`


1. Select **Next**. On the **Define label settings** page, select **Retain items forever or for a specific period**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image2.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image3.png)

1. On the **Define the period** page, set **How long is the period?** to **7 Years**, and **When should the period begin?** to **When items were created**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image4.png)

1. On the **Choose what happens after the retention period** page, select **Delete items automatically**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image5.png)

1. On the **Review and finish** page, select **Create label**. On the confirmation page, select **Do nothing**, then select **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image6.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image7.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image8.png)

    > [!Note]
    > This label retains content for a fixed period and then deletes it automatically — appropriate for records where unattended disposal is acceptable. Later in this lab you create a second label that routes regulated records to a human reviewer instead of deleting them automatically. Retaining from creation, rather than last modification, is common for records that must be kept for a set time regardless of edits.

    You have successfully created a retention label for clinical-trial records.


### Task 2 – Publish the retention label

Publishing makes a retention label available for users to apply manually across Microsoft 365. In this task, you'll publish the label to Exchange, SharePoint, and OneDrive.

1. In Microsoft Purview, on the **Retention labels** page, select the checkbox next to **Clinical Trial Records**, then select **Publish labels**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image9.png)

1. On the **Choose labels to publish** page, verify **Clinical Trial Records** is selected, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image10.png)

1. On the **Policy scope** page, select **Next**. On the **Choose the type of retention policy to create** page, select **Static**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image11.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image12.png)

1. On the **Choose where to publish labels** page, select **Let me choose specific locations**, enable **Exchange mailboxes**, **SharePoint classic and communication sites**, and **OneDrive accounts**, and deselect all other locations. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image13.png)

1. On the **Name your policy** page, enter:

    - **Name**:

        `Publish Clinical Trial Records label`

    - **Description**:

        `Makes the Clinical Trial Records label available in Exchange, SharePoint, and OneDrive.`


1. Select **Next**, then **Submit**, then **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image14.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image15.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image16.png)

    > [!Note]
    > A label policy makes the label selectable by users; it does not by itself apply the label to any content. Allow up to 24 hours (typically up to 7 days for a first publish) for the label to appear for users. This timing is indicative, not guaranteed.

    You have successfully published the retention label.


### Task 3 – Auto-apply a retention label using Contoso classifiers

Relying on users to label every record is unreliable, so you'll auto-apply the label to content that contains Contoso's regulated data. In this task, you'll create an auto-apply policy driven by the classifiers from Lab 2.

1. In Microsoft Purview, select **Data Lifecycle Management** > **Policies** > **Label policies**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image17.png)

1. On the **Label policies** page, select **Auto-apply a label**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image18.png)

1. On the **Let's get started** page, enter:

    - **Name**:

        `Auto-apply Clinical Trial Records`

    - **Description**:

        `Applies the Clinical Trial Records label to content containing Contoso trial identifiers.`


1. Select **Next**. On the **Choose the type of content you want to apply this label to** page, select **Apply label to content that contains sensitive info**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image19.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image20.png)

1. On the **Content that contains sensitive info** page, instead of a built-in regulation, select **Custom** > **Custom policy** > **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image21.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image22.png)

1. On the **Define content that contains sensitive info** page, select **Add** > **Sensitive info types**, select **Contoso Clinical Trial Subject ID** and **Contoso Clinical Trial Subjects (EDM)** — then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image23.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image24.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image25.png)

1. On the **Policy scope** page, select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image26.png)

1. On the **Choose the type of retention policy to create** page, select **Static**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image27.png)

1. On the **Choose where to apply the label** page, select **Let me choose specific locations**, enable **Exchange mailboxes**, **SharePoint classic and communication sites**, and **OneDrive accounts**, and deselect the rest. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image28.png)

1. On the **Choose a label to auto-apply** page, select **Add label**, select **Clinical Trial Records**, then select **Add**, then **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image29.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image30.png)

1. On the **Decide whether to test or run your policy** page, select **Test the policy before running it**, then select **Next**, **Submit**, and **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image31.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image32.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image33.png)

    > [!Note]
    > Auto-apply using Contoso's own sensitive information types is more precise than a generic regulation template, because it targets exactly Contoso's trial identifiers. Running in test mode first lets you confirm what the policy would label before it acts. Auto-apply evaluates existing content on a schedule and can take up to seven days to complete a first pass. This timing is indicative, not guaranteed.

    You have successfully created an auto-apply retention policy driven by Contoso's classifiers.


### Task 4 – Create a static retention policy for Teams

Retention labels apply to documents and emails, but Teams messages are retained through a retention policy. In this task, you'll create a static retention policy for Teams content.

1. In Microsoft Purview, select **Data Lifecycle Management** > **Policies** > **Retention policies**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image34.png)

1. Select **New retention policy**. On the **Name your retention policy** page, enter:

    - **Name**:

        `Teams Retention`

    - **Description**:

        `Retains Teams chats and channel messages for three years, then deletes them.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image35.png)


1. Select **Next**. On the **Policy scope** page, select **Next**. On the **Choose the type of retention policy to create** page, select **Static**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image36.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image37.png)

1. On the **Choose locations to apply the policy** page, enable **Teams channel messages** and **Teams chats**, and leave all other locations disabled. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image38.png)

1. On the **Decide if you want to retain content, delete it, or both** page, select **Retain items for a specific period**, choose **Custom** and set the period to **3 years**, set **Start the retention period based on** to **When items were last modified**, and set **At the end of the retention period** to **Delete items automatically**. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image39.png)

1. Select **Submit**, then **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image40.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image41.png)

    You have successfully created a static retention policy for Teams content.


### Task 5 – Create an adaptive scope and adaptive retention policy

Static policies apply to fixed locations; adaptive scopes target content dynamically based on attributes, so the policy stays current as the organization changes. In this task, you'll create an adaptive scope for privileged groups and a retention policy that uses it.

1. In Microsoft Purview, select **Settings** > **Roles and scopes** > **Adaptive scopes**, then select **+ Create scope**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image42.png)

1. On the **Name your adaptive policy scope** page, enter:

    - **Name**:

        `Leadership and Research Groups`

    - **Description**:

        `Targets Leadership and Research M365 groups that handle sensitive Contoso data.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image43.png)


1. Select **Next**. On the **Assign admin unit** page, select **Next**. On the **What type of scope do you want to create?** page, select **Microsoft 365 Groups**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image44.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image45.png)

1. On the **Create the query to define users** page, select the **Attribute** dropdown and select **Name**, leave **is equal to**, and enter `Leadership` as the value.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image46.png)

1. Select **+ Add attribute**. Change the operator from **And** to **Or**, select the **Attribute** dropdown and select **Name**, leave **is equal to**, and enter `Research` as the value. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image47.png)

1. On the **Review and finish** page, select **Submit**, then **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image48.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image49.png)

1. Now create the policy. Select **Data Lifecycle Management** > **Policies** > **Retention policies**, then **+ New retention policy**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image50.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image51.png)

1. On the **Name your retention policy** page, enter:

    - **Name**:

        `Privileged Group Retention`

    - **Description**:

        `Retains content from Leadership and Research groups for five years.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image52.png)


1. Select **Next**. On the **Policy scope** page, select **Next**. On the **Choose the type of retention policy to create** page, select **Adaptive**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image53.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image54.png)

1. On the **Choose adaptive policy scopes and locations** page, select **+ Add scopes**, select **Leadership and Research Groups**, then select **Add**. Enable **Microsoft 365 Group mailboxes & sites**, and leave other locations disabled. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image55.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image56.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image57.png)

1. On the retention configuration page, select **Retain items for a specific period**, choose **5 years**, set **Start the retention period based on** to **When items were last modified**, and set the end action to **Delete items automatically**. Select **Next**, **Submit**, then **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image58.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image59.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image60.png)

    > [!Note]
    > An adaptive scope re-evaluates its membership query on a schedule, so a policy scoped to "Research groups" automatically covers new research groups without editing the policy — unlike a static policy, whose locations are fixed at creation. This makes adaptive scopes the better choice for dynamic, attribute-based targeting. This timing is indicative, not guaranteed.

    You have successfully created an adaptive scope and an adaptive retention policy.


### Task 6 – Declare records using a file plan

Regulated records need more than retention — they must be declared as records so they can't be altered or deleted, and managed at scale through a file plan. In this task, you'll use the file plan to create a records label and review its descriptors.

1. In Microsoft Purview, select **Solutions** > **Records Management**, then select **File plan**.

1. On the **File plan** page, review the existing retention labels shown, then select **Create a label** to create a records label directly in the file plan.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image61.png)

1. On the **Name your retention label** page, enter:

    - **Name**:

        `Regulatory Submission Record`

    - **Description for admins**:

        `Declares regulatory submission documents as records, retained for the regulatory period.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image62.png)


1. Select **Next**. On the **File plan descriptors** page, you can set the optional descriptors that help manage records at scale — for example, a **Reference ID**, **Business function/department** (Regulatory Affairs), **Category**, and **Provision/citation** (the regulation) — for now select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image63.png)

    > [!Note]
    > File plan descriptors are metadata that make a large label taxonomy searchable and auditable — a records manager can filter by department, citation, or category. The file plan also lets you bulk-create labels by importing a spreadsheet and export existing labels for analysis, which is how records teams manage hundreds of labels.

1. On the **Define label settings** page, select **Retain items forever or for a specific period**, then set the period (for example, **10 Years** from when items were created). Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image64.png)

1. On the **Choose what happens during the retention period**, select **Mark items as a record**. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image65.png)

1. On the **Choose what happens after the retention period** page, select **Start a disposition review** (rather than delete automatically), which you'll use in Task 8. Select **+ Create stages and assign reviewers**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image66.png)

1. Select **Add a stage**. Name it as `Review 1` and then select **OK**. In the reviewers field, select **Megan Bowen** and then select **OK**. Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image67.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image68.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image69.png)

1. On the **Review and finish** page, select **Create label**, then **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image70.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image71.png)

    > [!Important]
    > Once an item is declared a record, it can't be edited or deleted for the retention period (in SharePoint and OneDrive, versioning still lets you work on a new version). A **regulatory record** is irreversible and even an administrator can't remove the marking — so this lab uses the standard record option. Managing record labels requires the Records Management role.

    You have successfully declared a records label through the file plan.


### Task 7 – Configure event-based retention for study closure

Clinical-trial records aren't retained from a fixed date — they must be kept for a period *after the study closes*, which is different for every study. Event-based retention handles this. In this task, you'll create an event-based label whose retention clock starts when a study-closure event is triggered.

1. In Microsoft Purview, select **Solutions** > **Records Management** > **File plan** (or **Data Lifecycle Management** > **Retention labels**), then select **Create a label**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image72.png)

1. On the **Name your retention label** page, enter:

    - **Name**:

        `Trial Records - Post-Closure`

    - **Description for admins**:

        `Retains trial records for the regulatory period after study closure, then routes to disposition review.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image73.png)


1. Select **Next**. On **Define file plan descriptors for this label**, select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image74.png)

1. On the **Define label settings** page, select **Retain items forever or for a specific period**, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image75.png)

1. On the **Define the period** page, set the period (for example, **7 Years**). For **Start the retention period based on**, select **Create new event type**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image76.png)

1. For the event type, enter a name such as `Study Closure`, then select **Next**, **Submit**, and **Done**. Back on the **Define the period** page, select the **Study Closure** event type in the **Start the retention period based on** dropdown.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image77.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image78.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image79.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image80.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image81.png)

1. Select the option to **Mark items as a record** (event-based retention is typically used for records), then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image82.png)

1. On the **Choose what happens after the retention period** page, select **Delete items automatically**, then select **Next**. Review and create the label.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image83.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image84.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-13/media/image85.png)

1. Understand how the event is later triggered: when a study actually closes, a records manager selects **Records Management** > **Events**, creates an event of type **Study Closure**, and provides the **asset ID** (or keyword/query) that ties the event to the labeled records — which starts the retention clock for exactly those records.

    > [!Important]
    > After you choose an event type and save the label, the event type can't be changed. The retention period does not begin until the matching event is created and triggered with the correct asset ID, so labeled records are retained indefinitely until closure occurs. This is exactly the behavior regulated trial records require. These timings are indicative, not guaranteed.

    You have successfully configured event-based retention that starts at study closure.


### Task 8 – Conduct a disposition review (Read-Only)

When regulated records reach the end of retention, they should be reviewed by a person before deletion — providing documented proof of disposition. In this task, you'll review how the disposition workflow operates and act on the disposition queue. In this lab, you will not be able to perform this task due to the time and environment constraints as you will not see the disposition reviews yet.

1. In Microsoft Purview, select **Solutions** > **Records Management** > **Disposition**.

1. Review the **Disposition** page, which lists items pending review — content whose retention period has ended for labels configured with **Start a disposition review** (such as the labels from Tasks 6 and 7).

1. Select a pending item to open its disposition review. As a reviewer, review the item's details, then choose one of the disposition actions:

    - **Approve disposal** — confirm the item can be permanently deleted, creating a record of disposition.
    - **Relabel** — apply a different retention label (for example, to extend retention).
    - **Extend the retention period** — keep the item longer, with justification.


1. Understand multi-stage review: a records label can require **multiple review stages** — for example, a Records Manager confirms eligibility, a Business Owner confirms no ongoing need, and Legal gives final sign-off. Each stage's reviewers are notified and their actions are logged for the audit trail. Multi-stage review is configured on the label in the Microsoft Purview portal.

1. Note that all disposition actions are recorded, and information about disposed items can be exported — this documented proof of disposition is what regulators and auditors require.

    > [!Note]
    > Disposition reviewers should be content owners or compliance officers who understand the regulatory context, not IT administrators — they need the business context to decide whether an item can be disposed. Items appear in the disposition queue only after their retention period actually elapses, so a live queue depends on content having reached end-of-retention. This timing is indicative, not guaranteed.

    You have successfully reviewed and acted on the disposition workflow.


### Task 9 – Understand retention precedence

Content is often covered by more than one retention setting, and the outcome is decided by precedence rules. In this task, you'll review the principles that determine what wins.

1. Understand the four principles of retention precedence, applied in order when multiple retention labels or policies affect the same content:

    - **Retention wins over deletion.** If one setting says delete and another says retain, the content is retained — nothing is deleted while any policy still requires retention. (Applied first.)
    - **Longest retention period wins.** When content must be retained by multiple settings, it's kept for the longest of the periods.
    - **Explicit wins over implicit.** A retention label applied directly to an item (explicit) takes precedence over a policy applied to a location (implicit) for the *deletion* decision.
    - **Shortest deletion period wins.** Among settings that only delete (after retention is satisfied), the shortest deletion timeline applies.


1. Apply the principles to a Contoso example: a trial document is covered by the 7-year `Clinical Trial Records` label and also sits in a location under the 3-year `Privileged Group Retention` policy. Because retention wins over deletion and the longest period wins, the document is retained for 7 years, not deleted at 3.

1. Recognize why this matters for Contoso: precedence guarantees that a short-term deletion policy can never cause a regulated record to be destroyed early — the regulatory retention always takes precedence.

    You have successfully reviewed how retention precedence resolves overlapping policies.


### Task 10 – Recover deleted SharePoint content (Optional)

Retention preserves content even when a user deletes it. In this task, you'll confirm that a deleted SharePoint document can be recovered.

1. In **Microsoft Edge**, signed in as **Allan Deyoung**, select the app launcher (grid icon), select **More apps**, then select **SharePoint**.

1. On the SharePoint landing page, search for a document library you can use for testing (for example, a team or project site), and open it.

1. In the site, select **Documents**. Select the checkbox for a test document, then select **Delete** from the action bar, and confirm the deletion.

1. In the left sidebar, select **Recycle bin**. Locate the deleted document, right-click it, and select **Restore**.

1. Select **Documents** again and confirm the file has been restored.

    > [!Note]
    > Because retention preserves content behind the scenes, even a user's deletion doesn't permanently remove content that's under a retention policy — a preserved copy is kept, and routine deletions can be restored from the recycle bin. This is the safety net that retention provides against accidental or malicious deletion. This timing is indicative, not guaranteed.

    You have successfully recovered a deleted SharePoint document.


## Summary

In this lab, you implemented Contoso Pharmaceuticals' complete retention and records lifecycle. You created retention labels that retain then delete, and — for regulated records — retain then route to disposition review. You published a label for manual use and auto-applied one using Contoso's own trial classifiers from Lab 2. You built static and adaptive-scope retention policies, then moved into records management: declaring content as records through a file plan with descriptors, and configuring event-based retention whose clock starts only when a study closes, exactly as regulated trial records require. You reviewed the disposition workflow — including multi-stage review and documented proof of disposition — and the precedence rules that guarantee a short-term deletion policy can never destroy a regulated record early. Finally, you confirmed that retention preserves content against deletion. Together these controls let Contoso meet its FDA and GxP retention obligations while limiting unnecessary data, with the auditable records governance a regulated pharmaceutical company requires.
