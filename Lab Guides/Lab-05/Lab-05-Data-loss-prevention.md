---
lab:
  title: Lab 5 — Prevent data exfiltration with endpoint, email, Teams, and cloud data loss prevention policies, from simulation to enforcement
  description: In this lab we created data loss prevention policies across endpoint, email, Teams, and cloud locations, moved them from simulation to enforcement, and verified that they block exfiltration.
  duration: 20 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Data Loss Prevention
---

# Lab 5 — Prevent data exfiltration with endpoint, email, Teams, and cloud data loss prevention policies, from simulation to enforcement

Contoso Pharmaceuticals now classifies and labels its regulated data, but classification does not stop someone from emailing a compound formulation to a competitor, pasting a trial-subject record into a Teams chat, or copying research files to a USB stick. Data loss prevention (DLP) closes those exfiltration paths. In this lab, acting as Allan Deyoung, you build DLP policies that detect Contoso's sensitive data — using the classifiers from Lab 2 and the labels from Lab 4 — and prevent it from leaving the organization across the paths that matter: endpoints (USB, clipboard, network shares, print), email, Teams, and cloud storage. You follow the disciplined rollout every DLP deployment should: start in simulation to observe impact, then enforce, and prove the block actually works.

You build the first policy in the portal to learn the wizard, then create a second with PowerShell, the way an administrator manages DLP at scale. The endpoint policy relies on the device onboarding enabled in Lab 0.

**Learning outcomes.** After this lab you can:

- Create a DLP policy in simulation mode across Exchange, Teams, SharePoint, and OneDrive.
- Create an Endpoint DLP policy that restricts USB, clipboard, network-share, and print activities on onboarded devices.
- Create a DLP policy with PowerShell.
- Move a policy from simulation to enforcement and manage policy priority.
- Review DLP alerts and activity.
- Prove that an enforced policy blocks a real exfiltration attempt.

**Tasks**:

1. Create a cloud and email DLP policy in simulation mode
2. Extend the policy to Teams and review simulation results
3. Create an Endpoint DLP policy for devices
4. Create a DLP policy with PowerShell
5. Move policies to enforcement and set priority
6. Prove the policy blocks a real exfiltration attempt
7. Review DLP alerts

## Task 0 – Set up the environment

### Synchronize the VM clock

1.  Close all the tabs of Microsoft Edge browser that are opened on your VM. Click on the **Windows** icon, then click on **Settings** as shown in the below image.

    ![](./media/image31.png)

2.  On the **Windows Settings** search bar, enter ```Date & time settings``` then select **Date & time settings** from the list.

3.  In the **Date & time** page, navigate and click on the **Sync now** button.

    ![](./media/image32.png)

### Onboarding a device

1.  Click on Windows icon, then select **Settings** as shown in the below image.

2.  Go to **Accounts** \> **Access work or school**. On the **Access work or school** page, click on **Connect**.

    ![](./media/image33.png)

    ![](./media/image34.png)

    ![](./media/image35.png)

3.  In the **Set up a work or school account** prompt, click on **Join this device to Microsoft Entra ID**.

    ![](./media/image36.png)

4.  In the sign in prompt, sign in with **MOD Administrator** credentials given on the resources tab of your lab environment.

5.  On the **Make sure this is your organization** dialog box, click on the **Join** button.

    ![](./media/image37.png)

6.  Once done you will see a confirmation window **You're all set!**. Click on **Done**.

    ![](./media/image38.png)

7.  Again, on the **Access work or school** page, click on **Connect**.

    ![](./media/image39.png)

8.  In the **Set up a work or school account** prompt, login using MOD administrator credentials.

    ![](./media/image40.png)

9.  On **Stay signed in?** dialog box, click on the **Yes** button.

10. If **Setting up your device** dialog box appears, then select **Got it**.

    ![](./media/image41.png)

11. Now go to **windows settings** \> **Accounts** \> **Access work or school** \> **Connected to Contoso MDM** \> **Info** \> **Sync**.

    ![](./media/image42.png)

    ![](./media/image43.png)

12. Click on the windows symbol on your VM. Select the user **Admin** and select **Sign out**.

    ![](./media/image44.png)

13. On the user screen select **Other user**.

    ![](./media/image45.png)

14. Enter your admin credentials given in the Resources of your lab environment and log into the VM as **MOD Administrator**.

    ![](./media/image46.png)

    ![](./media/image47.png)

15. Sign in to ```https://purview.microsoft.com``` using your **MOD Administrator** account on your Lab VM.

16. From the **Settings** \> **Device onboarding** \> **Onboarding**, click on **Download package**.

    ![](./media/image48.png)

    ![](./media/image49.png)

17. Once downloaded, copy the file to the desktop. Right-click the file and select **Extract all…**, then click on the **Extract** button.

18. Once done, open the folder and run the file with **Administrator** rights.

19. On the **The publisher could not be verified. Are you sure you want to run this software?** dialog box, click on the **Run** button.

20. If the **User Account Control** dialog box appears, click on the **Yes** button.

21. In the Command Prompt, press **Y** and press Enter to confirm. You will receive a message that the device is onboarded. Once you get the message, press any key to continue.

22. Once the Command Prompt is closed, open Command Prompt in administrator mode by typing **cmd** in Windows search, then right-click on **Command Prompt** and select **Run as administrator**.

23. On the **User Account Control** dialog box, click on the **Yes** button.

24. Run a detection test by running the following command. The Command Prompt window will close automatically.

    ```powershell
    powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference='silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'
    ```

25. Close the VM connection.

26. In Microsoft Purview, open **Settings** by clicking on the settings icon in the navigation and choose **Device onboarding** \> **Devices**.

> [!NOTE]
> While it usually takes about 60 seconds for device onboarding to be enabled, please allow up to 30 minutes.

27. You will be able to check the **Devices** list. The list will be empty until you onboard devices; once done, you will see your VM listed as the onboarded device.

## Task 1 – Create a cloud and email DLP policy in simulation mode

In this task, you'll create a DLP policy that detects Contoso's compound identifiers and exact trial-subject records and prevents them from being shared externally through Exchange, SharePoint, and OneDrive. You start in simulation mode so you can observe what the policy would catch before it affects users.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **Allan Deyoung**, `AllanD@TenantName` (the Tenant Name and account password are provided in the Resources tab).

2. In the left navigation, select **Solutions** > **Data loss prevention**.

	![](./media/image1.png)

3. Select **Policies**, then select **+ Create policy**.

	![](./media/image2.png)

4. On the **What info do you want to protect?** page, select **Enterprise applications and devices**.

	![](./media/image3.png)

5. On the **Start with a template or create a custom policy** page, under **Categories** select **Custom**, then under **Regulations** select **Custom policy**. Select **Next**.

	![](./media/image4.png)

6. On the **Name your DLP policy** page, enter the following, then select **Next**:

   - **Name**: `Protect research and trial data`
   - **Description**: `Prevents external sharing of Contoso compound identifiers and trial-subject records.`

	![](./media/image5.png)

7. On the **Assign admin units** page, select **Next**.

	![](./media/image6.png)

8. On the **Choose where to apply the policy** page, enable **Exchange email**, **SharePoint sites**, and **OneDrive accounts**. Disable all other locations for now (Teams is added in Task 2, Devices in Task 3). Select **Next**.

	![](./media/image7.png)

9. On the **Define policy settings** page, select **Create or customize advanced DLP rules**, then select **Next**.

	![](./media/image8.png)

10. On the **Customize advanced DLP rules** page, select **+ Create rule**.

	![](./media/image9.png)

11. On the **Create rule** page, in the **Name** field, enter `Block external sharing of research and trial data`.

12. Under **Conditions**, select **+ Add condition**, then select **Content is shared from Microsoft 365**. In the new section, select **with people outside my organization**.

	![](./media/image10.png)

	![](./media/image11.png)

13. Select **+ Add condition**, then select **Content contains**. Select **Add** > **Sensitive info types**, search for and select **Contoso Compound ID** and **Contoso Clinical Trial Subjects** (from Lab 2), then select **Add**.

	![](./media/image12.png)

	![](./media/image13.png)

	![](./media/image14.png)

14. Select **+ Add condition** again, then select **Content contains** a second grouping. Select **Add** > **Sensitivity labels**, select **Highly Confidential – Research** and **Restricted – Trial Data** (from Lab 4), then select **Add**. Set the grouping operator so the rule matches content that contains **both** of these SITs or labels, i.e. **And**.

	![](./media/image15.png)

	![](./media/image16.png)

	![](./media/image17.png)

15. Under **Actions**, select **+ Add an action**, then select **Restrict access or encrypt the content in Microsoft 365 locations**. Ensure **Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files** is selected, then select **Block only people outside your organization**.

	![](./media/image18.png)

	![](./media/image19.png)

16. In the **User notifications** section, set the toggle to **On**, and ensure **Policy tips** is selected.

	![](./media/image20.png)

17. In the **User overrides** section, select **Allow overrides from Microsoft 365 files and Microsoft Fabric items**, then select **Require a business justification to override**.

	![](./media/image21.png)

18. In the **Incident reports** section, set **Use this severity level in admin alerts and reports** to **Medium**, and ensure **Send an alert to admins when a rule match occurs** is on.

	![](./media/image22.png)

19. Select **Save**, then select **Next**.

	![](./media/image23.png)

	![](./media/image24.png)

20. On the **Policy mode** page, select **Run the policy in simulation mode**, and select the checkbox for **Show policy tips while in simulation mode**. Select **Next**.

	![](./media/image25.png)

21. Select **Submit**, then select **Done**.

	![](./media/image26.png)

	![](./media/image27.png)

You have successfully created a DLP policy in simulation mode that detects Contoso's research and trial data across email and cloud locations.

## Task 2 – Extend the policy to Teams and review simulation results

Simulation shows what a policy would do before it affects anyone. In this task, you'll review the first policy's simulation results and extend it to Teams so that compound identifiers and trial-subject records are also protected in chat and channel messages.

1. Allow the policy time to evaluate content, then on the **Policies** page select the **Protect research and trial data** policy to open its flyout.

2. Review the simulation overview, which shows how many items the policy would have acted on and where. This is the information you use to judge whether the policy is scoped correctly before enforcing it.

3. Select the **Protect research and trial data** policy, then select **Edit policy**. 

	![](./media/image28.png)

4. Select **Next** until you reach the **Choose where to apply the policy** page, select **Teams chat and channel messages**, then select **Next**, **Submit**, and **Done**.

	![](./media/image29.png)

	![](./media/image30.png)

> [!NOTE]
> Simulation results are not immediate — DLP evaluates content on a schedule, and a first pass over existing SharePoint and OneDrive content can take several hours to a day. Review simulation results before moving a policy to enforcement so you understand its impact. These timings are indicative, not guaranteed.

You have successfully extended the policy to Teams and reviewed its simulation results.

## Task 3 – Create an Endpoint DLP policy for devices

Cloud and email DLP cannot see what happens on a laptop — a researcher copying a formulation document to a USB stick, or pasting a compound identifier into a personal cloud upload. Endpoint DLP closes those paths. In this task, you'll create an endpoint DLP policy that restricts high-risk device activities for content containing Contoso's sensitive data. Device onboarding was enabled in Lab 0.

1. In the left navigation, select **Solutions** > **Data loss prevention** > **Policies**, then select **+ Create policy**.

    ![](./media/image50.png)

2. On the **What info do you want to protect?** page, select **Enterprise applications and devices**. On the template page, select **Custom** > **Custom policy**, then select **Next**.

    ![](./media/image51.png)

    ![](./media/image52.png)

3. On the **Name your DLP policy** page, enter the following, then select **Next**:

   - **Name**: `Endpoint protection for research and trial data`
   - **Description**: `Restricts USB, clipboard, network-share, and print activities for Contoso sensitive data on devices.`

4. On the **Assign admin units** page, select **Next**.

    ![](./media/image53.png)

5. On the **Choose where to apply the policy** page, enable **Devices** only, then select **Next**.

    ![](./media/image54.png)

6. On the **Define policy settings** page, select **Create or customize advanced DLP rules**, then select **Next**.

7. Select **+ Create rule**.

    ![](./media/image55.png)

8. Name it `Restrict device egress of sensitive data`. Under **Conditions**, select **+ Add condition** > **Content contains**. Select **Add** > **Sensitive info types**, select **Contoso Compound ID** and **Contoso Clinical Trial Subjects**, then select **Add**. Add a second grouping for **Sensitivity labels** and select **Highly Confidential – Research** and **Restricted – Trial Data**, so the rule matches content with all of these.

    ![](./media/image56.png)

9. Under **Actions**, select **+ Add an action**, then select **Audit or restrict activities on devices**.

    ![](./media/image57.png)

10. Under **File activities for all apps**, select **Apply restrictions to specific activity**, then set each of the following to **Block**:

    - **Copy to a removable USB device**
    - **Copy to a network share**
    - **Print**

11. Set **Copy to clipboard** to **Block with override** (so a user can proceed with a justification, which is less disruptive for a common activity while still capturing the event).

    ![](./media/image58.png)

12. In the **User notifications** section, set the toggle to **On** so users see a policy tip when an activity is restricted.

    ![](./media/image59.png)

13. In the **Incident reports** section, set the severity to **High** and ensure admin alerts are on. Select **Save**, then select **Next**.

    ![](./media/image60.png)

    ![](./media/image61.png)

14. On the **Policy mode** page, select **Run the policy in simulation mode**, then select **Next**, **Submit**, and **Done**.

    ![](./media/image62.png)

    ![](./media/image63.png)

    ![](./media/image64.png)

> [!NOTE]
> Endpoint DLP enforces through the Microsoft Defender for Endpoint sensor on the onboarded device; there is no separate agent. Policy changes reach the device once it is connected to the service, which can take some time to propagate. This timing is indicative, not guaranteed.

You have successfully created an Endpoint DLP policy that restricts high-risk device activities for Contoso's sensitive data.

## Task 4 – Create a DLP policy with PowerShell

Administrators create and manage DLP policies at scale with PowerShell rather than clicking through the wizard for each one. In this task, you'll create an additional DLP policy — blocking external email that contains the consent-form fingerprint — entirely from the command line.

1. On the client VM, open an elevated terminal: right-click the **Start** button and select **Terminal (Administrator)**. Select **Yes** on the User Account Control prompt.

2. Connect to Security & Compliance PowerShell. When the sign-in window appears, sign in as **Allan Deyoung**:

   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-IPPSSession -UserPrincipalName AllanD@TenantName
   ```

3. Create the DLP policy scoped to Exchange:

   ```powershell
   New-DlpCompliancePolicy -Name "Block external consent forms" -Comment "Blocks external email containing Contoso consent forms." -ExchangeLocation All -Mode Enable
   ```

    ![](./media/image65.png)

4. Add a rule that blocks external mail containing the consent-form fingerprint SIT from Lab 2:

   ```powershell
   New-DlpComplianceRule -Name "Block external consent form email" -Policy "Block external consent forms" -ContentContainsSensitiveInformation @{Name="Contoso Consent Form"} -AccessScope NotInOrganization -BlockAccess $true -BlockAccessScope All -NotifyUser Owner
   ```

    ![](./media/image66.png)

5. Confirm the rule was created and review its configuration:

   ```powershell
   Get-DlpComplianceRule -Identity "Block external consent form email" | Format-List Name, Policy, AccessScope, BlockAccess, ContentContainsSensitiveInformation
   ```

    ![](./media/image67.png)

You have successfully created a DLP policy with PowerShell that blocks external sharing of Contoso consent forms.

## Task 5 – Move policies to enforcement and set priority

Simulation is for observation; enforcement is where DLP protects data. In this task, you'll turn on the cloud/email policy and the endpoint policy, and set policy priority so the more restrictive policy wins when two match the same content.

1. In the Microsoft Purview portal, select **Solutions** > **Data loss prevention** > **Policies**.

2. Select the **Protect research and trial data** policy, then select **Edit policy**. Select **Next** until you reach the **Policy mode** page, select **Turn the policy on immediately**, then select **Next**, **Submit**, and **Done**.

    ![](./media/image68.png)

    ![](./media/image69.png)

3. Repeat step 2 for the **Endpoint protection for research and trial data** policy to turn it on.

4. On the **Policies** page, select the **Endpoint protection for research and trial data** policy, then select **Move up** (or **Move to top**) so it holds a higher priority than the broader policy.

    ![](./media/image70.png)

5. Select **Refresh** and review the **Order** column to confirm the priority.

> [!NOTE]
> When two DLP policies match the same content, the action of the higher-priority policy is enforced. Ordering the more restrictive endpoint policy above the broader policy ensures device egress is handled by the stricter rule. Enforcement changes can take time to propagate to services and devices. These timings are indicative, not guaranteed.

You have successfully moved the policies to enforcement and set their priority.

## Task 6 – Prove the policy blocks a real exfiltration attempt

A DLP policy is only trustworthy if it actually blocks. In this task, you'll attempt a genuine exfiltration — emailing a compound identifier externally — and confirm the enforced policy blocks it and shows the policy tip.

1. In **Microsoft Edge**, open a **New InPrivate window**, navigate to **`https://outlook.office.com`**, and sign in as **Isaiah Langer**, `IsaiahL@TenantName` (a Contoso user). Isaiah's password is provided in the Resources tab.

2. Select **New mail**. In the **To** line, enter an external email address you control (outside the Contoso tenant). In the subject, enter `Compound update`, and in the body enter `Please review the formulation data for investigational compound CX-2087.`

3. Before sending, confirm a **policy tip** appears in the message, warning that it contains sensitive information that Contoso policy protects.

> [!NOTE]
> If the policy tip and block do not appear immediately, this is expected: moving a policy from simulation to enforcement (Task 5) can take up to 24 hours to propagate to Exchange Online. Wait and retry this task rather than assuming the policy is misconfigured. Also note that in Outlook on the web, the policy tip sometimes appears only when you select **Send** (steps 4–5) rather than while composing (step 3) — the block at send is the definitive proof the policy is enforcing. The block and policy tip confirm the email/cloud policy is enforcing. To verify the endpoint policy the same way, on the onboarded device attempt to copy a document containing `CX-2087` to a USB device and confirm the copy is blocked with a policy tip — this requires the device to have received the enforced policy, which can take time. These timings are indicative, not guaranteed.

4. Select **Send**.

5. Confirm the send is **blocked**: Outlook reports that the message conflicts with a policy and cannot be sent to external recipients, and offers the option to override with a business justification (from the override setting you configured).

6. Select the override option, enter a business justification, and confirm the behavior — the message can now be sent, and the override with justification is recorded for the admin to review.

7. Return to the Microsoft Purview portal, go to **Data loss prevention** > **Alerts**, and confirm a new alert corresponding to this match has appeared (allowing a short time for it to surface).

You have successfully proven that the enforced DLP policy blocks a real exfiltration attempt, shows a policy tip, honors the justified override, and raises an alert.

## Task 7 – Review DLP alerts

DLP is only useful if someone acts on what it finds. In this task, you'll review the alerts DLP generates so you know where to monitor policy matches and investigate incidents.

1. In the Microsoft Purview portal, select **Solutions** > **Data loss prevention** > **Alerts**.

2. Review the **Alerts** dashboard. Each alert corresponds to a policy match; the list shows the policy, severity, and status.

    ![](./media/image71.png)

3. Select an alert to open its detail view, and review the associated events — what content matched, which rule fired, the user involved, and the action taken. This is the surface you use to triage and investigate DLP incidents.

    ![](./media/image72.png)

> [!NOTE]
> Alerts appear after a policy is enforced and a matching activity occurs, and can take time to surface after the event. If no alerts are present yet, generate one with the verification in the next task and return here. This timing is indicative, not guaranteed.

You have successfully reviewed the DLP alerts dashboard and an alert's detail.
## Summary

In this lab, you built Contoso Pharmaceuticals' data loss prevention across the paths that matter for exfiltration: a cloud and email policy spanning Exchange, SharePoint, and OneDrive, extended to Teams; and an Endpoint DLP policy restricting USB, clipboard, network-share, and print activities on onboarded devices. All of these detect Contoso's data using the sensitive information types and Exact Data Match classifier from Lab 2 and the sensitivity labels from Lab 4. You created a policy in the portal and another with PowerShell, followed the simulation-to-enforcement discipline, set policy priority, reviewed the DLP alerts surface, and proved that an enforced policy blocks a genuine exfiltration attempt while honoring a justified override. These policies stop sensitive data from leaving Contoso through everyday channels.

## Script notes

*Plain-English explanations of every command used in this lab, for verification by a non-technical reader. The code itself lives in the task steps; this section only explains it.*

### Task 4 — creating a DLP policy with PowerShell

```powershell
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName AllanD@TenantName
```

- **What it does:** Loads the management toolset and signs you in to Security & Compliance PowerShell, where DLP policies are managed.
- **To substitute:** replace `TenantName` with the tenant name from the Resources tab. Sign in as Allan Deyoung when the window appears.
- **What you should see:** the prompt returns with no red error text.

```powershell
New-DlpCompliancePolicy -Name "Block external consent forms" -Comment "Blocks external email containing Contoso consent forms." -ExchangeLocation All -Mode Enable
```

- **What it does:** Creates the DLP policy — the container for one or more rules. `New-DlpCompliancePolicy` is the command; `-Name` and `-Comment` label it.
- **The parameters, in plain English:** `-ExchangeLocation All` applies the policy to all mailboxes. `-Mode Enable` turns the policy on immediately (as opposed to `TestWithNotifications` or `TestWithoutNotifications`, which are the simulation modes).
- **What you should see:** the new policy's details with no red error text.

```powershell
New-DlpComplianceRule -Name "Block external consent form email" -Policy "Block external consent forms" -ContentContainsSensitiveInformation @{Name="Contoso Consent Form"} -AccessScope NotInOrganization -BlockAccess $true -BlockAccessScope All -NotifyUser Owner
```

- **What it does:** Adds a rule to the policy. A policy holds the rules that define what to detect and what to do.
- **The parameters, in plain English:** `-Policy` names the policy this rule belongs to. `-ContentContainsSensitiveInformation @{Name="Contoso Consent Form"}` is the trigger — content matching the consent-form fingerprint SIT from Lab 2. `-AccessScope NotInOrganization` limits the rule to content shared outside Contoso. `-BlockAccess $true` with `-BlockAccessScope All` blocks the sharing. `-NotifyUser Owner` notifies the content owner.
- **`@{Name="..."}`** is PowerShell's way of passing a named value (a hashtable) — here, the name of the sensitive information type.
- **What you should see:** the new rule's details with no red error text.

```powershell
Get-DlpComplianceRule -Identity "Block external consent form email" | Format-List Name, Policy, AccessScope, BlockAccess, ContentContainsSensitiveInformation
```

- **What it does:** Displays the rule so you can confirm it was created and configured correctly.
- **What you should see:** the rule's name, its policy, an access scope of `NotInOrganization`, `BlockAccess` of `True`, and the consent-form SIT listed as the condition.
- **To substitute:** nothing needs changing.