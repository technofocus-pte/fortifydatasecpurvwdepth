---
lab:
  title: Lab 16 — Create a DLP policy that blocks external access to a Microsoft Fabric workspace
  description: In this lab we created a custom data loss prevention policy to detect sensitive data in Fabric and Power BI content and block external user access, and ran it in simulation mode.
  duration: 15 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Microsoft Fabric
---

# Lab 16 — Create a DLP policy that blocks external access to a Microsoft Fabric workspace

## Introduction

Contoso Pharmaceuticals handles regulated payment and financial data belonging to its customers and partners, and some of that data flows into Microsoft Fabric and Power BI as reports and semantic models. Contoso needs to block external users from reaching Fabric content that contains this payment data, notify the compliance admin whenever a semantic model is blocked and the data owner that a restriction took place, and make internal users aware — through a policy tip — that the data is sensitive and must not be shared outside the organization. In this lab, acting as Allan Deyoung, you'll build a custom Data Loss Prevention (DLP) policy in Microsoft Purview that detects payment-card data in Fabric and Power BI content and restricts external access to it.

The following table maps Contoso's requirement to the DLP configuration you'll build in this lab.

| **Statement** | **Configuration question answered and configuration mapping** |
| ---  | --- |
|"We need to block external users..."           |       Where to monitor: **Fabric and Power BI**. Administrative scope: **Full directory**. Action: **Restrict access or encrypt the content in Microsoft 365 locations > Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files, and Power BI items > Block only people outside your organization**|
|"...from reports containing payment-card numbers..."| What to monitor: use the **Custom template**. Conditions for match: edit it to add the **Credit Card Number** sensitive info type.|
| "We want to notify the compliance admin to know whenever a semantic model is blocked..."|Incident reports: **Send an alert to admins when a rule match occurs: On**. Send an alert every time an activity matches the rule: **selected**|
| "...the data owner to be aware the restriction took place. We also want internal users to be aware that the data is sensitive and that they shouldn't share it outside the organization."| User notifications: **On**. Microsoft 365 files and Microsoft Fabric items: Notify users in Office 365 service with a policy tip or email notifications: **selected**. Policy tips: Customize the policy tip text: selected. Add text in the text box explaining the rules governing sharing of sensitive data.|

> [!IMPORTANT]
> For the purposes of this policy-creation procedure, you'll accept the default include/exclude values and leave the policy in simulation mode. You'll change these when you deploy the policy. This lab requires a Microsoft Fabric capacity, and — as noted at the end of the lab — the external-access block action has additional licensing requirements that a Power BI Pro license doesn't meet.

## Objective

- Create a custom Data Loss Prevention (DLP) policy in Microsoft Purview to block external user access to Fabric and Power BI content containing sensitive information.

**Learning outcomes.** After this lab you can:

- Translate a data-protection intent into a Fabric DLP policy configuration.
- Create a custom DLP policy scoped to Fabric and Power BI.
- Add a sensitive-information-type condition and an external-access restriction action.
- Configure user notifications, user overrides, and admin alerts.
- Run a DLP policy in simulation mode, and explain the requirements to enforce the external-access block.

## Exercise 1: Creating a Custom DLP Policy to Block External Access to Fabric Workspaces

In this exercise, you'll create a custom DLP policy, scope it to Fabric and Power BI, add a rule that detects payment-card data and blocks external access, configure notifications and alerts, and run it in simulation mode.

1.  In the Microsoft Purview portal, click on **Solutions**, then navigate and click on **Data Loss Prevention**

    ![](./media/image1.png)

2.  Now, click on **Policies**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image2.png)

3.  In the **Policies** page, click on **+** **Create policy**.

    ![](./media/image3.png)

4.  From the **What info do you want to protect?** pane, select **Enterprise applications and devices**.

    ![](./media/image32.png)

5.  On the **Choose what type of data to protect** page, ensure that the **Data stored in connected sources** radio button is selected, then click on the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image4.png)

6.  On the **Start with a template or create a custom policy** page, click on **Custom** under **Categories**.

   Select **Custom policy** from the **Regulations** list, then click on the **Next** button.

    ![](./media/image5.png)

7.  On the **Name your DLP policy** page, in the **Name** field, ensure that **Custom policy** is mentioned.

    **Note**: You can use the policy intent statement here. Policies can't be renamed.

    Click on the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image6.png)

8.  In the **Assign Admin units** page, click on the **Next** button.

    ![](./media/image7.png)

9.  On the **Choose where to apply the policy** page, click on the **Next** button.

    ![](./media/image8.png)

10. On the **Define policy settings** page, ensure that the **Create or customize advanced DLP rules** radio button is selected. Then, click on the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image9.png)

11. In the **Customize advanced DLP rules** page, select **+ Create rule**.

    ![](./media/image10.png)

12. On the **Create rule** page, in the **Name** field, enter **+++Block external users access to Fabric workspace+++**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image11.png)

13. Under the **Conditions** section, select **Add condition** \> **Content contains** \> **Add** \> **Sensitive info types**.

    ![](./media/image12.png)

    ![](./media/image13.png)

14. In the **Sensitive info types** pane that appears on the right side, click inside the search bar, type **+++credit card number+++** and press the enter button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image14.png)

    ![](./media/image15.png)

15. Select the check box beside **Credit Card Number**, then click on the **Add** button.

    ![](./media/image16.png)

16. Under **Actions**, select **Add an action** \> **Restrict access or encrypt the content in Microsoft 365 locations**

    ![](./media/image17.png)

17. Ensure that the **Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files, and Power BI items** and **Block only people outside your organization** are selected.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image18.png)

18. Under **User notifications**, set the toggle to **On**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image19.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image20.png)

19. Select the **Notify users in Office 365 service with a policy tip or email notifications** check box and the **Customize the policy tip text** checkbox.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image21.png)

20. In the **User overrides** section, select the checkbox beside **Allow users to override policy restrictions in Fabric (including Power BI), Exchange, SharePoint, OneDrive, and Teams**, then navigate and select the checkbox beside **Override the rule automatically if they report it as a false positive**.

    ![](./media/image22.png)

21. Under **Incident reports**, set **Use this severity level in admin alerts and reports** to **High**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

    ![](./media/image24.png)

22. Make sure the **Send an alert to admins when a rule match occurs** toggle is set to **On**.

23. Make sure the **Send alert every time an activity matches the rule** radio button is selected.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image25.png)

24. Click on the **Save** button.

    ![](./media/image26.png)

25. Review the rule, then click on the **Next** button.

    ![](./media/image27.png)

26. Ensure that the **Run the policy in simulation mode** radio button and the **Show policy tips while in simulation mode** checkboxes are selected. Then, click on the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image28.png)

27. In the **Review and finish** page, click on the **Submit** button. After a few seconds, the policy will be successfully created.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image29.png)

    ![](./media/image30.png)

> [!IMPORTANT]
> **You may encounter the following error due to a licensing limitation in this lab environment.**
>
> ![](./media/image31.png)
>
> This lab is running under a Power BI Pro license, which does not support Microsoft Purview DLP integration for Fabric or Premium workspaces. As a result, DLP policy actions like "Block external users" can't be properly scoped, and the wizard fails with the following error:
>
> *To block only people outside your organization, you must select the condition 'Content is shared with people outside my organization'.*
>
> In a real-world enterprise environment, this issue will not occur if your tenant has:
>
> - Power BI Premium Per User (PPU) license
> - or a Microsoft Fabric capacity (F64 or larger)
>
> These licenses allow full DLP policy integration with Microsoft Fabric and Power BI, including support for block actions and proper condition scoping. Note also that the restrict-access action for Fabric semantic models and lakehouses has been rolling out through 2026 and, depending on your tenant, may still be in preview and may require pay-as-you-go billing for Fabric DLP.

## Summary

In this lab, you created a custom DLP policy in Microsoft Purview to protect Contoso Pharmaceuticals' Fabric and Power BI content by detecting sensitive payment-card data and applying restrictions to block external user access, with user notifications and admin alerts. You built the policy to the point of running it in simulation mode, and learned that enforcing the external-access block requires a Fabric capacity of F64 or larger, or a Power BI Premium Per User license — beyond the Power BI Pro license used in this lab environment. With the appropriate licensing in place, Contoso can move this policy from simulation to enforcement to keep regulated payment data from leaving the organization through its analytics estate.