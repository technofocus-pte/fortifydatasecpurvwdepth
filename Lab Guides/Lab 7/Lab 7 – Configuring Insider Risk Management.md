# Lab 7 – Configuring Insider Risk Management

## Objective:

In this lab we will learn how to configure Insider Risk Management using
the Insider Risk Management Policies. We will use the Sensitive Info
Types that we created in Lab 2 and DLP policies that we created in Lab 5
to create policies which will secure the organisation against risky
browser usage or any data theft or leaks.

To do this we will create an infrastructure in Azure that will represent
the devices in an organisation. We will learn how to onboard those
devices in Azure AD and Intune, and install an MDM agent on them, so
that they can be used to get the alerts from those machines.

## Exercise 1: Synchronize the VM clock

1.  After logging into the VM, select the windows icon. Then search
    for **Date and time**, and select **Date and time settings**.

![A screenshot of a computer Description automatically
generated](./media/image1.jpeg)

2.  On the Settings screen that opens up, click on the **Sync
    now** under Additional settings.

![A screenshot of a computer Description automatically
generated](./media/image2.jpeg)

3.  This takes care of synchronizing the time just in case the automatic
    synchronization does not work.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image3.png)

## Exercise 2: Create Insider Risk Management policies.

### Prerequisites

#### Step 1 – Add users to Insider risk management role group

1.  If the Microsoft Purview portal is open continue to step 2,
    otherwise, open the ```https://purview.microsoft.com ``` and log
    in with the **MOD Administrator** credentials.

![](./media/image54.png)

2.  In the navigation select **Settings**, and select **Role groups**
    under **Role groups**, select **Insider Risk Management**. Then
    select **Edit**. On the side pane, again select **Edit**

![](./media/image55.png)

3.  On the **Edit Members of the role group** page, select **Choose
    users**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

4.  Select the checkbox near **MOD Admin**, **Patti**, **Megan** and **Alex**. Then
    choose **Select**.

![](./media/image62.png)

5. Then select **Next**.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

6. Select **Save** to add the users to the role group.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

7. Select **Done** to complete the steps.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

#### Step 2 – Enable insider risk analytics insights

1.  In the Microsoft Purview portal. Navigate to **Settings**, go
    to **Insider risk management**. Go to **Analytics**, and enable the
    radio button, and click on **Save**.

![](./media/image70.png)

#### Step 3 – Onboarding a device

In this deployment scenario, you'll onboard devices that hasn't been
onboarded yet, and you just want to detect insider risk activities on
Windows 10 devices.

We need to register our device/VM in Microsoft Entra ID as a prerequisite to creating any Insider Risk Policy.

1.  Open windows **Setting** on your VM.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  Go to **Accounts** \> **Access work or school**. On the **Access work or school** page, click on **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

3.  In the **Set up a work or school account** prompt, click on **Join
    this device to Microsoft Entra ID**.

![](./media/image16.png)

4.  In the sign in prompt, sign in with **MOD
    Administrator** credentials given on the resources tab of your lab
    environment. 

![A screenshot of a computer Description automatically
generated](./media/image17.png)

![Graphical user interface, application, PowerPoint Description
automatically generated](./media/image18.png)

5.  Press **Join** in the prompt **Make sure this is your organisation**.

![Graphical user interface, text, application Description automatically
generated](./media/image19.png)

6.  Once done you will see a confirmation window **You’re all set!**.
    Click on **Done**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

7.  Again go to **Accounts** \> **Access work or school**. On the **Access work or school** page, click on **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

8. In the **Set up a work or school account** prompt, use the MOD admin credentials to log in.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

9. On the **Setting up your device** page, select **Got it**.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

10. Now go to **windows settings** > **Accounts** > **Access work or school** > **Connected to Contoso MDM** > **Info** > **Sync**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

![A screenshot of a computer Description automatically
generated](./media/image24.png)

11. Click on the windows symbol on your VM. Select the
    user **Admin** and select **Sign out**.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

12.  On the user screen select **Other user**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image26.png)

13. Enter your O365 credentials given on the home page of your lab
    environment and log into the VM as **MOD Administrator**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image27.png)

14. Close the windows settings app. Sign in to  ```https://purview.microsoft.com``` using
    your **MOD Administrator** account on your Lab VM.

15. Select **Settings** \> **Device onboarding** > **Devices**.

![](./media/image80.png)

16. Click on **Turn on Device onboarding**.

![A screenshot of a computer Description automatically
generated](./media/image82.png)

17. From the **Settings** \> **Device onboarding** \> **Onboarding**.
    Click on **Download package**.

![A screenshot of a computer Description automatically
generated](./media/image83.png)

18. Right click the file and **Extract all…** .

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image86.png)

![A screenshot of a computer Description automatically
generated](./media/image87.png)

19. Once done open the folder and run the file
    with **Administrator** rights.

![A computer screen with a computer screen Description automatically
generated](./media/image88.png)

20. Click on **More info**.

![Graphical user interface, application Description automatically
generated](./media/image89.png)

21. Click on **Run anyway**.

![A screenshot of a computer error Description automatically
generated](./media/image90.png)

22. In the Command Prompt, press **Y** and press enter to confirm and
    continue when prompted.

![A screenshot of a computer error Description automatically
generated](./media/image91.png)

23. You will receive a message that the device is onboarded. In the
    Command Prompt once you get the message, **Press any key to continue
    ...**, press any key.

24. Once the Command Prompt is closed, open Command Prompt in
    administrator mode to run a detection test and at the prompt, copy
    and run the command below. The Command Prompt window will close
    automatically.

```powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'```

![Text Description automatically generated](./media/image92.png)

25. Open the **settings** by clicking on the settings in the navigation
    and choose **Devices Onboarding** \> **Devices**.

**Note:** While it usually takes about 60 seconds for device onboarding
to be enabled, please allow up to 30 minutes.

26. You will be able to check the **Devices** list. The list will be
    empty until you onboard devices, once done, you will be able to see
    your VMs listed as the onboarded device.

### Task 1: Creating an organisation wide policy to detect and score Risky Browser Usage

#### Step 1 – Create a new policy

1.  If you closed the browser window in the previous task, open
    the ```https://purview.microsoft.com ``` and log in with the
    Admin credentials.

2.  Go to **Insider Risk Management** and select
    the **Policies** tab. Select **Create policy** to open the policy
    wizard.

![](./media/image100.png)

3.  On the **Choose a policy template** page, choose **Risky browser usage
    (preview)**, under **Risky browser usage (preview)**.

![A screenshot of a computer Description automatically
generated](./media/image102.png)

4.  Make sure that all the prerequisites are met.

![A screenshot of a computer Description automatically
generated](./media/image103.png)

5.  Select **Next** to continue.

![A screenshot of a computer Description automatically
generated](./media/image104.png)

6.  On the **Name and description** page, complete the following fields:

    - Name (required): ```Risky usage of browser```

    - Description (optional): ```This is a test policy for the risky browser usage.```

7.  Select **Next** to continue.

![Graphical user interface, text, application Description automatically
generated](./media/image105.png)

8.  On the **Choose users, groups, & adaptive scopes** page, select **All users, groups, & adaptive scopes**. Select **Next** to continue.

9.   On the **Exclude users and groups** page, select **Next**.

10.  On the **Decide whether to prioritize** page, select **I don't want to
    specify priority content right now** (you'll be able to do this after
    the policy is created). Select **Next** to continue.

![Graphical user interface, text, application Description automatically
generated](./media/image107.png)

11. On the **Triggers for this policy** page, select **Turn on indicators**.

![A screenshot of a computer Description automatically
generated](./media/image108.png)

12. On **Choose indicators to turn on**, select **Select all under Risky
    browsing indicators (preview)**, and uncheck rest of the boxes.

![A screenshot of a computer Description automatically
generated](./media/image109.png)

13. Scroll down and select **Save**.

14. On **Triggers for this policy**, under **Select which activities will
    trigger this policy**. Select all the options and click on **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image110.png)

15. On **Triggering thresholds for this policy** page, select **Use custom
    thresholds (Recommended)**, change all the thresholds to **1** per day and
    then select **Next**.

![Graphical user interface, application Description automatically
generated](./media/image111.png)

![A screenshot of a computer Description automatically
generated](./media/image112.png)

16. On **indicators** page, select **Next**.

![A screenshot of a computer Description automatically
generated](./media/image113.png)

17. On **Decide whether to use default or custom indicator thresholds**,
    select **Use default thresholds for all indicators**, then select **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image114.png)

18. On **Review settings and finish**, select **Submit**.

![Graphical user interface, text, application Description automatically
generated](./media/image115.png)

19. On **Your policy was created**, select **Done**.

![A screenshot of a computer Description automatically
generated](./media/image116.png)

20. Keep the tab open and continue to the next task.

#### Step 2 – Score the policy

1.  Click on the new policy named **Risky usage of browser**. Select **Start
    scoring activity for users**.

![A screenshot of a computer Description automatically
generated](./media/image117.png)

2.  In the **Reason** field in the **Add users to multiple policies** pane,
    type **Testing the policy**.

![A screenshot of a computer Description automatically
generated](./media/image118.png)

3.  In the **This should last for (choose between 5 and 30 days)** field,
    select **10** days.

4.  Use the **Search user to add to policies** field. Add **MOD Admin**. Then click on **Start scoring activity**.

5.  Once you get the confirmation that you have started **Scoring
    activity for 1 users**, click **Close**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image120.png)

### Task 2: Data theft by departing users

#### Step 1 – Create a new policy

1.  If you closed the browser window in the previous task, open
    the ```https://purview.microsoft.com ``` and log in with the admin credentials.

2.  Go to **Insider Risk Management** and select the **Policies** tab.
    Select **Create policy** to open the policy wizard.

![](./media/image100.png)

3.  On the Choose a policy template page, choose Data theft by departing
    users, under Data theft. Select Next to continue.

![A screenshot of a computer Description automatically
generated](./media/image121.png)

4.  On the **Name and description** page, complete the following fields:

    - Name (required): ```Data theft by a user```

    - Description (optional): ```This is a test policy for the preventing data theft.```

5.  Select **Next** to continue.

![A screenshot of a computer Description automatically
generated](./media/image122.png)

6.  On the **Choose users, groups, & adaptive scopes** page, select **All users, groups, & adaptive scopes**. Select **Next** to continue.

7.  On the **Exclude users, groups, & adaptive scopes** page, select **Next**.

9.  On the **Decide whether to prioritize** page, select **I want to specify
    priority content**. Select the check box for **Sensitivity
    labels** and **Sensitive info types**. Select **Next** to continue.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image123.png)

9.  On the **Sensitivity labels to prioritize** page, select **Add or edit
    sensitivity labels**. On the flyout pane, select **Internal/Employee
    data (HR)** and select **Add**. Then click **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image124.png)

10.  On the **Sensitive info types to prioritize** page, select **Add or edit
    sensitive info types**. On the flyout pane, search for and
    select **Credit Card Number**, **Contoso Employee ID** and **Contoso Employee
    EDM**. Select **Add**. Then click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image125.png)

11.  On **Decide whether to score only activity with priority content**,
    select **Get alerts for all activity**. Select **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image126.png)

12.  On triggers for this policy page, select the default and then
    select Next.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image127.png)

13.  On **Indicators** page, select **Turn on indicators** from the
    prompt.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image128.png)

14. Select **Select all under Office indicators** and click **Save**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image129.png)

15. Select all the options and click on **Next**.

![A screenshot of a computer Description automatically
generated](./media/image130.png)

16. On **Detection options** page, select the default and then
    select **Next**.

![A screenshot of a computer Description automatically
generated](./media/image131.png)

17. On **indicators** page, select **Next**.

![A screenshot of a computer Description automatically
generated](./media/image113.png)

18. On **Decide whether to use default or custom indicator thresholds**,
    select **Customise thresholds**, use **1**, **2**, and **3** events for each stage
    respectively then select Next.

![A screenshot of a computer screen Description automatically
generated](./media/image132.png)

19. On **Review settings and finish**, select **Submit**.

![A screenshot of a computer Description automatically
generated](./media/image133.png)

20. On **Your policy was created**, select **Done**.

![A screenshot of a computer Description automatically
generated](./media/image134.png)

21. Keep the tab open and continue to the next task.

#### Step 2 – Score the policy

1.  Click on the new policy named **Data theft by a user**. Select **Start
    scoring activity for users**.

![A screenshot of a computer Description automatically
generated](./media/image135.png)

2.  In the **Reason field in the Add users to multiple policies** pane,
    type **Testing the policy**.

![A screenshot of a computer Description automatically
generated](./media/image118.png)

3.  In the **This should last for (choose between 5 and 30 days)** field,
    select **10** days.

4.  Use the **Search user to add to policies** field. Add **MOD Admin**. Then click
    on **Start scoring activity**.

5.  Once you get the confirmation that you have started **Scoring
    activity for 1 users**, click **Close**.

![A screenshot of a computer Description automatically
generated](./media/image137.png)

### Task 3: Data leaks by users

#### Step 1 – Create a new policy

1.  If you closed the browser window in the previous task, open
    the ```https://purview.microsoft.com ``` and log in with admin credentials.

2.  Go to **Insider Risk Management** and select the **Policies** tab.
    Select **Create policy** to open the policy wizard.

![A screenshot of a computer Description automatically
generated](./media/image100.png)

3.  On the **Choose a policy template** page, choose **Data leaks**,
    under **Data leaks**. Select **Next** to continue.

![A screenshot of a computer Description automatically
generated](./media/image138.png)

4.  On the **Name and description** page, complete the following fields:

    - Name (required): ```Data leaks by a user```

    - Description (optional): ```This is a test policy for preventing data leaks.```

5.  Select **Next** to continue.

![A screenshot of a computer Description automatically
generated](./media/image139.png)

6.  On the **Choose users and groups** page, select **Include all users and
    groups**. Select **Next** to continue.

![A screenshot of a computer Description automatically
generated](./media/image106.png)

7.  On the **Exclude users and groups** page, select **Next**.

9.  On the **Decide whether to prioritize** page, select **I want to specify
    priority content**. Select the check box for **SharePoint
    sites**, **Sensitivity labels** and **Sensitive info types**. Select **Next** to
    continue.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image140.png)

9.  On the **SharePoint sites to prioritize** page, select **Add or edit
    SharePoint sites**. On the flyout pane,
    select ```https://{TENANTPREFIX}.sharepoint.com/sites/ContosoWeb1``` and
    select **Add**. Then click **Next**.

10.  On the **Sensitivity labels to prioritize** page, select **Add or edit
    sensitivity labels**. On the flyout pane, select **Internal/Employee
    data (HR)** and select **Add**. Then click **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image124.png)

11. On the **Sensitive info types to prioritize** page, select **Add or edit
    sensitive info types**. On the flyout pane, search for and
    select **Credit Card Number**, **Contoso Employee ID** and **Contoso Employee
    EDM**. Select **Add**. Then click **Next**.

![A screenshot of a computer Description automatically
generated](./media/image125.png)

12. On **Decide whether to score only activity with priority content**,
    select **Get alerts for all activity**. Select **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image126.png)

13. On **Triggers for this policy** page, select Radio button near **User
    performs an exfiltration activity**. Under select which activities
    will trigger this policy, select all the available
    options especially **Download content from SharePoint**. and then
    select **Next**.

![A screenshot of a computer Description automatically
generated](./media/image141.png)

14. On **Triggering thresholds for this policy**, select **Use custom
    thresholds**. Set every threshold to **1** and select **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image142.png)

15. Select the default settings on the **Indicators** page and
    select **Next**.

16. On **Decide whether to use default or custom indicator thresholds**,
    select **Customise thresholds**, use **1**, **2**, and **3** events for each stage
    respectively then select **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image143.png)

17. On **Review settings and finish**, select **Submit**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image144.png)

18. On **Your policy was created**, select **Done**.

![A screenshot of a computer Description automatically
generated](./media/image145.png)

19. Keep the tab open and continue to the next task.

#### Step 2 – Score the policy

1.  Click on the new policy named **Data leaks by a user**. Select **Start
    scoring activity for users**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image146.png)

2.  In the **Reason field in the Add users to multiple policies** pane,
    type Testing the policy. In the **This should last for (choose between
    5 and 30 days)** field, select **10** days. Use the **Search user to add to
    policies** field. Add **MOD Admin**. Then click on **Start
    scoring activity**.

3.  Once you get the confirmation that you have started **Scoring
    activity for 1 user**, click **Close**.

You have successfully created the Insider risk management policies.

## Summary:

In this lab we explored setting up Insider Risk Management from
end-to-end. With your own subscription and licenses, you can also use
this lab guide to create an Azure setup that can also be used to create
various alerts (which includes sending emails with restricted data,
which is not possible from a trial subscription) for the Insider Risk
management policies which you can use to explore the Adaptive Protection
feature on Purview.
