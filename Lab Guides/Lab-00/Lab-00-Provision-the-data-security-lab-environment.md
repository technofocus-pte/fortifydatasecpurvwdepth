---
lab:
  title: Lab 0 — Provision the data-security lab environment
  description: In this lab we prepared the data-security lab environment by enabling auditing, onboarding devices, initializing Microsoft Defender and Insider Risk analytics, and connecting administrative PowerShell.
  duration: 20 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Microsoft 365
---

# Lab 0 — Provision the data-security lab environment

Before Contoso Pharmaceuticals can protect any data, its security team must turn on the platform capabilities that every later configuration depends on. Several of these features have long provisioning times — device onboarding, insider risk analytics, and Adaptive Protection can take from 30 minutes to 72 hours to become fully active — so they are enabled first, at the very start of the labs, and left to warm up while you work through the labs that don't depend on them yet.

In this lab you act as the Global Administrator (the **MOD Administrator** account) to prepare the tenant: you enable unified audit logging, turn on device onboarding, enable Insider Risk Management analytics and data sharing, initialize Microsoft Defender XDR, secure the administrator account with multi-factor authentication, and enable Adaptive Protection. No day-to-day compliance roles are assigned here — that happens in Lab 1. This lab is purely environment provisioning.

**Learning outcomes.** After this lab you can:

- Enable unified audit logging in the Microsoft Purview portal.
- Turn on device onboarding so endpoints can be protected by endpoint DLP policies later.
- Enable Insider Risk Management analytics and cross-solution data sharing.
- Initialize Microsoft Defender XDR.
- Configure multi-factor authentication for the administrator account in Microsoft Entra.
- Enable Adaptive Protection so risk-based controls become available in later labs.
- Create the security group that authorizes EDM data upload, allowing time for membership to propagate.

**Tasks**:

1. Enable auditing in the Microsoft Purview portal
2. Enable device onboarding
3. Enable Insider Risk Management analytics and data sharing
4. Initialize Microsoft Defender XDR
5. Configure multi-factor authentication in Microsoft Entra
6. Enable Adaptive Protection
7. Create the EDM data uploaders security group

> [!IMPORTANT]
> Several features enabled in this lab are intentionally turned on first because they take time to activate: device onboarding can take up to 30 minutes, Insider Risk analytics can take up to 24 hours to produce insights, and Adaptive Protection can take up to 72 hours to begin assigning risk levels. Enable them now and continue with other labs while they warm up. These timings are indicative, not guaranteed.

## Task 1 – Enable auditing in the Microsoft Purview portal

In this task, you'll enable unified audit logging so that user and administrator activity across the tenant is recorded and searchable. Auditing underpins the investigation, alerting, and verification steps in every later lab.

1. Log into the lab VM with the **Admin** account credentials given in the Resources tab of your lab environment.

2. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **MOD Administrator**, `admin@TenantName` (the Tenant Name and the Admin password are provided in the Resources tab of your lab environment).

	![](./media/image1.png)

	![](./media/image2.png)

3. If a message about the new Microsoft Purview portal appears, select **Get started** to access the portal. Close the introduction/walk-through pane.

	![](./media/image3.png)

	![](./media/image4.png)

4. In the left navigation, select **Solutions**, then select **Audit**.

	![](./media/image5.png)

5. On the **Audit** page, select the **Start recording user and admin activity** bar.

	![](./media/image6.png)

6. Confirm the blue bar disappears, which indicates auditing is now being enabled.

	![](./media/image7.png)

> [!NOTE]
> Enabling auditing can take up to 60 minutes to take effect, and audit events can take several hours after that before they become searchable. Auditing is often not enabled by default in trial tenants, so this step is required rather than confirmatory. These timings are indicative, not guaranteed.

You have successfully enabled unified audit logging for the tenant.

## Task 2 – Enable device onboarding

In this task, you'll enable device onboarding so that Windows endpoints can later be brought under management and protected by endpoint data loss prevention (DLP) policies. You only enable the capability here; onboarding an actual device happens in the DLP lab.

1. You should still be signed in to the Microsoft Purview portal as **MOD Administrator**.

2. In the left navigation select **Settings**, then expand **Device onboarding**.

3. On the **Device onboarding** page, select **Devices**.

	![](./media/image8.png)

4. On the **Devices** page, select **Turn on device onboarding**.

	![](./media/image9.png)

5. When prompted, select **OK** to confirm that device monitoring is being turned on.

	![](./media/image10.png)

	![](./media/image11.png)

> [!NOTE]
> The process of enabling device onboarding can take up to 30 minutes to complete. No device is onboarded yet — that happens in the DLP lab. This timing is indicative, not guaranteed.

You have successfully enabled device onboarding, so that endpoints can later be onboarded and protected by endpoint DLP policies.

## Task 3 – Enable Insider Risk Management analytics and data sharing

In this task, you'll enable analytics for Insider Risk Management, which produces tenant- and user-level risk insights, and enable data sharing so that user risk levels can be consumed by other security solutions — a prerequisite for Adaptive Protection later in the course.

1. In the Microsoft Purview portal, in the left navigation select **Settings**, then select **Insider Risk Management**, then choose **Analytics**.

2. Toggle both of these settings to **On**:

   - **Show insights at tenant level**
   - **Show insights at user level**

	![](./media/image12.png)

3. Select **Save** at the bottom of the page.

	![](./media/image13.png)

4. In the left navigation of the settings pane, select **Data sharing**.

5. Toggle **Share user risk details with other security solutions** to **On**.

6. Select **Save** at the bottom of the page.

	![](./media/image14.png)

> [!NOTE]
> Insider Risk analytics can take up to 24 hours to generate its first insights. Enabling it now lets it begin producing data before the Insider Risk and Adaptive Protection labs. This timing is indicative, not guaranteed.

You have successfully enabled Insider Risk Management analytics and cross-solution data sharing.

## Task 4 – Initialize Microsoft Defender XDR

In this task, you'll open Microsoft Defender and allow Microsoft Defender XDR to initialize. Defender XDR provides the incident and alert surface used alongside Purview in later investigation work.

1. In **Microsoft Edge**, navigate to **`https://security.microsoft.com/`** to open Microsoft Defender.

2. In the navigation pane, select **Incidents & alerts** > **Incidents**.

3. If a message states that Microsoft Defender XDR is being prepared, allow the process to run — it completes automatically and can take a few minutes.

	![](./media/image15.png)

> [!NOTE]
> The Microsoft Defender XDR initialization screen may or may not appear depending on your lab tenant. If it does, you can continue with other tasks while it finishes.

You have successfully started Microsoft Defender XDR initialization.

## Task 5 – Configure multi-factor authentication in Microsoft Entra

In this task, you'll secure the administrator account with multi-factor authentication (MFA) using the Microsoft Authenticator app. This step requires a mobile device with the Microsoft Authenticator app.

1. In **Microsoft Edge**, navigate to **`https://entra.microsoft.com/`** and sign in using the **Admin** credentials. On the **Let's keep your account secure** prompt, select **Next**.

	![](./media/image16.png)

2. On the **Start by getting the app** screen, install the **Microsoft Authenticator** app from your device's app store, or open it if it's already installed, then select **Next**. If you prefer a different app, select **I want to use a different authenticator app** and follow the on-screen instructions.

	![](./media/image17.png)

3. On the **Set up your account** screen, follow the instructions on your phone to allow notifications, then select **Next**. If Microsoft Authenticator is already installed and configured, you may not see this screen — continue to the next step.

	![](./media/image18.png)

4. On the **Scan the QR code** screen, use the Microsoft Authenticator app to scan the QR code displayed, then select **Next**.

5. On your phone, approve the sign-in request by entering the number shown in your browser.

6. On the **Notification approved** screen, select **Next**.

7. On the **Success!** screen, verify that your **Default sign-in method** shows **Microsoft Authenticator**, then select **Done**.

8. When prompted to sign in again, approve the sign-in request on your phone to verify your identity.

9. Select **Done**. Confirm you are redirected to the Microsoft Entra admin center.

	![](./media/image19.png)

You have successfully configured and verified multi-factor authentication for the administrator account.

## Task 6 – Enable Adaptive Protection

In this task, you'll enable Adaptive Protection, which links Insider Risk Management with DLP so that controls can be applied dynamically based on a user's risk level. You enable it now because it can take up to 72 hours to begin assigning risk levels; the Adaptive Protection lab later in the course relies on it being active.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **MOD Administrator**.

2. In the left navigation, select **Solutions** > **Insider Risk Management** > **User** > **Adaptive Protection**, then select **Dashboard**.

3. Select **Quick setup**. A message indicates that Adaptive Protection is being set up.

	![](./media/image20.png)

4. Select the **Adaptive Protection settings** tab, toggle **Adaptive Protection** to **On**, then select **Save**. If you do not see the **Adaptive Protection settings** tab, refresh the page.

	![](./media/image21.png)

> [!IMPORTANT]
> Adaptive Protection can take up to 72 hours to become fully active and begin assigning risk levels to users. If risk levels are not assigned, risk-based DLP rules will not apply. Enabling it now, at the start of the course, ensures it is ready by the time you reach the Adaptive Protection lab. This timing is indicative, not guaranteed.

You have successfully enabled Adaptive Protection, so that risk-based controls become available in later labs.

## Task 7 – Create the EDM data uploaders security group

In this task, you'll create the security group that authorizes users to hash and upload Exact Data Match (EDM) source data. You create it now, during setup, so that its membership has time to propagate before the sensitive-information-types lab uses it. You perform this task as the Global Administrator.

1. Open **Microsoft Edge** in a new **InPrivate** window, navigate to **`https://admin.microsoft.com`**, and sign in as **MOD Administrator**, `admin@TenantName`.

2. In the Microsoft 365 admin center, in the left navigation, expand **Teams & groups**, then select **Active teams & groups**.

	![](./media/image22.png)

3. Select the **Security groups** tab, then select **+ Add a security group**.

	![](./media/image23.png)

4. On the **Set up the basics** page, enter the following, then select **Next**:

   - **Name**: `EDM_DataUploaders`
   - **Description**: `Users authorized to hash and upload EDM source data.`

	![](./media/image24.png)

5. Leave the default settings, select **Next**, then select **Create group**.

	![](./media/image25.png)

	![](./media/image26.png)

6. Select **Close**.

	![](./media/image27.png)

7. On the **Active teams & groups** page, select the **Security groups** tab, then select **Refresh**.

8. Select the **EDM_DataUploaders** group.

	![](./media/image28.png)

9. Select the **Members** tab, then select **View all and manage owners**.

	![](./media/image29.png)

10. Select **+ Add owners**, select the checkbox next to **MOD Administrator**, then select **Add**. Select **Back**.

	![](./media/image30.png)

	![](./media/image31.png)

	![](./media/image32.png)

11. Select the **Members** tab, then select **View all and manage members**.

	![](./media/image33.png)

12. Select **+ Add members**, select the checkbox next to **Allan Deyoung**, then select **Add**.

	![](./media/image34.png)

	![](./media/image35.png)

13. Close the flyout, then close the InPrivate window.

	![](./media/image36.png)

> [!IMPORTANT]
> The `EDM_DataUploaders` group name must be exactly as shown, because the EDM Upload Agent checks membership in this specific group when you reach the sensitive-information-types lab. Group membership can take time to propagate; if the EDM upload later fails with a permissions error, wait and retry.

You have successfully created the EDM data uploaders security group and added Allan Deyoung as a member, giving its membership time to propagate before it is needed.

## Summary

In this lab, you provisioned the Contoso Pharmaceuticals data-security environment by enabling unified audit logging, device onboarding, Insider Risk Management analytics and data sharing, Microsoft Defender XDR, administrator multi-factor authentication, and Adaptive Protection, and by creating the EDM data uploaders security group. Because several of these features and group memberships take from 30 minutes to 72 hours to activate or propagate, enabling them first allows them to warm up while you complete the labs that follow. The tenant is now ready for role assignment and the data-protection work that begins in Lab 1.