<!--
lab:
  title: Lab 1 — Establish least-privilege compliance roles and encrypt sensitive correspondence with Office 365 Message Encryption
  description: In this lab we assigned least-privilege compliance and security roles and learnt how to use Microsoft 365 built-in Office 365 Message Encryption (OME) to automatically encrypt sensitive correspondence.
  duration: 30 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Office 365
-->

# Lab 1 — Establish least-privilege compliance roles and encrypt sensitive correspondence with Office 365 Message Encryption

Contoso Pharmaceuticals is standing up its data-security program, and the first operational step is to give its security administrator exactly the access needed to run Microsoft Purview — no more. Contoso follows the principle of least privilege: rather than granting broad global rights, it assigns a small, fixed set of roles — giving the security administrator, Allan Deyoung, the Compliance Administrator and Security Administrator roles, and the communication-compliance reviewer, Megan Bowen, the Communication Compliance role — so each person can perform only their part of the compliance work and nothing else. With access in place, the team then tackles its first protection requirement — ensuring that sensitive correspondence leaving the organization, such as legal email sent to external partners, is automatically encrypted, carries a clear secure-message notice, and is scoped so that only the intended senders trigger it.

In this lab, you first act as the Global Administrator (the **MOD Administrator** account) to assign the standing roles to **Allan Deyoung**, Contoso's Information Security Administrator. You then work through the Exchange admin center to create a mail-flow rule that encrypts sensitive outbound correspondence, add a disclaimer, enable the rule, and validate it end to end — including a rigorous check that the rule encrypts mail from authorized senders while leaving other mail untouched.

**Learning outcomes.** After this lab you can:
- Assign Microsoft Entra and Microsoft Purview roles to an operator using least privilege.
- Create a mail-flow rule that applies Microsoft Purview Message Encryption to sensitive correspondence.
- Add a disclaimer that notifies recipients a message was sent securely.
- Enable a mail-flow rule and validate encryption from an external recipient's perspective.
- Verify that an encryption rule is correctly scoped, encrypting only mail from the intended senders.


**Tasks**:

1. Assign the standing administrative roles
1. Create a mail-flow rule to encrypt sensitive correspondence
1. Add a disclaimer to encrypted messages
1. Enable the mail-flow rule
1. Validate message encryption
1. Verify the encryption rule is correctly scoped


## Exercise 1 — Establish least-privilege compliance roles

### Task 1 – Assign the standing administrative roles

In this task, you'll assign compliance roles following least privilege and separation of duties: **Allan Deyoung**, the security administrator, receives **Compliance Administrator** in Microsoft Purview and **Security Administrator** in Microsoft Entra, while **Megan Bowen**, the communication-compliance reviewer, receives **Communication Compliance**. **MOD Administrator** is also added to the Purview role groups. These are the only role assignments for the entire course; no later lab changes permissions. You perform this task as the Global Administrator.

1. Log into the lab VM with the **Admin** account credentials given in the Resources tab of your lab environment.

1. In **Microsoft Edge**, navigate to +++https://purview.microsoft.com+++ and sign in as **MOD Administrator**, `admin@TenantName` (the Tenant Name and Admin password are provided in the Resources tab).

    > [!Note]
    > If a Portal MFA Enforcement prompt appears, select **Skip for now**, choose any justification on the **Let us know why you're skipping MFA** dialog, then select **Send and skip**. This postpones MFA enforcement so you can proceed.

1. In the left navigation, select **Settings**, then in the left sub-navigation select **Roles and scopes**, then select **Role groups**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image1.png)

1. On the **Role groups for Microsoft Purview solutions** page, select **Compliance Administrator** from the list. Do not select the checkbox, select the name.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image2.png)

1. On the **Compliance Administrator** pane, select the **Members** tab.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image3.png)

1. On the **Members** tab, select **+ Add Member > Choose users**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image4.png)

1. In the user list, select the checkbox next to **MOD Administrator** and **Allan Deyoung**, then choose **Select**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image5.png)

1. With the user in the list, select **Done**. Then select **Confirm** on the pop-up.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image6.png)

1. Back on the **Role groups** page, select **Communication Compliance** from the list. Do not select the checkbox, select the name.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image7.png)

1. On the **Communication Compliance** pane, select the **Members** tab.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image8.png)

1. On the **Members** tab, make sure that **MOD Administrator** and **Megan Bowen** are added.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image9.png)

1. Close the panel. Now we will assign the Microsoft Entra security role.

1. Open a new tab in **Microsoft Edge**, navigate to +++https://entra.microsoft.com+++, and confirm you are signed in as **MOD Administrator**.

1. In the left navigation, expand **Entra ID**, then select **Roles & admins**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image10.png)

1. In the search box, enter `Security Administrator`, then select the **Security Administrator** role from the results. Do not select the checkbox, select the name.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image11.png)

1. On the **Security Administrator** page, select **+ Add assignments**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image12.png)

1. On the **Add assignments** panel, select **No member selected**, select the checkbox next to **Allan Deyoung**, then select **Select**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image13.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image14.png)

1. Select **Next**, set the assignment type to +++Active+++. Under **Enter justification**, add +++To set up Data Security solutions+++. Select **Assign**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image15.png)

    > [!Note]
    > Microsoft Entra role assignments generally take effect within a few minutes but can take longer to fully propagate. If a later task reports insufficient permissions, wait a few minutes and retry. This timing is indicative, not guaranteed.

    You have successfully assigned the compliance roles under least privilege — Compliance Administrator and Security Administrator to Allan Deyoung, and Communication Compliance to Megan Bowen.


## Exercise 2 — Manage Office 365 Message Encryption

Contoso Pharmaceuticals exchanges sensitive information with external contract research organizations, and legal staff sometimes email content that must not be exposed in transit. In this exercise, you'll configure Microsoft 365 built-in Office 365 Message Encryption (OME) through the Exchange admin center to automatically encrypt messages sent from the Legal team, include a clear notice that the message was sent securely, and confirm the rule is scoped correctly.

### Task 1 – Create a mail-flow rule to encrypt sensitive correspondence

In this task, you'll use the Exchange admin center to create a mail-flow rule that applies Microsoft Purview Message Encryption to all messages sent by members of Contoso's Legal team (the **Legal Team** group in the tenant).

1. In **Microsoft Edge**, navigate to the Exchange admin center at +++https://admin.exchange.microsoft.com+++ and sign in as **Allan Deyoung**, `AllanD@TenantName`.

1. In the left navigation pane, expand **Mail flow**, then select **Rules**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image16.png)

1. On the **Rules** page, select **+ Add a rule** > **Apply Office 365 Message Encryption and rights protection to messages**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image17.png)

1. On the **Set rule conditions** page, configure:

    - **Name**:

        `Encrypt sensitive research correspondence`
  
    - In the **Apply this rule if** section:
    - For the first dropdown, select **The sender**.
    - For the second dropdown, select **is a member of this group**, then select the **Legal Team** group and select **Save** in the **Select members** flyout.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image18.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image19.png)

    - In the **Do the following** section:
    - Leave the default **Modify the message security** and **Apply Office 365 Message Encryption and rights protection** selected.
    - Select the **Select one** link under the **Do the following** section.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image20.png)

    - In the **Select RMS template** flyout, select **Encrypt**, then select **Save**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image21.png)

    - Select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image22.png)


1. On the **Set rule settings** page, review the defaults selected, then select **Next**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image23.png)

1. On the **Review and finish** page, review your mail-flow rule, then select **Finish**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image24.png)

1. Select **Done** once your mail-flow rule has been created.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image25.png)

    You have successfully created a mail-flow rule that encrypts messages sent from Contoso's **Legal Team** group using Microsoft Purview Message Encryption.


### Task 2 – Add a disclaimer to encrypted messages

Next, you'll modify the encryption rule to append a disclaimer. This acts as a simple form of message branding, notifying recipients that the message was sent securely by Contoso Pharmaceuticals.

1. On the **Rules** page, select the newly created **Encrypt sensitive research correspondence** rule.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image26.png)

1. In the flyout, select **Edit rule conditions**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image27.png)

1. Select the **+** to the right of the **Do the following** section to add another action.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image28.png)

1. In the newly created **And** section:

    - For the first dropdown, select **Apply a disclaimer to the message**.
    - For the second dropdown, select **append a disclaimer**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image29.png)

    - Under the dropdowns, select **Enter text**, then enter +++This email has been encrypted and sent securely by Contoso Pharmaceuticals.+++ in the **specify disclaimer text** flyout, and select **Save** at the bottom of the flyout.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image30.png)

    - Select the **Select one** link to add a fallback action. In the **specify fallback action** flyout, select **Wrap**, then select **Save** at the bottom of the flyout.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image31.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image32.png)


1. Select **Save** at the bottom of the **Encrypt sensitive research correspondence** flyout.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image33.png)

1. Once the rule has been changed, you'll see a message stating **Transport rule updated successfully**.

1. Close the flyout by selecting **Done**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image34.png)

    You have successfully updated the encryption rule to append a disclaimer, making it clear to recipients that the email was encrypted and securely transmitted from Contoso Pharmaceuticals.


### Task 3 – Enable the mail-flow rule

By default, new mail-flow rules are created in a disabled state. In this task, you'll enable the encryption rule so it can begin protecting messages from the Legal team.

1. On the **Rules** page, select **Disabled** for the newly created **Encrypt sensitive research correspondence** rule.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image35.png)

1. In the flyout, set the toggle under **Enable or disable rule** to **Enabled**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image36.png)

1. The mail-flow rule enables automatically. You'll see **Updating the rule status, please wait...**, and once enabled, **Rule status updated successfully**.

1. Close the flyout by selecting the **X** in the top-right corner.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image37.png)

    > [!Note]
    > Mail-flow rule changes can take several minutes to apply across the service. If a validation send in the next task isn't encrypted, wait a few minutes and send again. This timing is indicative, not guaranteed.

    You have successfully enabled the encryption rule, which is now enforcing Microsoft Purview Message Encryption for messages sent from Contoso's Legal team.


### Task 4 – Validate message encryption

In this task, you'll send a test email from a member of the Legal team to confirm that Microsoft Purview Message Encryption is applied automatically and that the recipient sees the secure-message notice.

1. Open **Microsoft Edge** in an InPrivate window by right-clicking Microsoft Edge in the task bar and selecting **New InPrivate window**.

1. Navigate to +++https://outlook.office.com+++ and sign in to Outlook on the web as **Grady Archie**, `GradyA@TenantName` (a member of the **Legal Team**). Grady's password is provided in the Resources tab.

1. On the **Stay signed in?** dialog, select the checkbox for **Don't show this again**, then select **No**.

1. In Outlook on the web, select **New mail**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image38.png)

1. In the **To** line, enter your personal or other third-party email address that isn't in the tenant domain. Enter +++Legal updates on ongoing research+++ in the subject line and `Sharing an update on the current research program.` in the body.

1. Select **Send**. Leave the Outlook window open.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image39.png)

    > [!Note]
    > Sign in to your personal email account in a new window and open the message from Grady Archie. If you sent it to a Microsoft account (such as @outlook.com), it might open automatically. If you sent it to another service (such as @gmail.com), you might need the next steps to process the encryption and read the message. Check your junk or spam folder if you don't see it.

1. Select **Read the message**.

1. Confirm that the message is protected and select **Sign in with a One-time passcode** to receive a limited-time passcode.

1. Go to your personal email portal and open the message with subject **Your one-time passcode to view the message**.

1. Copy the passcode, paste it into the portal, and select **Continue**.

1. Review the encrypted message. Confirm the **This email has been encrypted and sent securely by Contoso Pharmaceuticals.** disclaimer appears at the bottom.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-01/media/image40.png)

    You have successfully validated that messages from the Legal team are automatically encrypted and include the appended Contoso disclaimer, confirming that Microsoft Purview Message Encryption is working as expected.


### Task 5 – Verify the encryption rule is correctly scoped

Validating that authorized mail is encrypted is only half the picture — a correctly scoped rule must also leave *other* mail untouched, so that it neither over-encrypts routine communication nor misfires. In this task, you'll send a message from a user who is **not** in the Legal team and confirm it is delivered normally, without encryption — proving the rule is scoped to the intended senders only.

1. In the InPrivate window, sign out of Grady Archie's mailbox (or open a new InPrivate window), navigate to +++https://outlook.office.com+++, and sign in as **Pradeep Gupta**, `PradeepG@TenantName` (a user who is **not** a member of the Legal Team). Pradeep's password is provided in the Resources tab.

1. Select **New mail**. In the **To** line, enter the same external email address you used in Task 4. Enter `Finance summary` in the subject line and `Sharing this month's routine summary.` in the body.

1. Select **Send**.

1. Sign in to your external email account and open the message from Pradeep Gupta. Confirm that this message arrives **unencrypted** — it is delivered directly as a normal email, with **no** "Read the message" wrapper, no one-time-passcode step, and no Contoso encryption disclaimer.

1. Compare the two results to confirm the rule is correctly scoped:

    - Grady Archie's message (Task 4), sent from a member of the Legal team, **was** encrypted and carried the disclaimer.
    - Pradeep Gupta's message (this task), sent from outside the Legal team, was **not** encrypted.

    > [!Note]
    > This two-sided check confirms the rule's sender condition is working: it encrypts mail from the **Legal Team** group and takes no action on mail from other users. If Pradeep's message were also encrypted, the rule's membership condition would be too broad and would need correcting. Because mail-flow changes can lag by a few minutes, if the results don't match at first, wait briefly and resend. This timing is indicative, not guaranteed.

    You have successfully verified that the encryption rule is correctly scoped — encrypting sensitive correspondence from the Legal team while leaving other mail untouched.


## Summary

In this lab, you assigned compliance roles using least privilege and separation of duties — Compliance Administrator and Security Administrator to Allan Deyoung, the operator, and Communication Compliance to Megan Bowen, the reviewer — so each person has exactly the access their role requires and nothing more. You then used the Exchange admin center to create a mail-flow rule that applies Microsoft Purview Message Encryption to correspondence from Contoso's Legal team, added a disclaimer notifying recipients the message was sent securely, and enabled the rule. Finally, you validated the encryption end to end from an external recipient's perspective, and verified that the rule is correctly scoped by confirming that mail from an unauthorized sender is delivered normally without encryption. Contoso's sensitive legal correspondence is now automatically protected in transit, with confidence that the control applies to exactly the right senders.
