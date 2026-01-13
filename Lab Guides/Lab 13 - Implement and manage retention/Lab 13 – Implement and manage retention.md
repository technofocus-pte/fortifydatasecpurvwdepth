# Lab 13 – Implement and manage retention

You are Patti Fernandez, a Compliance Administrator at Contoso Ltd. The company is tightening its data security strategy to reduce risk exposure related to financial data and privileged communications. You've been asked to configure Microsoft Purview retention solutions that support audit readiness, limit unnecessary data retention, and ensure proper oversight for sensitive communications.

**Tasks**:

- Create a retention label
- Publish a retention label
- Create an auto-apply retention label policy
- Create a static retention policy
- Recover SharePoint content

## Exercise 1 – Create a retention label

In this task, you'll create a retention label for sensitive financial data that needs to be retained for auditing and investigation purposes.

1. Log into VM as admin.

1. In Microsoft Edge, navigate to ```https://purview.microsoft.com``` and sign in as ```pattif@TenantName```.

1. Navigate to **Solutions** > **Data Lifecycle Management**.

   ![](./media/image1.png)

1. Then select **Retention labels**.

   ![](./media/image2.png)

1. On the **Labels** page, select **Create a label**.

   ![](./media/image3.png)

1. On the **Name your retention label** page, enter:

   - **Name**: ```Sensitive Financial Records```
   - **Description for users**: ```Use for financial files with sensitive data that must be retained for audit or security purposes.```
   - **Description for admins**: ```Retains high-impact financial data for 5 years to support audits and security investigations.```

1. Select **Next**.

   ![](./media/image4.png)

1. On the **Define label settings** page, select **Retain items forever or for a specific period**, then select **Next**.

   ![](./media/image5.png)

1. On the **Define the period** page, ensure these values are set for the retention period configuration input:

    - **How long is the period?**: 5 Years

      ![](./media/image6.png)

    - **When should the period begin?**: When items were modified

      ![](./media/image7.png)

1. Select **Next**.

   ![](./media/image8.png)

1. On the **Choose what happens after the retention period** page select **Delete items automatically**, then select **Next**.

   ![](./media/image9.png)

1. On the **Review and finish** page, select **Create label**.

   ![](./media/image10.png)

1. On the **Your retention label is created** page, select the option to **Do nothing**, then select **Done**.

   ![](./media/image11.png)

You've created a retention label that retains financial content for five years and deletes it afterward to reduce data exposure.

## Exercise 2 – Publish a retention label

In this task, you'll publish the retention label so users can apply it in Microsoft 365 services like Exchange, SharePoint, and OneDrive.

1. In Microsoft Purview, navigate to **Solutions** > **Data Lifecycle Management** > **Retention labels**.

   ![](./media/image12.png)

1. Select the checkbox next to the **Sensitive Financial Records** label, then select the **Publish labels** icon to publish this retention label.

   ![](./media/image13.png)

1. On the **Choose labels to publish** page, verify the **Sensitive Financial Records** label is selected, then select **Next**.

   ![](./media/image14.png)

1. On the **Policy Scope** page select **Next**.

   ![](./media/image15.png)

1. On the **Choose the type of retention policy to create** page select **Static** then select **Next**.

   ![](./media/image16.png)

1. On the **Choose where to publish labels** page select **Let me choose specific locations** and select:

    - Exchange mailboxes
    - SharePoint classic and communication sites
    - OneDrive accounts
    - Deselect all other locations

1. Select **Next**.

   ![](./media/image17.png)

1. On the **Name your policy** enter:

    - **Name**: ```Sensitive Financial Data Retention```
    - **Description**: ```Makes the 'Sensitive Financial Records' label available to users in Exchange, SharePoint, and OneDrive.```

1. Select **Next**.

   ![](./media/image18.png)

1. On the **Finish** page, select **Submit**.

   ![](./media/image19.png)

1. On the **Your retention label was published** page, select **Done**.

   ![](./media/image20.png)

You've published the retention label, making it available for users to apply in key Microsoft 365 services.

## Exercise 3 – Create an auto-apply retention label policy

In this task, you'll configure a policy that automatically applies a retention label to content containing personal financial information.

1. In Microsoft Purview, navigate to **Solutions** > **Data Lifecycle Management** > **Policies** > **Label policies**.

   ![](./media/image21.png)

1. On the **Label policies** page, select **Auto-apply a label** to start the label configuration.

   ![](./media/image22.png)

1. On the **Let's get started page**, enter:

   - **Name**: ```Auto-apply Personal Financial PII```
   - **Description**: ```Applies this label to personal financial data to help meet audit and investigation requirements. Retains content for 3 years.```

1. Select **Next**.

   ![](./media/image23.png)

1. On the **Choose the type of content you want to apply this label to** page, select **Apply label to content that contains sensitive info**, then select **Next**.

   ![](./media/image24.png)

1. On the **Content that contains sensitive info** page, select the **Financial** category, then select the **U.S. Gramm-Leach-Bliley Act (GLBA)** regulation, then select **Next**.

   ![](./media/image25.png)

1. On the **Define content that contains sensitive info** page, select **Next**.

   ![](./media/image26.png)

1. On the **Policy Scope** page, select **Next**.

   ![](./media/image27.png)

1. On the **Choose the type of retention policy to create​** page, select **Static**. Select **Next**.

   ![](./media/image28.png)

1. On the **Choose where to publish labels** page select **Let me choose specific locations** and select:

    - Exchange mailboxes
    - SharePoint classic and communication sites
    - OneDrive accounts
    - Deselect all other locations

1. Select **Next**.

   ![](./media/image29.png)

1. On the **Choose a label to auto-apply** page, select **Add label**.

   ![](./media/image30.png)

1. On the **Choose a label** flyout, select **Personal Financial PII**, then select **Add**.

   ![](./media/image31.png)

1. Back on the **Choose a label to auto-apply** page, select **Next**.

   ![](./media/image32.png)

1. On the **Decide whether to test or run your policy**, select **Test the policy before running it**, then select **Next**.

   ![](./media/image33.png)

1. On the **Review and finish** page, select **Submit**.

   ![](./media/image34.png)

1. Then select **Done** on the **Your auto-labeling policy has been created** page.

   ![](./media/image35.png)

You've created an auto-apply policy that identifies personal financial data and applies a retention label automatically.

## Exercise 4 – Create a static retention policy

In this task, you'll create a static retention policy for Microsoft Teams content to help reduce long-term data risk.

1. In Microsoft Purview, navigate to **Solutions** > **Data Lifecycle Management** > **Policies** > **Retention policies**.

   ![](./media/image36.png)

1. On the **Retention policies** page, select **New retention policy**.

   ![](./media/image37.png)

1. On the **Name your retention policy** page, enter:

   - **Name**: ```Teams Retention```
   - **Description**: ```Retains Teams chats and channel messages for 3 years, then deletes them to reduce long-term data risk.```

1. Select **Next**.

   ![](./media/image38.png)

1. On the **Policy Scope** page, select **Next**.

   ![](./media/image39.png)

1. On the **Choose the type of retention policy to create** page, select **Static**, then select **Next**.

   ![](./media/image40.png)

1. On the **Choose locations to apply the policy** page, enable:

   - Teams channel messages
   - Teams chats
   - Leave all other locations disabled.

1. Select **Next**.

   ![](./media/image41.png)

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **Custom** from the dropdown list

   	 ![](./media/image42.png)

   - Change the years field to `3`
   - **Start the retention period based on**: When items were last modified

    ![](./media/image43.png)

   - **At the end of the retention period**: Delete items automatically

1. Select **Next**.

   ![](./media/image44.png)

1. On the **Review and finish** page select **Submit**.

   ![](./media/image45.png)

1. Then select **Done** on the **You successfully created a retention policy** page.

   ![](./media/image46.png)

You've configured a static retention policy that retains Teams messages for three years before automatically deleting them.

## Exercise 5 – Create an adaptive scope

In this task, you'll define an adaptive scope that targets Microsoft 365 groups associated with leadership and operations roles.

1. In Microsoft Purview, **Settings** > **Roles and scopes** > **Adaptive scopes**.

1. On the **Adaptive scopes** page select **+ Create scope**.

   ![](./media/image47.png)

1. On the **Name your adaptive policy scope** page enter:

    - **Name**: ```Leadership and Ops Groups```
    - **Description**: ```Targets Leadership and Operations M365 groups with privileged access to sensitive data.```

1. Select **Next**.

   ![](./media/image48.png)

1. On the **Assign admin unit** page select **Next**.

   ![](./media/image49.png)

1. On the **What type of scope do you want to create?** page select **Microsoft 365 Groups**, then select **Next**.

   ![](./media/image50.png)

1. On the **Create the query to define users** page, in the **User attributes** section, ensure these values are selected for the user attribute configuration:

   - Select the **Attribute** dropdown then select **Name**

     ![](./media/image51.png)

   - Leave the default **is equal to** value in the next field
   - Enter ```Leadership``` as the **Value**

1. Add a second attribute by selecting **+ Add attribute** on the **Create the query to define users** page.

   ![](./media/image52.png)

1. In the new field under the one we just configured, configure these values:

   - Select the dropdown for the query operator and update it from And to **Or**.

     ![](./media/image53.png)

   - Select the **Attribute** dropdown then select **Name**.

     ![](./media/image54.png)

   - Leave the default **is equal to** value in the next field
   - Enter ```Operations``` as the **Value**

1. Select **Next**.

   ![](./media/image55.png)

1. On the **Review and finish** page select **Submit**.

   ![](./media/image56.png)

1. Once your adaptive scope is created select **Done** on the **Your scope was created** page.

   ![](./media/image57.png)

You've created an adaptive scope to support targeted retention for privileged groups in the organization.

## Exercise 6 – Create an adaptive retention policy

In this task, you'll use the adaptive scope you created to configure a retention policy for Microsoft 365 groups with sensitive responsibilities.

1. In Microsoft Purview, navigate to **Solutions** > **Data Lifecycle Management** > **Policies** >  **Retention policies**.

   ![](./media/image58.png)

1. On the **Retention policies** page, select **+ New retention policy**.

   ![](./media/image59.png)

1. On the **Name your retention policy** page enter:

    - **Name**: ```Privileged Group Retention```
    - **Description**: ```Retains content from Leadership and Operations groups for 5 years to support audit and investigation.```

1. Select **Next**.

   ![](./media/image60.png)

1. On the **Policy Scope** page select **Next**.

   ![](./media/image61.png)

1. On the **Choose the type of retention policy to create** page select **Adaptive** then select **Next**.

   ![](./media/image62.png)

1. On the **Choose adaptive policy scopes and locations** page select **+ Add scopes**.

   ![](./media/image63.png)

1. On the **Choose adaptive policy scopes** flyout panel select the checkbox for **Leadership and Ops Groups** then select **Add** at the bottom of the panel.

   ![](./media/image64.png)

1. Back on the **Choose locations to apply the policy** enable:

    - Microsoft 365 Group mailboxes & sites
    - Leave all other locations disabled.

1. Select **Next**.

   ![](./media/image65.png)

1. On the **Decide if you want to retain content, delete it, or both** page, ensure these values are set for the retention configuration:

   - Select **Retain items for a specific period**.
   - Under **Retain items for a specific period**, select **5 years** from the dropdown list
   - **Start the retention period based on**: When items were last modified
   - **At the end of the retention period**: Delete items automatically

1. Select **Next**.

   ![](./media/image66.png)

1. On the **Review and finish** page select **Submit**.

   ![](./media/image67.png)

1. Select **Done** once the policy is created.

   ![](./media/image68.png)

You've created a retention policy that applies to content owned by privileged groups, retaining it for five years before deletion.

## Exercise 7 – Recover SharePoint content

In this task, you'll simulate restoring a deleted document from a SharePoint site to validate your recovery options.

1. You should still be logged into VM and logged in as Patti Fernandez in Microsoft Purview.

1. Select the App launcher (the grid icon) in the top-left corner, then select **More apps** from the sub-menu.

   ![](./media/image69.png)

1. Select **SharePoint**.

   ![](./media/image70.png)

1. On the SharePoint landing page, search for ```Benefits``` then select **Benefits @ Contoso** from the search results.

   ![](./media/image71.png)

1. In the left sidebar select **Documents**.

   ![](./media/image72.png)

1. On the **Documents** page, select the checkbox for **Vacation Policies.pptx** then select **Delete** from the action bar.

   ![](./media/image73.png)

1. On the **Delete?** dialog, select **Delete**.

   ![](./media/image74.png)

1. On the left sidebar, select **Recycle bin**.

   ![](./media/image75.png)

1. On the **Recycle bin** page, right click **Vacation Policies.pptx**, then select **Restore**.

   ![](./media/image76.png)

1. On the left sidebar, select **Documents** and notice the file has been restored.

   ![](./media/image77.png)

You have successfully recovered a deleted document from a SharePoint Site.