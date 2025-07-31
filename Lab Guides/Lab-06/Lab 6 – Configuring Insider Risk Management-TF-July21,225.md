# **Lab 6 – Configuring Insider Risk Management**

## Introduction

In this lab, we will learn how to configure Insider Risk Management using
the Insider Risk Management Policies. We will use the Sensitive Info
Types that we created in Lab 1 and DLP policies that we created in Lab 4
to create policies which will secure the organisation against risky
browser usage or any data theft or leaks.

To do this, we will create an infrastructure in Azure that will represent
the devices in an organisation. We will learn how to onboard those
devices in Azure AD and Intune, and install an MDM agent on them, so
that they can be used to get the alerts from those machines.

## Objectives

- Synchronize VM clocks to ensure accurate time settings for policy
  testing.

- Assign users to the Insider Risk Management role group in Microsoft
  Purview.

- Enable analytics insights for insider risk detection at tenant and
  user levels.

- Onboard Windows 10 devices to Microsoft Defender for Endpoint for
  insider risk monitoring.

- Create and configure Insider Risk Management policies for:

  - Risky browser usage

  - Data theft by departing users

  - Data leaks by users

- Score each policy to simulate insider risk detection scenarios for the
  MOD administrator account.

## Exercise 1: Set up the environment

### Task 0: Synchronize the VM clock

1.  Close all the tabs of Microsoft Edge browser that are opened on your VM. Click on the **Windows** icon, then click on **Settings** as shown
    in the below image.

    ![](./media/image1.png)

2.  On the **Windows Settings** search bar, type **+++data and time+++**
    then select **Date & time settings** from the list.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image2.png)

3.  In the **Date & time** page, navigate and click on the **Syn now**
    button.

    ![](./media/image3.png)

## Exercise 2: Create Insider Risk Management policies.

### Prerequisites

#### Step 1 – Add users to Insider risk management role group

1.  If the Microsoft Purview portal is opened, then continue with step
    2, otherwise, open the **+++https://purview.microsoft.com+++** and
    log in with the **MOD Administrator** credentials.

2.  In the left-sided navigation menu, click on **Settings.**

    ![](./media/image4.png)

3.  In the **Settings** pane, navigate and click on **Roles and
    scopes**. Click on **Role groups**, then select the checkbox beside
    **Insider Risk Management** and click on the pencil icon to Edit.

    ![](./media/image5.png)

    ![](./media/image6.png)

4.  On the **Edit Members of the role group** page, click on **Choose
    users**.

    ![](./media/image7.png)

5.  Select the checkbox near **Alex Wilber**. Then, click on the
    **Select** button.

**Note**: In case, you did not see Megan Bowen and MOD Administrator
names in the Edit members name, then in addition to Alex name, select
Megan Bowen and MOD administrator names also.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image8.png)

6.  Ensure that MOD Administrator, Megan Bowen, and Alex Wilber name is
    displayed, then click on the **Next** button.

    ![](./media/image9.png)

7.  Select **Save** to add the users to the role group.

    ![A screenshot of a computer Description automatically generated](./media/image10.png)

8.  Select **Done** to complete the steps.

    ![A screenshot of a computer Description automatically generated](./media/image11.png)

#### Step 2 – Enable insider risk analytics insights

1.  In the Microsoft Purview portal, navigate to **Settings**, then
    scroll down and click on **Insider risk management**. On **Insider
    Risk Management settings** – **Analytics** page, turn on the toggle
    of **Show insights at tenant level** and **Show insights at user
    level**. Then, click on the **Save** button.

    ![](./media/image12.png)

### Step 3 – Onboarding a device

In this deployment scenario, you'll onboard devices that hasn't been
onboarded yet, and you just want to detect insider risk activities on
Windows 10 devices.

We need to register our device/VM in Microsoft Entra ID as a
prerequisite to creating any Insider Risk Policy.

1.  Click on Windows icon, then select **Settings** as shown in the
    below image.

    ![](./media/image13.png)

2.  Go to **Accounts** \> **Access work or school**. On the **Access
    work or school** page, click on **Connect**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image14.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image15.png)

3.  In the **Set up a work or school account** prompt, click on **Join
    this device to Microsoft Entra ID**.

    ![](./media/image16.png)

4.  In the sign in prompt, sign in with **MOD
    Administrator** credentials given on the resources tab of your lab
    environment.

    ![](./media/image17.png)

    ![](./media/image18.png)

5.  On **Make sure this is your organisation** dialog box, click on the
    **Join** button.

    ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image19.png)

6.  Once done you will see a confirmation window **You're all set!**.
    Click on **Done**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image20.png)

7.  Again, on the **Access work or school** page, click on **Connect**.

    ![](./media/image21.png)

8.  In the **Set up a work or school account** prompt, login using MOD
    administrator credentials.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

9.  On **Stay signed in?** dialog box, click on the **Yes** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image24.png)

10. If **Setting up your device** dialog box appears, then select **Got
    it**.

    ![A screenshot of a computer Description automatically generated](./media/image25.png)

11. Now go to **windows settings** \> **Accounts** \> **Access work or
    school** \> **Connected to Contoso MDM** \> **Info** \> **Sync**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image27.png)

12. Click on the windows symbol on your VM. Select the
    user **Admin** and select **Sign out**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image28.png)

13. On the user screen select **Other user**.

    ![A screenshot of a computer Description automatically generated with medium confidence](./media/image29.png)

14. Enter your O365 credentials given on the home page of your lab
    environment and log into the VM as **MOD Administrator**.

    ![A screenshot of a login screen AI-generated content may be incorrect.](./media/image30.png)

15. Sign in to +++**https://security.microsoft.com/+++** using
    your **MOD Administrator** account on your Lab VM.

16. Select **Settings** \> **Device** **onboarding \> Devices**. Click
    on **Turn on Device onboarding**.

  ![A screenshot of a computer AI-generated content may be incorrect.](./media/image31.png)

  ![A screenshot of a computer AI-generated content may be incorrect.](./media/image32.png)

17. On **Turn on device onboarding** dialog box, click on the **OK**
    button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image33.png)

18. On **Device monitoring is being turned on** dialog box, click on the
    **OK** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image34.png)

19. Wait for few minutes, then refresh the page.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image35.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image36.png)

20. From the **settings** \> **Device onboarding** \> **Onboarding**.
    Click on **Download package**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image37.png)

21. Once downloaded, copy the file to the desktop. Right click the file
    and **Extract all…**, then click on the **Extract** button

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image38.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image39.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image40.png)

22. Once done, open the folder and run the file
    with **Administrator** rights.

    ![A computer screen with a computer screen Description automatically generated](./media/image41.png)

23. If **Search for app in the Store?** dialog box appears, then click
    on the **Yes** button, else ignore.

24. On **The publisher could not be verified. Are you sure you want to
    run this software?** dialog box, click on the **Run** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image42.png)

25. If **User Account Control** dialog box appears, then click on the
    **Yes** button.

     ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image43.png)

27. In the Command Prompt, press **Y** and press enter to confirm. You
    will receive a message that the device is onboarded. In the Command
    Prompt once you get the message, **Press any key to continue . .
    .**, press any key.

    ![A screenshot of a computer error Description automatically generated](./media/image44.png)

27. Once the Command Prompt is closed, open Command Prompt in
    administrator mode by typing **cmd** in Windows search bar, then
    right click on **Command Prompt** and select **Run as
    administrator**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image45.png)

28. On **User Account Control** dialog box, click on the Yes button.

    ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image43.png)

29. Run a detection test by running the following command. The Command
    Prompt window will close automatically.

    **+++powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'+++**

    ![Text Description automatically generated](./media/image46.png)

30. Close the VM connection.

31. Open the **settings** by clicking on the settings in the navigation
    and choose **Devices Onboarding** \> **Devices**.

    **Note:** While it usually takes about 60 seconds for device onboarding to be enabled, please allow up to 30 minutes.

32. You will be able to check the **Devices** list. The list will be
    empty until you onboard devices, once done, you will be able to see
    your VMs listed as the onboarded device.

### Task 1: Creating an organisation wide policy to detect and score Risky Browser Usage

#### Step 1 – Create a new policy

1.  In Microsoft Purview portal, click on Solutions, then click on
    **Insider Risk Management** ![](./media/image47.png)

2.  Click on **Policies**. In the Policies page, click on **+Create
    policy \> Custom policy**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image48.png)

3.  On the Choose a policy template page, choose Risky browser usage
    (preview), under Risky browser usage (preview).

    ![A screenshot of a computer Description automatically generated](./media/image49.png)

4.  Review all the prerequisites.

    ![A screenshot of a computer Description automatically generated](./media/image50.png)

5.  Select **Next** to continue.

    ![A screenshot of a computer Description automatically generated](./media/image51.png)

6.  On the **Name and description** page, complete the following fields:

    - Name (required): Risky usage of browser

    - Description (optional): This is a test policy for the risky
      browser usage.

7.  Select **Next** to continue.

    ![Graphical user interface, text, application Description automatically generated](./media/image52.png)

8.  On the Choose users and groups page, select Include all users and
    groups. Select Next to continue.

    ![Graphical user interface, text, application Description automatically generated](./media/image52.png)

9.  On the **Choose users, groups, & adaptive scopes** page,
    select **All users, groups, & adaptive scopes**. Select **Next** to
    continue.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image53.png)

10. On the **Exclude users and groups** page, select **Next**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image54.png)

11. On the Decide whether to prioritize page, select I don't want to
    specify priority content right now (you'll be able to do this after
    the policy is created). Select Next to continue.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image55.png)

12. On the Triggers for this policy page, select Turn on indicators.

    ![A screenshot of a computer Description automatically generated](./media/image56.png)

13. On **Turn on indicators for your organization** dialog box, scroll
    down and click on **Choose indicators to turn on** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image57.png)

    ![](./media/image58.png)

14. On **Choose indicators to turn on** dialog box, ensure that
    under Risky browsing indicators (preview) all the indicators are
    selected.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image59.png)

    ![A screenshot of a computer Description automatically generated](./media/image60.png)

15. Scroll down and select **Save**.

16. On **Choose triggering event for this policy** page, ensure that the
    radio button beside **User browsed to a potentially risky website**
    is selected. Under **Select which activities will trigger this
    policy**, select all the options and click on the **Next** button.

    ![Graphical user interface, text, application Description automatically generated](./media/image61.png)

17. On **Choose thresholds for triggering events** page, select **Choose
    your own thresholds** radio button, change all the thresholds to 1
    per day and then select **Next**.

    ![](./media/image62.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image63.png)

18. On **indicators** page, select **Next**.

    ![A screenshot of a computer Description automatically generated](./media/image64.png)

19. On **Choose threshold type for indicators** page, ensure that
    **Apply thresholds provided by Microsoft** is selected, then click
    on the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image65.png)

20. On **Review settings and finish** page, select **Submit**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image66.png)

21. On **Your policy was created** page, select **Done**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image67.png)

22. Keep the tab open and continue to the next task.

#### Step 2 – Score the policy

1.  Click on the new policy named Risky usage of browser. Select **Start
    scoring activity for users**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image68.png)

2.  In the Reason for scoring activity field, type **Testing the
    policy**. In **Scoring activity for this many days (between 5 and
    30)** field, select **10 days**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image69.png)

3.  In Score activity for these users field, type MOD and then select
    MOD administrator.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image70.png)

4.  Then, click on **Start scoring activity** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image71.png)

5.  Click on the **Close** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image72.png)

### Task 2: Data theft by departing users

#### Step 1 – Create a new policy

1.  In the **Policies** page, click on **+ Create policy**, then select
    **Custom policy**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image73.png)

2.  On the Choose a policy template page, choose Data theft by departing
    users, under Data theft. Select Next to continue.

    ![A screenshot of a computer Description automatically generated](./media/image74.png)

3.  On the **Name and description** page, complete the following fields:

    - Name (required): Data theft by a user

    - Description (optional): This is a test policy forthe preventing
      data theft.

4.  Select **Next** to continue.

    ![A screenshot of a computer Description automatically generated](./media/image75.png)

5.  On the Choose users and groups page, select Include all users and
    groups. Select Next to continue.

    ![A screenshot of a computer Description automaticall generated](./media/image76.png)

6.  On the Decide whether to prioritize page, select I want to specify
    priority content. Select only the check box for Sensitivity
    labels and Sensitive info types. Select Next to continue.

    ![A screenshot of a computer screen Description automatically generated with medium confidence](./media/image77.png)

7.  On the Sensitivity labels to prioritize page, select Add or edit
    sensitivity labels. On Add or edit sensitivity labels search bar,
    type employee and press the enter button, select Internal/Employee
    data (HR) and select Add. Then click Next.

    ![A screenshot of a computer screen Description automatically generated with medium confidence](./media/image78.png)

8.  On the Sensitive info types to prioritize page, select Add or edit
    sensitive info types. On the flyout pane, search for and
    select Credit Card Number, Contoso Employee ID and Contoso Employee
    EDM. Select Add. Then click Next.

    ![A screenshot of a computer Description automaticall generated](./media/image79.png)

9.  On Decide whether to score only activity with priority content,
    select Get alerts for all activity. Select Next.

    ![A screenshot of a computer screen Description automatically generated with medium confidence](./media/image80.png)

10. On **Choose triggering event for this policy** page, keep the
    default selection and select **Next**.

    ![](./media/image81.png)

11. On **Indicators** page, click on the dropdown beside **Office
    indicators (31/31 selected)**.

    ![A screenshot of a computer AI-generated content may b incorrect.](./media/image82.png)

12. Ensure that all the Office indicators are selected, then click on
    the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image83.png)

13. Keep all the parameters on the **Detection options** page in the
    default state and click on the **Next** button

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image84.png)

14. On **Choose threshold type for indicators** page, select the radio
    button beside **Choose your own thresholds**, then scroll down and
    click on Office indicators dropdown.

    ![](./media/image85.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image86.png)

15. Under Sharing SharePoint files with people outside the
    organizzation, use 1, 2, and 3 events for each stage respectively
    then select Next.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image87.png)

16. On **Review settings and finish** page, click on the **Submit**
    button.

    ![](./media/image88.png)

17. On Your policy was created, select Done.

    ![](./media/image89.png)

#### Step 2 – Score the policy

1.  Click on the new policy named Data theft by a user. Select Start
    scoring activity for users.

    ![](./media/image90.png)

2.  In the Reason for scoring activity field, type **Testing the
    policy**. In **Scoring activity for this many days (between 5 and
    30)** field, select **10 days**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image69.png)

3.  In Score activity for these users field, type MOD and then select
    MOD administrator.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image70.png)

4.  Then, click on **Start scoring activity** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image71.png)

5.  Click on the **Close** button.

    ![](./media/image91.png)

### Task 3: Data leaks by users

#### Step 1 – Create a new policy

1.  In the **Policies** page, click on **+ Create policy**, then select
    **Custom policy**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image73.png)

2.  On the **Choose a policy template** page, choose **Data leaks**,
    under **Data leaks**. Select **Next** to continue.

    ![A screenshot of a computer Description automatically generated](./media/image92.png)

3.  On the **Name and description** page, complete the following fields:

    - Name: Data leaks by a user

    - Description: This is a test policy forthe preventing data leaks.

4.  Select **Next** to continue.

    ![A screenshot of a computer Description automatically generated](./media/image93.png)

5.  On **Choose users, groups, & adaptive scopes** page, ensure that
    **All users, groups, and adaptive scopes** radio button is selected.
    Then, click on the **Next** button to continue.

    ![](./media/image94.png)

6.  On the Decide whether to prioritize page, select I want to specify
    priority content. Select the check box for SharePoint
    sites, Sensitivity labels and Sensitive info types. Select Next to
    continue.

    ![A screenshot of a computer Description automatically generated wit medium confidence](./media/image95.png)

7.  On the SharePoint sites to prioritize page, select **Add or edit
    SharePoint sites**. On the flyout pane,
    select **https://wwlxXXXXXX.sharepoint.com/sites/ContosoWeb1** and
    select **Add**. Then, click **Next**.

    **Note**: Tenant Prefix is available in the **Resources** tab.

    ![](./media/image96.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image97.png)

    ![](./media/image98.png)

8.  On the Sensitivity labels to prioritize page, select **Add or edit
    sensitivity labels**. On the flyout pane, type **+++employee+++**
    and then select Internal/Employee data (HR) checkbox and click on
    the **Add** button. Then, click on the **Next** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image99.png)

    ![](./media/image100.png)

9.  On the Sensitive info types to prioritize page, select Add or edit
    sensitive info types. On the flyout pane, search for and
    select Credit Card Number, Contoso Employee ID and Contoso Employee
    EDM. Select Add. Then click Next.

    ![A screenshot of a computer Description automatically generated](./media/image79.png)

10. On Decide whether to score only activity with priority content,
    select Get alerts for all activity. Select Next.

    ![](./media/image101.png)

11. On **Choose triggering event for this policy** page, ensure that the
    radio button for **User performs an exfiltration activity** is
    selected. Under **Select which activities will trigger this
    policy**, select **Download content from SharePoint, Sending email
    with attachments to recipients outside the organisation**, **Sharing
    SharePoint files with people outside the organization**, then
    select **Next**.

    ![](./media/image102.png)

    ![](./media/image103.png)

12. On Triggering thresholds for this policy, select Use custom
    thresholds. Set every threshold to 1 and select Next.

    ![](./media/image104.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image105.png)

13. Keep the default settings on the **Indicators** page and
    select **Next**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image106.png)

14. Keep the default settings on the **Detection options** page and
    select **Next**.

    ![](./media/image107.png)

15. On **Choose threshold type for indicators** page, ensure that the
    **Choose your own thresholds** radio button is selected. Then, click
    on Office indicators, use 1, 2, and 3 events for each stage
    respectively then select **Next**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image108.png)

    ![](./media/image109.png)

    ![](./media/image110.png)

16. On **Review settings and finish**, select **Submit**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image111.png)

17. On Your policy was created, select Done.

    ![](./media/image112.png)

#### Step 2 – Score the policy

1.  In the Policies page, select the checkbox beside the new policy
    named Data leaks by a user. Then, select **Start scoring activity
    for users**.

    ![](./media/image113.png)

2.  In the Reason for scoring activity field, type **Testing the
    policy**. In **Scoring activity for this many days (between 5 and
    30)** field, select **10 days**. In Score activity for these users
    field, type MOD and then select MOD administrator.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image69.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image70.png)

3.  Then, click on **Start scoring activity** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image71.png)

4.  Click on the **Close** button.

    ![](./media/image114.png)

## Summary:

In this lab, you first prepared the environment by synchronizing VM
clocks and onboarding required users and devices for Insider Risk
Management in Microsoft Purview. You enabled analytics insights and
verified the Defender antimalware client version on all target VMs.
After onboarding the devices, you created three different Insider Risk
Management policies to monitor and score activities related to risky
browser usage, potential data theft by departing users, and data leaks
by internal users. Each policy was customized with sensitivity labels,
SharePoint sites, and sensitive information types as priority content,
and thresholds were configured to trigger alerts and scoring. Finally,
you initiated scoring activities to simulate real-world insider risk
scenarios and assess the effectiveness of the configured policies.
