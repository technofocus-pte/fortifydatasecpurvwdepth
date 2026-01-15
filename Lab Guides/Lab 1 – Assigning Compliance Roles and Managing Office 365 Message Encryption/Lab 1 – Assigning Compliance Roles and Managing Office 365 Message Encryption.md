# Lab 1 – Assigning Compliance Roles and Managing Office 365 Message Encryption

## Introduction:

The Microsoft Purview portal supports directly managing permissions for users who perform tasks within Microsoft Purview. Using the Roles and scopes area in Settings for the portal, you can manage permissions for users across your Purview data security, data governance, and risk and compliance solutions. You can limit users to perform only specific tasks that you explicitly grant them access to.

## Objective:

- Assign managers and compliance roles to users in Microsoft 365.
- Create Microsoft 365 and security groups for team collaboration.
- Enable trial for Microsoft Purview compliance assessments.
- Verify and configure Azure RMS for Office 365 Message Encryption.
- Modify the default OME template to disable social ID access.
- Test encrypted email delivery without social sign-in.
- Create and apply a custom OME branding template for the finance team.
- Create a mail flow rule to encrypt messages from the Finance department
- Add a disclaimer to encrypted messages
- Enable the mail flow rule
- Validate message encryption

## Exercise 1 - Managing Compliance Roles

In this exercise we will be activating all the trial licenses required
for implementing security with Microsoft Purview.

### Task 1 – Adding Manager role to an existing user.

1.  Log into the VM with the account details provided with your lab.

2.  Open **Microsoft Edge** and navigate to the Microsoft 365 admin center, ```https://admin.microsoft.com```, and log in as **MOD Administrator**, using Admin Credentials.

    > [!Note] **Note: Skip MFA for the Microsoft 365 Admin center**
    >
    > In some tenants, you might see a Portal MFA Enforcement prompt when signing in. If this prompt appears:
    >
    > - Select **Skip for now** to temporarily delay MFA setup.
    >
    > - On the **Let us know why you're skipping MFA** dialogue, select any justification, then select **Send and skip**.
    >
    > This postpones MFA enforcement in the Microsoft 365 Admin center for the tenant and allows you to proceed with the lab.

3.  From the left pane, select **Users** \> **Active users**, and click on the first user **Adele Vance**.

    ![](./media/image1.png)

4.  Under **Manager**, Click **Edit manager**.

    ![](./media/image2.png)

5.  Remove the current manager and type ```Patti``` in the search box. Select **Patti Fernandez**. Click **Save Changes**.

    ![](./media/image3.png)

6.  Change the manager to **Patti Fernandez** for all the following users.

	- Adele Vance

	- Christie Cline

	- Megan Bowen

7.  For **Patti Fernandez**, add **MOD Administrator** as the manager.

### Task 2 – Assign administrative roles

1.  Select the user **Patti Fernandez**, under **Account**, scroll to **Roles** and click on **Manage roles**.

    ![](./media/image4.png)

2.  Once the **Roles** pane opens, check the radio button near **Admin center access**, and expand **Show all by category.**

    ![](./media/image5.png)

3.  Under the **Security & Compliance** category, select the checkbox for **Compliance Administrator**, **Security Administrator**, and **Application Administrator** then, select **Save changes** at the bottom of the flyout panel. Click on **Save changes**.

    ![](./media/image6.png)

4. Close the pane, stay on the same page, and continue to the next task.

### Task 3 – Creating teams and groups in Microsoft admin center

1.  Now expand **Teams & groups**, select **Active teams & groups** and click on **Add a Microsoft 365 group** under **Teams & Microsoft 365 groups**.

    ![](./media/image7.png)

2.  In the **Name** field, enter ```Contoso Finance Team```, and in the **Description** field, enter ```This team handles finance.```, and then click on **Next**.

    ![](./media/image8.png)

3.  On the **Assign Owners** page, click on **Assign owners**, check the box besides **Adele Vance**, and click on **Add(1)**. Click on **Next**.

    ![](./media/image9.png)

4.  On the **Add members** page add **Adele Vance**, and **Christie Cline** as members, click **Next**. On the **Add members** page, select **Next**.

5.  For group email address use ```contosofinance``` and then click **Next**.

    ![](./media/image10.png)

6.  Click on **Create group**.

    ![](./media/image11.png)

7.  Once done, click on **Close**.

    ![](./media/image12.png)

8.  On the **Active teams & groups page**, select **Security groups** tab. Select **Add a security group.**

    ![](./media/image13.png)

9. Repeat the steps to create another group with the following  information.

	- On the **Set up the basics**, enter the following to the **Name** field: ```EDM_DataUploaders```.

	- On the **Description** field, enter ```People who will upload data for EDM```.

	- Select **Next**.

	- On the **Settings** page, select **Next**.

	- On the **Review and finish adding group** page, review your settings and select **Create group**.

	- When the **New group created** page is shown, select the close button. 

	- Now select the newly created **EDM_DataUploaders** group from the list.

	- Under **Members** tab, select **View all and manage owners**, and add **Patti Fernandez** and **Christie Cline**.

	- Similarly add add **Patti Fernandez** and **Christie Cline** as the members.

    ![](./media/image14.png)

<!--

### Task 3 – Enabling trial for compliance Assessments

1.  Log in to the Purview Portal ```https://purview.microsoft.com```, and log in as **MOD Administrator**, using Admin Credentials.

2.  If a welcome window is displayed, agree to the terms if asked and select **Get started**.

    ![](./media/image15.png)

3.  Scroll down and under Trials and recommendations, select **View all trials and recommendations**.

    ![](./media/image16.png)

4.  On the **Microsoft Purview trials and recommendations** page, go to **Compliance assessments**, under **Purview and Priva trials** and select **Try now**.

    ![](./media/image17.png)

5. Click on **Start Trials**.

    ![](./media/image18.png)

Note: It might take up to 2 hours for the changes to take effect. Sign n again to see the new features. In the meantime, continue with next steps.

6. From the navigation bar select **Solutions** \> **Audit**.

    ![](./media/image19.png)

7. On the **Audit** page, select **Start recording user and admin activity** to activate audit logging.

    ![](./media/image20.png)

## Exercise 2 – Managing Office 365 Message Encryption

**Patti Fernandez**, an Information Security Administrator at Contoso Ltd., is implementing secure email communication to protect sensitive information exchanged between departments. As part of this effort, they'll configure **Microsoft 365 built-in Office 365 Message Encryption (OME)** by using the Exchange admin center to automatically encrypt messages sent from the Finance department and include a clear notice that the message was sent securely.

### Task 1 – Verifying Azure RMS functionality

In this task, you will install the **Exchange Online PowerShell** module and verify the correct Azure RMS functionality of your tenant.

1.  Open an **elevated PowerShell** window by selecting the Windows button with the right mouse button and then run **Windows PowerShell** as administrator.

    ![](./media/image21.png)

2.  Confirm the **User Account Control** window with **Yes**.

3.  Enter the following cmdlet to install the latest Exchange Online PowerShell module version:

`Install-Module ExchangeOnlineManagement`

    ![](./media/image22.png)

4.  Confirm the **NuGet** provider security dialog with **Y** for Yes and press **Enter**. This process may take some seconds to complete.

    ![](./media/image23.png)

5.  Confirm the Untrusted repository security dialog with **Y** for Yes and press **Enter**. This process may take some seconds to complete.

    ![](./media/image24.png)

6.  Enter the following cmdlet to change your execution policy and press **Enter**

`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

    ![](./media/image25.png)

7.  Confirm the Execution Policy Change with  **Y** for Yes and press **Enter**.

    ![](./media/image26.png)

8.  Enter the following cmdlet to use the **Exchange Online PowerShell** module and connect to your tenant:

`Connect-ExchangeOnline`

    ![](./media/image27.png)

9. When the **Sign in** window is displayed, sign in as **Patti  Fernandez** using the username ```PattiF@TenantName``` and the User Password given on your resources tab. (replace TenantName with Tenant Name given on the resources tab)

10. Verify Azure RMS and IRM is activated in your tenant by using the following cmdlet and press **Enter**:

`Get-IRMConfiguration | fl AzureRMSLicensingEnabled`

11. When **AzureRMSLicensingEnabled** result is **True**, Azure RMS is activated for your tenant. Continue with the next step.

    ![](./media/image28.png)

12. Test the Azure RMS templates used for Office 365 Message Encryption against the demo pilot user **Adele Vance** by using the following cmdlet (replace {TENANTPREFIX} with your tenant prefix given on the resources tab)

 `Test-IRMConfiguration -Sender adelev@TenantName -Recipient adelev@TenantName```

13. Verify all tests are in the status PASS and no errors are shown.

    ![](./media/image29.png)

14. Leave the **PowerShell** window open.

You have successfully installed the Exchange Online PowerShell module, connected to your tenant, and verified the correct functionality of Azure RMS.

### Task 2 – Modifying default OME template

Next, there is a requirement in your organization to restrict trust for foreign identity providers, such as Google or Facebook. Because these social IDs are activated by default for accessing messages protected with OME, you need to deactivate the use of social IDs for all users in your organization.

1.  Run the following cmdlet to view the default OME configuration:

`Get-OMEConfiguration -Identity "OME Configuration" |fl`

    ![](./media/image30.png)

2.  Review the settings and confirm that the **SocialIdSignIn** parameter is set to **True**.

    ![](./media/image31.png)

3.  Run the following cmdlet to restrict the use of social IDs for accessing messages from your tenant protected with OME:

`Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn:$false`

    ![](./media/image32.png)

4.  Confirm the warning message for customizing the default template with **Y** for Yes and press Enter.

    ![](./media/image33.png)

5.  Check the default configuration again and validate, the **SocialIdSignIn** parameter is now set to **False**.

`Get-OMEConfiguration -Identity "OME Configuration" |fl`

6.  Notice the result should show the **SocialIDSignIn** is set to **False**.

    ![](./media/image34.png)

7.  Leave the **PowerShell window** open and proceed to next exercise.

You have successfully deactivated the usage of foreign identity providers, such as Google and Facebook in Office 365 Message Encryption.

### Task 3 – Testing Modified OME template

You must confirm that no social IDs dialog is displayed for external recipients when receiving a message protected with Office 365 Message Encryption from users of your tenant and they need to use the OTP at any time accessing the encrypted content.

1.  In **Microsoft Edge**, open a **New InPrivate Window** and navigate to ```https://outlook.office.com``` and log into Outlook on the web with the username ```AdeleV@TenantName``` and the User Password given on your resources tab.

2.  On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **No**.

3.  Select **Save** in the **Save password** dialog, to save the pilot users password in your browser.

4.  If a **Translate page from…** window is shown, select the arrow down and select **Never translate from…**.

5.  Select **New mail** from the upper left side part of Outlook on the web.

    ![](./media/image35.png)

6.  In the **To** line enter your personal or other third-party email address that is not in the tenant domain. Enter ```Secret Message``` to the subject line and ```My super-secret message.``` to the body.

    ![](./media/image36.png)

7.  From the top pane go to **Options** pane, select **Encrypt** to encrypt the message. If you do not find the option, select the **3 dots (…)** at the top right, then from the dropdown select **Encrypt**.

    ![](./media/image37.png)

8.  Once you've successfully encrypted the message, you should see a notice that says "**Encrypt: This message is encrypted. Recipients can't remove encryption.**"

    ![](./media/image38.png)

9. Select **Send** to send the message.

    ![](./media/image39.png)

**Note**: In the trial account you may or may not have the privilege to send any email and your mail may not be able to reach the receiver from your current tenant. But your email goes through, you can check out the following steps to test the template.

10. Sign in to your personal email account and open the message from Adele Vance. If you sent this email to a Microsoft account (like @outlook.com) the encryption may be processed automatically and you will see the message automatically.

**Note**: If you sent the email to another email service like (@gmail.com), you may have to perform the next steps to process the encryption and read the message. You may need to check your junk or spam
folder for the message.

11. Select **Read the message**.

12. Without having social IDs activated, there is no button to authenticate with your Google account.

13. Select **Sign in with a One-time passcode** to receive a limited time passcode.

14. Go to your personal email portal and open the message with subject **Your one-time passcode to view the message**.

15. Copy the passcode, paste it in to the OME portal and select **Continue**.

16. Review the encrypted message.

You have successfully tested the modified default OME template with deactivated social IDs.

### Task 4 – Creating custom branding template

Protected messages sent by your organizations finance department require a special branding, including customized introduction and body texts and a Disclaimer link in the footer. The finance messages shall also expire after seven days. In this task, you will create a new custom OME configuration and create a transport rule to apply the OME configuration to all mails sent from the finance department.

1.  In the PowerShell window that we left open with Exchange Online connected. run the following cmdlet to create a new OME configuration:

`New-OMEConfiguration -Identity "Finance Department" -ExternalMailExpiryInDays 7`

    ![](./media/image40.png)

2.  Confirm the warning message for customizing the template with **Y** for Yes and press **Enter**.

    ![](./media/image41.png)

3.  Change the introduction text message with the following cmdlet

`Set-OMEConfiguration -Identity "Finance Department" -IntroductionText "from Contoso Ltd. finance department has sent you a secure message."`

    ![](./media/image42.png)

4.  Confirm the warning message for customizing the template with **Y** for Yes and press **Enter**.

    ![](./media/image43.png)

5.  Change the body email text of the message with the following cmdlet

`Set-OMEConfiguration -Identity "Finance Department" -EmailText "Encrypted message sent from Contoso Ltd. finance department. Handle the content responsibly."`

6.  Confirm the warning message for customizing the template with **Y** for Yes and press **Enter**.

    ![](./media/image44.png)

7.  Change the disclaimer URL to point to Contoso's privacy statement site.

`Set-OMEConfiguration -Identity "Finance Department" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`

    ![](./media/image45.png)

8.  Confirm the warning message for customizing the template with **Y** for Yes and press **Enter**.

    ![](./media/image46.png)

9.  Use the following cmdlet to create a mail flow rule, which applies the custom OME template to all messages sent from the Contoso finance team. This process may take a few seconds to complete.

`New-TransportRule -Name "Encrypt all mails from Contoso Finance team" -FromScope InOrganization -FromMemberOf "Contoso Finance Team" -ApplyRightsProtectionCustomizationTemplate "Finance Department" -ApplyRightsProtectionTemplate Encrypt`

    ![](./media/image47.png)

    ![](./media/image48.png)

10. Type the following cmdlet to verify changes.

`Get-OMEConfiguration -Identity "Finance Department" | Format-List`

    ![](./media/image49.png)

11. Leave the **PowerShell** open.

You have successfully created a new transport rule that applies the custom OME template automatically, when a member of the finance department sends a message to external recipients.

### Task 5 – Testing the custom branding template

To validate the new custom OME configuration, you need to use the account of Adele Vence, who is a member of the finance team. In the trial account you will not have the privilege to send any email but you can check out the following steps to understand how to test the template when you have your own licenses. You can perform step 1 - 4 but your mail may not be able to reach the receiver from your current trial tenant.

1.  In **Microsoft Edge**, open a **New InPrivate Window** and navigate to ```https://outlook.office.com``` and log into Outlook on the web with the username ```AdeleV@TenantName``` and the User Password given on the resources tab.

    ![](./media/image50.png)

2.  Select **New message** from the upper left side part of Outlook on the web.

3.  In the **To** line enter your personal or other third-party email address that is not in the tenant domain. Enter ```Finance Report``` to the subject line and enter ```Secret finance information. ``` to the body.

4.  Select **Send** to send the message.

5.  Sign in to the email account you used above and open the message from Adele Vance.

6.  You should see a message from **Christie Cline** that looks like the image below. Select **Read the message**.

7.  If you want to read the message, perform the following steps.

    1.  Click on **Read the message**. Select **Sign in with a One-time passcode** to receive a limited time passcode.

    2.  Go to your personal email portal and open the message with subject **Your one-time passcode to view the message**.

    3.  Copy the passcode, paste it in to the OME portal and select **Continue**.

    4.  Review the encrypted message with custom branding.

You have successfully tested the new customized OME template.

 -->

## Exercise 2 – Managing Office 365 Message Encryption


### Task 1 – Create a mail flow rule to encrypt messages from the Finance department

In this task, you'll use the Exchange admin center to create a mail flow rule that applies Microsoft Purview Message Encryption to all messages sent by members of the Finance Team group.

1. In **Microsoft Edge**, go to ```https://admin.exchange.microsoft.com``` and sign in as `PattiF@TenantName`.

1. In the left navigation pane, expand **Mail flow**, then select **Rules**.

    ![](./media/image51.png)

1. On the **Rules** page, select **+ Add a rule** > **Apply Office 365 Message Encryption and rights protection to messages**.

    ![](./media/image52.png)

1. On the **Set rule conditions** page, configure:

   - **Name:** ```Encrypt messages from Finance department```

   - In the **Apply this rule if** section, configure:

      - For dropdown 1: **The sender**

    	![](./media/image53.png)

      - For dropdown 2: **is a member of this group**, then select **Finance Team** and **Save** in the **Select members** flyout.

    	![](./media/image54.png)

    	![](./media/image55.png)

    	![](./media/image56.png)

   - In the **Do the following** section:

     - Leave the default **Modify the message security** and **Apply Office 365 Message Encryption and rights protection** selected

    	![](./media/image57.png)

     - Select the **Select one** link under the **Do the following** section.

    	![](./media/image58.png)

     - In the **Select RMS template** flyout, select **Encrypt**, then select **Save**.

    	![](./media/image59.png)

     - Select **Next** back on the **Set rule conditions** page.

    	![](./media/image60.png)

1. On the **Set rule settings** page, leave the default selected, then select **Next**.

    ![](./media/image61.png)

1. On the **Review and finish** page, review your mail flow rule, then select **Finish**.

    ![](./media/image62.png)

1. Select **Done** once your mail flow rule has been created.

    ![](./media/image63.png)

You've successfully created a mail flow rule that encrypts messages sent from the Finance department using Microsoft Purview Message Encryption. This ensures that sensitive financial communications are protected before leaving the organization.

### Task 2 – Add a disclaimer to encrypted messages

Next, you'll modify the existing encryption rule to append a disclaimer. This disclaimer acts as a simple form of message branding, notifying recipients that the message was sent securely by Contoso Ltd.

1. On the **Rules** page, select the newly created **Encrypt messages from Finance department**.

    ![](./media/image64.png)

1. In the **Encrypt messages from Finance department** flyout, select **Edit rule conditions**.

    ![](./media/image65.png)

1. Select the **+** to the right of the **Do the following** section to add another action.

    ![](./media/image66.png)

1. In the newly created **And** section:

   - For dropdown 1: **Apply a disclaimer to the message**

    ![](./media/image67.png)

   - For dropdown 2: **append a disclaimer**.

    ![](./media/image68.png)

   - Under the dropdowns, select **Enter text**.
   
    ![](./media/image69.png)

   - Then enter ```This email has been encrypted and sent securely by Contoso Ltd.``` in the **specify disclaimer text** flyout.

   - Select **Save** at the bottom of the flyout.

    ![](./media/image70.png)

   - Select the 'Select one' link to add a fallback action.

   - In the **specify fallback action** flyout, select **Wrap**, then select **Save** at the bottom of the flyout.

    ![](./media/image71.png)

1. Select **Save** at the bottom **Encrypt messages from Finance department** flyout.

    ![](./media/image72.png)

1. Once the rule has been changed, you'll see a message stating **Transport rule updated successfully**.

    ![](./media/image73.png)

1. Close the flyout by selecting the **Done**.

    ![](./media/image74.png)

You've updated the encryption rule to append a disclaimer to each protected message. This makes it clear to recipients that the email was encrypted and securely transmitted from Contoso Ltd.

### Task 3 – Enable the mail flow rule

By default, new mail flow rules are created in a disabled state. In this task, you'll enable the encryption rule so it can begin protecting messages from the Finance department.

1. On the **Rules** page, select **Disabled** for the newly created **Encrypt messages from Finance department**.

    ![](./media/image75.png)

1. In the **Encrypt messages from Finance department** flyout, set the toggle under **Enable or disable rule** to **Enabled**.

    ![](./media/image76.png)

1. The mail flow rule will enable automatically. You'll see a message stating **Updating the rule status, please wait...**. Once the rule is enabled, you'll see a message stating **Rule status updated successfully**.

    ![](./media/image77.png)

1. Close the flyout by selecting the **X** in the top right corner of the flyout.

    ![](./media/image78.png)

**Note**: Rule propagation Changes can take several minutes to apply. If validation fails, wait a few minutes and send the test again.

The encryption rule is now active and enforcing Microsoft Purview Message Encryption for messages sent from the Finance department. Any future messages from Finance users will be automatically encrypted and include the Contoso Ltd. disclaimer.

### Task 4 – Validate message encryption

In this task, you'll send a test email from a member of the Finance department to confirm that Microsoft Purview Message Encryption is applied automatically and that the recipient sees the secure message notice.

1. Open **Microsoft Edge** in an InPrivate window by right clicking Microsoft Edge from the task bar and selecting **New InPrivate window**.

1. Navigate to ```https://outlook.office.com``` and log into Outlook on the web as ```AdeleV@TenantName```.

1. On the **Stay signed in?** dialog box, select the checkbox for **Don't show this again** then select **No**.

1. In Outlook on the web, select **New mail**.

    ![](./media/image79.png)

1. In the **To** line enter your personal or other third-party email address that isn't in the tenant domain. Enter ```Secret Message``` in the subject line and ```My super-secret message.``` in the body of the email.

1. Select **Send** to send the message. Leave the Outlook window open.

    ![](./media/image80.png)

	>Sign into your personal email account in a new window and open the message from Adele Vance. If you sent the message to a Microsoft account (such as @outlook.com), it might open automatically. If you sent the email to another email service like (@gmail.com), you might have to perform the next steps to process the encryption and read the message.

1. Select **Read the message**.

    ![](./media/image81.png)

1. Select **Sign in with a One-time passcode** to receive a limited time passcode.

1. Go to your personal email portal and open the message with subject **Your one-time passcode to view the message**.

1. Copy the passcode, paste it into the portal and select **Continue**.

1. Review the encrypted message. You should see the **This email has been encrypted and sent securely by Contoso Ltd.** message at the bottom of your email.

You've successfully validated that messages from the Finance department are automatically encrypted and include the appended Contoso disclaimer, confirming that Microsoft Purview Message Encryption is working as expected.

## Summary:

In this lab we successfully replicated an organisation in our admin center, assigned appropriate licenses and learnt how to use Microsoft 365 built-in Office 365 Message Encryption (OME).
