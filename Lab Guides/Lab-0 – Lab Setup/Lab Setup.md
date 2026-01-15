# Lab setup - Prepare your environment for administration

In this lab, you'll configure and prepare your environment for administration tasks. You'll enable required features, configure permissions, and prepare core services for administration.

**Tasks:**

- Enable Audit in the Microsoft Purview portal  
- Enable device onboarding  
- Enable insider risk analytics and data sharing  
- Initialize Microsoft Defender XDR
- Configure multi-factor authentication in Microsoft Entra
- Enabling Adaptive Protection

## Exercise 1 - Enable Audit in the Microsoft Purview portal

In this task, you'll enable Audit in the Microsoft Purview portal to monitor portal activities.

1. Log into VM with the **Admin** account credentials given in the Resources tab of your lab environment.

1. In **Microsoft Edge**, navigate to ```https://purview.microsoft.com``` and sign in as **MOD Administrator**, ```admin@TenantName``` (Tenant Name and Admin's password should be provided in the Resources tab of your lab environment.)

1. A message about the new Microsoft Purview portal will appear on the screen. Select **Get started** to access the new portal.

    ![](../media/image1.png)

1. Select **Solutions** from the left sidebar, then select **Audit**.

    ![](../media/image2.png)

1. On the **Search** page, select the **Start recording user and admin activity** bar to enable audit logging.

    ![](../media/image3.png)

1. Once you select this option, the blue bar should disappear from this page.

    ![](../media/image4.png)

You have successfully enabled auditing in Microsoft 365.

## Exercise 2 – Enable device onboarding

In this task, you'll enable device onboarding for your organization.

1. You should still be logged into the VM as the **admin** account and logged in as the MOD Administrator in Microsoft Purview.

1. Select **Settings** from the left sidebar, then expand **Device onboarding**.

1. On the **Device onboarding** page, select **Devices**.

    ![](../media/image5.png)

1. On the **Devices** page, select **Turn on device onboarding** then select **Ok** to confirm.

    ![](../media/image6.png)

1. When prompted, select **OK** to confirm that device monitoring is being turned on.

    ![](../media/image7.png)

You have now enabled device onboarding and can start to onboard devices to be protected with Endpoint DLP policies. The process of enabling the feature might take up to 30 minutes.

## Exercise 3 – Enable insider risk analytics and data sharing

In this task, you'll enable analytics and data sharing for Insider Risk Management.

1. In Microsoft Purview, navigate to **Settings** > **Insider Risk Management** > **Analytics**.

    ![](../media/image8.png)

1. Toggle these settings to **On**:

   - **Show insights at tenant level**

   - **Show insights at user level**

1. Select **Save** at the bottom of the page.

    ![](../media/image9.png)

1. Select **Data sharing** on the left navigation pane.

    ![](../media/image10.png)

1. In the Data sharing section, toggle **Share user risk details with other security solutions** to **On**.

1. Select **Save** at the bottom of the page.

    ![](../media/image11.png)

You have enabled analytics and data sharing for Insider Risk Management.

## Exercise 4 – Initialize Microsoft Defender XDR

In this task, you'll go to Microsoft Defender and wait for Microsoft Defender XDR to initialize.

1. In **Microsoft Edge**, navigate to ```https://security.microsoft.com/``` to open Microsoft Defender.

1. From the navigation pane, select **Investigation & response** > **Incidents & alerts** > **Incidents**.

    ![](../media/image12.png)

    > [!Note] **Note: Microsoft Defender XDR initialization**
    >
    > The Microsoft Defender XDR initialization screen might or might not appear depending on your lab tenant.

1. You'll see a message stating that Microsoft Defender XDR is being prepared. This process runs automatically and might take a few minutes.

    ![](../media/image13.png)

Microsoft Defender XDR is being initialized. You can continue with other tasks while it finishes setting up.

## Exercise 5 – Configure multi-factor authentication in Microsoft Entra

In this task, you'll configure multi-factor authentication (MFA) for the admin account to secure access to Microsoft Entra and other connected Microsoft 365 services.

1. In **Microsoft Edge**, navigate to ```https://entra.microsoft.com/``` to open Microsoft Entra and log in using the Admin credentials. On the 'Lets keep your account secure' prompt, Select **Next**.

    ![](../media/image14.png)

1. On the **Start by getting the app** screen, install the **Microsoft Authenticator** app from your device's app store, or open it if it's already installed. Select **Next**.

    ![](../media/image15.png)

   - If you prefer a different app, select **I want to use a different authenticator app** and follow the on-screen instructions.

1. On the **Set up your account** screen, follow the instructions on your phone to allow notifications, then select **Next**.  

    ![](../media/image16.png)

   - If you already have the Microsoft Authenticator app installed and configured, you might not see this screen. In that case, continue to the next step.

1. On the **Scan the QR code** screen, use the Microsoft Authenticator app on your device to scan the QR code displayed on your screen, then select **Next**.

    ![](../media/image17.png)

1. On your phone, approve the sign-in request by entering the number shown on your browser.

1. After approving the request, the **Notification approved** screen will appear. Select **Next**.

1. On the **Success!** screen, verify that your **Default sign-in method** shows **Microsoft Authenticator**, then select **Done**.

1. When prompted to sign in again, approve the sign-in request on your phone to verify your identity.

1. After the approval completes, you'll be redirected to the **Microsoft Entra admin center**.

You've successfully configured and verified multi-factor authentication for the admin account in Microsoft Entra.

## Exercise 6 – Enabling Adaptive Protection

1.	In Microsoft Edge, navigate to ```https://purview.microsoft.com``` and log into the perview portal as **MOD Administrator**.

2.	From the left navigation pane, select **Solutions** \> **Insider risk management** \> **User** \> **Adaptive Protection**. Then select **Dashboard**. Select **Quick setup**.
 
    ![](../media/image18.png)

3.	It will show a message saying we are setting things up. It will take 72 hours to enable it. We will use this in the 8th lab where we explore Adaptive Protection feature.

    ![](../media/image19.png)
 
4.	Select **Adaptive Protection settings** tab and switch on the **Adaptive Protection** toggle button. Select **Save**.

    ![](../media/image20.png)

You've successfully enabled Adaptive Protection in Microsoft Purview.
