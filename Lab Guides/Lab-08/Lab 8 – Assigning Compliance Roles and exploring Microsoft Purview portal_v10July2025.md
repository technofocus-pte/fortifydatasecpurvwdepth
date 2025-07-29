# **Lab 8 – Assigning Compliance Roles and exploring Microsoft Purview portal**

## **Introduction**

The Microsoft Purview portal supports directly managing permissions for users who perform tasks within Microsoft Purview. Using the Roles and scopes area in Settings for the portal, you can manage permissions for users across your Purview data security, data governance, and risk and compliance solutions. You can limit users to perform only specific tasks that you explicitly grant them access to.

## **Objectives**
- Assign managers and compliance roles to users in Microsoft 365.
- Create Microsoft 365 and security groups for team collaboration.
- Enable trial for Microsoft Purview compliance assessments.
- Verify and configure Azure RMS for Office 365 Message Encryption.
- Modify the default OME template to disable social ID access.
- Test encrypted email delivery without social sign-in.
- Create and apply a custom OME branding template for the finance team.
- Enable Adaptive Protection in Microsoft Purview.

## Exercise 1 - Managing Compliance Roles

In this exercise, we will be activating all the trial licenses required
for implementing security with Microsoft Purview.

### Task 1 – Adding Manager role to an existing user.

1.  Log into the VM with the account details provided in
    the **resources** tab of your lab.

2.  Log in to the Microsoft 365 admin
    center **+++https://admin.microsoft.com+++** using Administrative
    Username and Administrative Password.

3.  From the left pane, select **Users** \> **Active users**, and click
    on the first user **Adele Vance**.

    ![](./media/image1.png)

4.  Under **Manager**, click **Edit manager**.

    ![A screenshot of a computer Description automatically generated](./media/image2.png)

5.  Remove the current manager and type +++Patti+++ in the search box.
    Select **Patti Fernandez**. Click on the **Save Changes** button.

    ![A screenshot of a computer Description automatically generated](./media/image3.png)

6.  Similarly, change the manager to **Patti Fernandez** for all the following users.
    - Christie Cline
    - Megan Bowen
      
8.  For Patti Fernandez, add **MOD Administrator** as the manager.

   ![A screenshot of a computer Description automatically generated](./media/p3.png)

   ![A screenshot of a computer Description automatically generated](./media/p4.png)

### Task 2 – Adding a Compliance Administrator

1.  Select the user **Patti Fernandez**, under **Account**, scroll
    to **Roles** and click on **Manage roles**.

    ![A screenshot of a computer Description automatically generated](./media/image4.png)

2.  Once the **Roles** pane opens, check the radio button near **Admin
    center access**, and expand **Show all by category.**

    ![A screenshot of a computer Description automatically generated](./media/image5.png)

3.  Scroll to **Security & compliance**, check the box
    beside **Compliance Administrator**, and click on **Save changes**.

    ![A screenshot of a computer Description automatically generated](./media/image6.png)

### Task 3 – Creating teams and groups in Microsoft admin center

1.  Now expand **Teams & groups**, select **Active teams & groups** and
    click on **Add a Microsoft 365 group** under Teams & Microsoft 365
    groups.

    ![A screenshot of a computer Description automatically generated](./media/image7.png)

2.  In the **Name** field, enter **+++Contoso Finance Team+++**, and in the **Description**
    box, enter **+++This team handles finance.+++**, then click
    on the **Next** button.

    ![A screenshot of a computer Description automatically generated](./media/image8.png)

3.  On the **Assign Owners** page, click on **Assign owners**, check the
    box besides **Adele Vance**, and click on **Add(1)**. Click
    on **Next**.

    ![](./media/image9.png)

4.  On the **Add members** page, add **Adele Vance** as a member,
    click **Next**. On the **Add members** page, select **Next**.

5.  In  the **Group email address** field, enter **+++contfosofinance+++**, then
    click **Next**.

    ![A screenshot of a computer Description automatically generated](./media/image10.png)

6.  Click on **Create group**.

    ![A screenshot of a computer Description automatically generated](./media/image11.png)

7.  Once done, click on **Close**.

    ![A screenshot of a computer Description automatically generated](./media/image12.png)

8.  On the **Active teams & groups page**, select **Security
    groups** tab. Select **Add a security group.**

    ![A screenshot of a computer Description automatically generated](./media/image13.png)

9.  Repeat the steps to create another group with the following
    information.

- On the **Set up the basics**, enter the following to
  the **Name** field: **+++EDM_DataUploaders+++**. In the Description
  field, enter **+++People who will upload data for EDM+++**.

- Select **Next**.

- On the **Settings** page, select **Next**.

- On the **Review and finish adding group** page, review your settings
  and select **Create group**. Once the EDM_DataUploaders group created, then click on the **Close** button.

- When the **New group created** page is shown, select newly created
  **EDM_DataUploaders** group.
    ![A screenshot of a computer Description automatically generated](./media/e10.png)
  
- Click on **Members** tab, then select **View all and manage owners**, and add **Patti Fernandez**.

    ![A screenshot of a computer Description automatically generated](./media/e1.png)

    ![A screenshot of a computer Description automatically generated](./media/e2.png)

- Similarly add **Christie Cline** as the member.

    ![A screenshot of a computer Description automatically generated](./media/e3.png)

    ![A screenshot of a computer Description automatically generated](./media/e4.png)
    
### Task 4 – Enabling trial for compliance Assessments

1.  Log in to the Purview Portal **+++https://purview.microsoft.com+++**
    using Administrative Username and Administrative Password.

2.  If a welcome window is displayed, agree to the terms and
    select **Get started** and close it.

    ![](./media/image15.png)

    **Note**: In case, you did not see **I agree to the terms of data flow disclosure and Privacy Statement**, then ignore and click on **Get started** button

3.  From the navigation bar, select **Solutions** \> **Audit**.

    ![](./media/image16.png)

4.  On the **Audit** page, select **Start recording user and admin
    activity** to activate audit logging.

    ![A screenshot of a search engine Description automatically generated](./media/image17.png)

## Exercise 2 - Managing Office 365 Message Encryption

The first setting **Patti Fernandez** needs to configure and test with
her pilot team is the **Microsoft 365 built-in** **Office 365 Message
Encryption (OME)**. For this purpose, she will modify the default
template and create a new branding template, that will be assigned to
one of the pilot users. The pilot users will then test the OME
functionality with their accounts.

### Task 1 – Verifying Azure RMS functionality

In this task, you will install the **Exchange Online PowerShell** module
and verify the correct Azure RMS functionality of your tenant.

1.  Open an **elevated PowerShell** window by selecting the Windows
    button with the right mouse button and then run **Windows
    PowerShell** as administrator.

    ![A screenshot of a computer Description automatically generated](./media/ab1.png)

2.  Confirm the **User Account Control** window with **Yes**.

3.  Enter the following cmdlet to install the latest Exchange Online
    PowerShell module version:

    **+++Install-Module ExchangeOnlineManagement+++**

    ![](./media/image19.png)

4.  In case, Untrusted repository security message appears, then type **Y** for Yes
    and press **Enter**. If it does not appear, then move on to the next step. 

5.  Enter the following cmdlet to change your execution policy and
    press **Enter**

    **+++Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser+++**

    ![](./media/image20.png)

6.  Confirm the Execution Policy Change with  **Y** for Yes and
    press **Enter**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image21.png)

7.  Enter the following cmdlet to use the **Exchange Online
    PowerShell** module and connect to your tenant:

    **+++Connect-ExchangeOnline+++**

8.  When the **Sign in** window is displayed, sign in as **Patti
    Fernandez** using the username PattiF@WWLxXXXXXX.onmicrosoft.com and
    the User Password given on your resources tab.

    ![](./media/image22.png)

    ![](./media/image23.png)

    In case, **Automatically sign in to all desktop apps and websites on this device?** dialog box appears, then click on the **No, this app only** button

    ![](./media/image24.png)

9.  Verify Azure RMS and IRM is activated in your tenant by using the
    following cmdlet and press **Enter**:

    **+++Get-IRMConfiguration | fl AzureRMSLicensingEnabled+++**

    ![](./media/image25.png)

10. When **AzureRMSLicensingEnabled** result is **True**, Azure RMS is
    activated for your tenant. Continue with the next step.

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image26.png)

11. Test the Azure RMS templates used for Office 365 Message Encryption
    against the demo pilot user **Adele Vance** by using the following
    cmdlet (replace WWLxXXXXXX with your tenant prefix given on the
    resources tab)

**+++Test-IRMConfiguration -Sender adelev@WWLxXXXXXX.onmicrosoft.com -Recipient adelev@WWLxXXXXX.onmicrosoft.com+++**

12. Verify all tests are in the status PASS and no errors are shown.

    ![](./media/image27.png)

13. Leave the **PowerShell** window open.

You have successfully installed the Exchange Online PowerShell module,
connected to your tenant, and verified the correct functionality of
Azure RMS.

### Task 2 – Modifying default OME template

Next, there is a requirement in your organization to restrict trust for
foreign identity providers, such as Google or Facebook. Because these
social IDs are activated by default for accessing messages protected
with OME, you need to deactivate the use of social IDs for all users in
your organization.

1.  Run the following cmdlet to view the default OME configuration:

**+++Get-OMEConfiguration -Identity"OME Configuration" |fl+++**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image28.png)

2.  Review the settings and confirm that
    the **SocialIdSignIn** parameter is set to **True**.

    ![](./media/image29.png)

3.  Run the following cmdlet to restrict the use of social IDs for
    accessing messages from your tenant protected with OME:

**Set-OMEConfiguration -Identity"OME
Configuration" -SocialIdSignIn:$false**

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image30.png)

4.  Confirm the warning message for customizing the default template
    with **Y** for Yes and press Enter.

    ![A blue screen with white text AI-generated content may be incorrect.](./media/image31.png)

5.  Check the default configuration again and validate,
    the **SocialIdSignIn** parameter is now set to **False**.

**+++Get-OMEConfiguration -Identity"OME Configuration" |fl+++**

6.  Notice the result should show the **SocialIDSignIn**is set
    to **False**.

    ![](./media/image32.png)

7.  Leave the **PowerShell window** **open** and proceed to next
    exercise.

You have successfully deactivated the usage of foreign identity
providers, such as Google and Facebook in Office 365 Message Encryption.

### Task 3 – Testing Modified OME template

You must confirm that no social IDs dialog is displayed for external
recipients when receiving a message protected with Office 365 Message
Encryption from users of your tenant and they need to use the OTP at any
time accessing the encrypted content.

1.  In **Microsoft Edge**, open a **New InPrivate Window** and navigate
    to **https://outlook.office.com** and log into Outlook on the web
    with the username **AdeleV@WWLxXXXXXX.onmicrosoft.com** and the User
    Password given on your resources tab.

2.  On the **Stay signed in?** dialog box, select the **Don’t show this
    again** checkbox and then select **No**.

3.  In case, **Save password** dialog box appears, then select **Save**.

4.  If a **Translate page from…** window is shown, select the arrow down
    and select **Never translate from…**.

5.  If you see **Your privacy matters** dialog box, then click on the
    **Continue** button.

    ![](./media/image33.png)

6.  Select **New mail** from the upper left side part of Outlook on the
    web.

    ![Graphical user interface, text, application, Word Description automatically generated](./media/image34.png)

7.  In the **To** line enter your personal or other third-party email
    address that is not in the tenant domain.
    Enter **Secret Message** to the subject line
    and **+++My super-secret message.+++** to the body.

    ![Graphical user interface, text, application, Word Description automatically generated](./media/image35.png)

8.  From the top pane go to **Options** pane, select **Encrypt** to
    encrypt the message.

    ![A screenshot of a computer Description automatically generated](./media/image36.png)

9.  Once you've successfully encrypted the message, you should see a
    notice that says "**Encrypt: This message is encrypted. Recipients
    can't remove encryption.**"

    ![A screenshot of a computer screen Description automatically generated](./media/image37.png)

10. Select **Send** to send the message.

    ![Graphical user interface, text, email Description automatically generated](./media/image38.png)

In the trial account you will not have the privilege to send any email
but you can check out the following steps to understand how to test the
template when you have your own licenses. Your mail will not be able to
reach the receiver from your current tenant.

11. Sign in to your personal email account and open the message from
    Adele Vance. If you sent this email to a Microsoft account (like
    @outlook.com) the encryption may be processed automatically and you
    will see the message automatically.

    ![](./media/image39.png)

**Note:** If you sent the email to another email service like
(@google.com), you may have to perform the next steps to process the
encryption and read the message. You may need to check your junk or spam
folder for the message.

12. Select **Read the message**.

13. Without having social IDs activated, there is no button to
    authenticate with your Google account.

14. Select **Sign in with a One-time passcode** to receive a limited
    time passcode.

    ![](./media/image40.png)

15. Go to your personal email portal and open the message with
    subject **Your one-time passcode to view the message**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image41.png)

16. Copy the passcode, paste it in to the OME portal and
    select **Continue**.

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image42.png)

17. Review the encrypted message.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image43.png)

You have successfully tested the modified default OME template with
deactivated social IDs.

### Task 4 – Creating custom branding template

Protected messages sent by your organizations finance department require
a special branding, including customized introduction and body texts and
a Disclaimer link in the footer. The finance messages shall also expire
after seven days. In this task, you will create a new custom OME
configuration and create a transport rule to apply the OME configuration
to all mails sent from the finance department.

1.  In the PowerShell window that we left open with Exchange Online
    connected, run the following cmdlet to create a new OME
    configuration:

**+++New-OMEConfiguration -Identity"Finance
Department" -ExternalMailExpiryInDays 7+++**

    ![](./media/image44.png)

2.  Confirm the warning message for customizing the template
    with **Y** for Yes and press **Enter**.

    ![A blue screen with white text AI-generated content may be incorrect.](./media/image45.png)

3.  Change the introduction text message with the following cmdlet:

**+++Set-OMEConfiguration -Identity"Finance
Department" -IntroductionText " from Contoso Ltd. finance department has
sent you a secure message." +++**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image46.png)

4.  Confirm the warning message for customizing the template
    with **Y** for Yes and press **Enter**.

    ![A screen shot of a computer AI-generated content may be incorrect.](./media/image47.png)

5.  Change the body email text of the message with the following cmdlet:

**+++Set-OMEConfiguration -Identity"Finance
Department" -EmailText "Encrypted message sent from Contoso Ltd. finance
department. Handle the content responsibly." +++**

6.  Confirm the warning message for customizing the template
    with **Y** for Yes and press **Enter**.

    ![](./media/image48.png)

7.  Change the disclaimer URL to point to Contoso's privacy statement
    site:

**+++Set-OMEConfiguration -Identity "Finance
Department" -PrivacyStatementURL"https://contoso.com/privacystatement.html"+++**

8.  Confirm the warning message for customizing the template
    with **Y** for Yes and press **Enter**.

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image49.png)

9.  Use the following cmdlet to create a mail flow rule, which applies
    the custom OME template to all messages sent from the Contoso
    finance team. This process may take a few seconds to complete.

**+++New-TransportRule -Name "Encrypt all mails from Contoso Finance
team" -FromScopeInOrganization -FromMemberOf "Contoso Finance
Team"-ApplyRightsProtectionCustomizationTemplate"Finance
Department" -ApplyRightsProtectionTemplate Encrypt+++**

    ![A screenshot of a computer screen AI-generated content may be incorrect.](./media/image50.png)

10. Type the following cmdlet to verify changes.

**+++Get-OMEConfiguration -Identity"Finance
Department" | Format-List+++**

    ![](./media/image51.png)

11. Leave the **PowerShell** open.

You have successfully created a new transport rule that applies the
custom OME template automatically, when a member of the finance
department sends a message to external recipients.

### Task 5 – Testing the custom branding template

To validate the new custom OME configuration, you need to use the
account of Christie Cline, who is a member of the finance team. In the
trial account you will not have the privilege to send any email but you
can check out the following steps to understand how to test the template
when you have your own licenses. You can perform step 1 - 4 but your
mail will not be able to reach the receiver from your current tenant.

1.  In **Microsoft Edge**, open a **New InPrivate Window** and navigate
    to **https://outlook.office.com** and log into Outlook on the web
    with the username **<ChristieC@M365xXXXXXX.onmicrosoft.com>** and
    the User Password given on the resources tab.

    ![Graphical user interface, text, application Description automatically generated](./media/image52.png)

2.  Select **New message** from the upper left side part of Outlook on
    the web.

3.  In the **To** line enter your personal or other third-party email
    address that is not in the tenant domain.
    Enter **Finance Report** to the subject line and
    enter **Secret finance information.** to the body.

4.  Select **Send** to send the message.

5.  Sign in to the email account you used above and open the message
    from Veronica Quek.

6.  You should see a message from **Christie Cline** that looks like the
    image below. Select **Read the message**.

    ![](./media/image53.png)

7.  If you want to read the message, perform the following steps.

    1.  Click on **Read the message**. Select **Sign in with a One-time
        passcode** to receive a limited time passcode.

    2.  Go to your personal email portal and open the message with
        subject **Your one-time passcode to view the message**.

    3.  Copy the passcode, paste it in to the OME portal and
        select **Continue**.

    4.  Review the encrypted message with custom branding.

You have successfully tested the new customized OME template

## **Exercise 3 - Enabling Adaptive Protection**

1.  In the Microsoft Purview portal left navigation pane, click on
    **Solutions**, then navigate and select **Insider Risk Management**

     ![](./media/image54.png)

2.  In the **Insider Risk Management** pane, navigate and click on
    **Adaptive Protection**, then select **Adaptive Protection
    settings**. Now, turn **On** the Adaptive Protection toggle.

    ![](./media/image55.png)

3.  Click on the **Save** button.

    ![](./media/image56.png)

4.  Enabling of Adaptive protection will take time. We will explore
    Adaptive protection feature in the 8^(th) lab.

    ![](./media/image57.png)

## **Summary**

In this lab, you configured foundational compliance settings and
explored Microsoft Purview capabilities for data protection. You started
by creating users, assigning them appropriate roles (such as Manager and
Compliance Administrator), and setting up Microsoft 365 groups and
security groups to simulate an organization structure for Contoso.

You then enabled trials for compliance features and activated audit
logging in Microsoft Purview. The lab proceeded with configuring and
testing **Office 365 Message Encryption (OME)** by modifying the default
template to disable social ID access, and creating a **custom branded
OME configuration** for the finance department, enforced via a transport
rule. Finally, you enabled **Adaptive Protection** under Insider Risk
Management in Purview, laying the groundwork for intelligent, risk-based
data protection policies to be explored further in later labs.
