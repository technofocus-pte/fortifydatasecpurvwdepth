# Lab 14 – Using DSPM for AI to secure your agents and AI apps

You are Patti Fernandez, the Information Security Administrator for Contoso Ltd. As AI tools like Microsoft Copilot become more integrated into daily workflows, your team has been asked to assess and improve protections around sensitive data. In this lab, you'll explore how Microsoft Purview DSPM for AI can help secure data interactions with AI tools through policy enforcement, risk detection, and exposure assessments.

**Tasks**:

- Use DSPM for AI to create a DLP policy for generative AI sites
- Create an insider risk policy to detect risky AI interactions
- Detect unethical behavior in AI apps
- Run a data assessment to detect unlabeled content

## Task 1 – Use DSPM for AI to create a DLP policy for generative AI sites

To reduce the risk of data loss through AI assistants, you'll start by creating a DLP policy using the Fortify your data security recommendation. This policy uses Adaptive Protection to restrict pasting or uploading sensitive data into AI tools like ChatGPT and Copilot in Edge, Chrome, and Firefox.

1. Sign into the VM as the admin.

1. In **Microsoft Edge**, navigate to ```https://purview.microsoft.com``` and sign in as **Patti Fernandez**, ```Pattif@TenantName```.

1. In Microsoft Purview, navigate to DSPM for AI by selecting **Solutions** > **DSPM for AI** > **Recommendations**	

   ![](./media/image1.png)
   ![](./media/image2.png)
   ![](./media/image3.png)

1. Select the **Fortify your data security** recommendation.

   ![](./media/image4.png)

1. In the **Data security for AI** flyout page, review the summary, then select **Create policies**. This creates a preconfigured DLP policy targeting generative AI sites.

   ![](./media/image5.png)

1. You will see the 'Block elevated risk users from pasting or uploading sensitive info on AI sites' policy created. Since the other 2 require pay-as-you-go capability they will not be created in this tenant.  Once the policy has been created, select **Policy details**.

   ![](./media/image6.png)

1. In the **Policy details** section, select **Edit policy in solution** to open the **Data Loss Prevention** solution in Microsoft Purview.

   ![](./media/image7.png)

1. Select **Next** until you reach the **Choose where to apply the policy** page.

   ![](./media/image8.png)

1. Confirm the policy is scoped to **Devices**. Select **Next**.

  ![](./media/image9.png)

1. On the **Customize advanced DLP rules** page, select the pencil icon next to **Block with override for elevated risk users** to view the rule.

  ![](./media/image10.png)

1. Review the configuration of the rule created by DSPM for AI:
   - Under **Conditions**, note the sensitive info types included and that the rule uses **Adaptive Protection** based on elevated risk.

     ![](./media/image11.png)
     ![](./media/image12.png)

   - Under **Actions**, for both the Upload and Paste activities, select **Edit** next to **Sensitive service domain group restriction(s)**.

     ![](./media/image13.png)

   - In the service domain group configuration, confirm that **Generative AI Websites** is set to **Block with override**.

     ![](./media/image14.png)

   - Select **Close** to close the panel.

     ![](./media/image15.png)

1. Select **Cancel** to exit the rule editor without changes.

  ![](./media/image16.png)

1. Back on the **Customize advanced DLP rules** page, select **Next**.

  ![](./media/image17.png)

1. On the **Policy mode** page, select **Turn the policy on if it's not edited within fifteen days of simulation**, then select **Next**.

  ![](./media/image18.png)

1. On the **Review and finish** page, select **Submit**, then select **Done**.

  ![](./media/image19.png)
  ![](./media/image20.png)

You've created a policy that blocks high-risk users from sharing sensitive data on generative AI sites and confirmed the policy configuration set by DSPM for AI.

You can similarly review the rest of the policies by selecting **Solutions** > **DSPM for AI** > **Recommendations**. If you have a pay-as-you-go capability in your own tenant or user ID you can continue with the next exercises
## Task 2 – Create an insider risk policy to detect risky AI interactions

Next, you'll create a policy that helps detect risky prompt behavior in Copilot.

1. In Microsoft Purview, navigate to **DSPM for AI** by selecting **Solutions** > **DSPM for AI** > **Recommendations**.

1. Select the **Detect risky interactions in AI apps (preview)** recommendation.

1. In the **Detect risky interactions in AI apps (preview)** flyout page, review the summary, then select **Create policy**.

1. Once the policy is created, select **View policy**.

1. In the **Policy details** section, select **Edit policy in solution** to open the **Insider Risk Management** area of Microsoft Purview.

1. On the **Policies** page, locate and select the **DSPM for AI - Detect risky AI usage** policy.

1. In the flyout, select **Edit policy** to review the full policy configuration.

1. On the **Choose a policy template** page, observe that the policy uses the **Risky AI usage (preview)** template.

1. Select **Next** until you reach the **Choose triggering event for this policy page**.
Confirm that the triggering event is **User account deleted from Microsoft Entra ID**, which signals potential offboarding-related risks that might precede or follow risky AI activity.

1. Select **Next**.

1. On the **Indicators** page, expand the indicator categories to review which signals are selected:

   - Browsed to generative AI websites
   - Received sensitive response from Copilot
   - Entered risky prompt in Copilot

1. Select **Next** until you reach the **Review and finish** page, then select **Cancel** to exit the editor without making changes.

You've created a policy that detects risky AI interactions, including prompts and responses, to help identify early signs of risky user behavior.

## Task 3 – Detect unethical behavior in AI apps

In this task, you'll create a policy in DSPM for AI to detect unethical or inappropriate behavior in Microsoft 365 Copilot and other AI applications.

1. In Microsoft Purview, go to **DSPM for AI** by selecting **Solutions** > **DSPM for AI** > **Recommendations**.

1. Select the **Detect unethical behavior in AI apps** recommendation.

1. In the flyout, review the overview of what this policy will configure:

   - The default policy name is **DSPM for AI – Unethical behavior in AI apps**.

   - The policy detects sensitive or inappropriate information within prompts and responses in Microsoft 365 Copilot and other AI agents.

   - It applies to all users and groups in your organization.

1. Select **Create policy** to create the Communication Compliance policy.

1. On the **Policy successfully created** page, select **X** to close the flyout.

1. The **Recommendations** page will refresh, and the **Detect unethical behavior in AI apps** recommendation will move to **Completed**.

1. In the left navigation, select **Policies**.

1. Select the newly created **DSPM for AI – Unethical behavior in AI apps** policy to review its configuration and status.

1. On the **DSPM for AI - Unethical behavior in AI apps** page, select **X** to close the flyout.

You've created a policy that detects unethical activity in AI applications to help Contoso maintain responsible use of Copilot.

## Task 4 – Create a data risk assessment to detect unlabeled content

To understand potential gaps in labeling coverage, you'll run a data risk assessment to identify files without sensitivity labels that may be accessed by Copilot.

1. In **DSPM for AI**, select the recommendation titled **Protect sensitive data referenced in Copilot and agent responses**.

1. In the **Protect sensitive data referenced in Copilot and agent responses** pane, review the summary, then select **Go to assessments**.

1. On the **Data risk assessments** page, select **Create custom assessment**

1. On the **Basic details** page, enter:

   - **Name**: ```Unlabeled File Exposure Assessment```
   - **Description**: ```Identifies files without sensitivity labels that may be exposed in Microsoft 365 Copilot responses and provides recommendations to reduce oversharing risks.```

1. Select **Next**.

1. On the **Add users** page, select **All**, then select **Next**.

1. On the **Add data sources to assess** page, leave the default location of **SharePoint** selected, then select **Next**.

1. On the **Review and run the data assessment scan** page, select **Save and run**.

1. On the **Data assessment successfully created** page, select **Done**.

You've now used Microsoft Purview DSPM for AI to detect AI-related risks, enforce policies, and assess sensitive data exposure, helping your organization use AI securely.
