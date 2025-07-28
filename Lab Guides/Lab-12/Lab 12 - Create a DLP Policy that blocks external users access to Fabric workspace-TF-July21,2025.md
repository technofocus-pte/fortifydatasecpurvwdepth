**Lab 12: Create a DLP Policy that blocks external users access to
Fabric workspace**

**Introduction**

*We need to block external users from reports containing credit card
numbers, unless the data is labeled with the 'Highly Confidential -
Internal' sensitivity label, in which case a protection policy restricts
access to select security groups. We want to notify the compliance admin
to know whenever a semantic model is blocked and the data owner to be
aware the restriction took place. We also want internal users to be
aware that the data is highly confidential and that they shouldn't share
it outside the organization.*

|**Statement**|**Configuration question answered and configuration mapping**|
| ------------|-------------------------------------- ---------------------|

|"We need to block external users..."           |       - Where to monitor: Fabric and Power BI
- Administrative scope: Full directory
- Action: Restrict access or encrypt the content in Microsoft 365 locations > Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files, and Power BI items > Block only people outside your organization
|

|"...from reports containing credit card numbers..."|- What to monitor: use the Custom template
- Conditions for match: edit it to add the Credit Card Number sensitive info type.
|
|  "...except if the data is labeled with the Highly Confidential - Internal sensitivity label..."|        - Condition group configuration: Create a nested boolean NOT condition group joined to the first condition using a boolean AND
- Condition for match: edit it to add the Highly Confidential - Internal sensitivity label.
|
|  "We want to notify the compliance admin to know whenever a semantic model is blocked..."           |                          -Incident reports: Send an alert to admins when a rule match occurs: On
- Send an alert every time an activity matches the rule: selected
  |
|  "...the data owner to be aware the restriction took place. We also want internal users to be aware that the data is highly confidential and that they shouldn't share it outside the organization."|                    - User notifications: On
- Microsoft 365 files and Microsoft Fabric items: Notify users in Office 365 service with a policy tip or email notifications: selected
- Policy tips: Customize the policy tip text: selected. Add text in the text box explaining the rules governing sharing highly confidential data.
|

**Important**

For the purposes of this policy creation procedure, you'll accept the
default include/exclude values and leave the policy turned off. You'll
be changing these when you deploy the policy.

**Objective**

- Create a custom Data Loss Prevention (DLP) policy in Microsoft Purview
  to block external user access to Fabric and Power BI content
  containing sensitive information.

**Exercise 1: Creating a Custom DLP Policy to Block External Access to
Fabric Workspaces**

1.  In the Microsoft Purview portal, click on **Solutions**, then
    navigate and click on **Data Loss Prevention**

![](./media/image1.png)

1.  Now, click on **Policies**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

2.  In the **Policies** page, click on **+** **Create policy**.

![](./media/image3.png)

3.  On **Choose what type of data to protect** page, ensure that **Data
    stored in connected sources** radio button is selected, then click
    on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

4.  On **Start with a template or create a custom policy** page, click
    on **Custom** under **Categories**.

> Select **Custom policy** from the **Regulations** list, then click on
> the **Next** button.

![](./media/image5.png)

5.  On the **Name your DLP policy** page, in the **Name** field, ensure
    that **Custom policy** is mentioned.

**Note**: You can use the policy intent statement here. Policies can't
be renamed.

> Click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

6.  In the **Assign** **Admin units** page, click on the **Next**
    button.

![](./media/image7.png)

7.  On Choose where to apply the policy page, click on the Next button.

![](./media/image8.png)

8.  On the **Define policy settings** page, ensure that **Create or
    customize advanced DLP rules** radio button is selected. Then, click
    on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  In **Customize advanced DLP rules** page, select **+ Create rule**.

![](./media/image10.png)

10. On the **Create rule** page, in the **Name** field, enter **Block
    external users access to Fabric workspace**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

11. Under **Conditions** section, select **Add condition** \> **Content
    contains** \> **Add** \> **Sensitive info types**.

![](./media/image12.png)

![](./media/image13.png)

12. In the **Sensitive info types** pane that appear on the right side,
    click inside the search bar, type **credit card number** and press
    the enter button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

![](./media/image15.png)

13. Select the check box beside **Credit Card Number**, then click on
    the **Add** button.

![](./media/image16.png)

14. Under **Actions**, select **Add an action** \> **Restrict access or
    encrypt the content in Microsoft 365 locations**

![](./media/image17.png)

15. Ensure that the **Block users from receiving email or accessing
    shared SharePoint, OneDrive, and Teams files, and Power BI
    items** and **Block only people outside your organization** are
    selected.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

16. Under **User notifications**, set the toggle to **On**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

17. Select **Notify users in Office 365 service with a policy tip or
    email notifications** check box and **Customize the policy tip
    text** checkbox.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

18. In the **User overrides** section, select the checkbox beside
    **Allow users to override policy restrictions in Fabric (including
    Power BI), Exchange, SharePoint, OneDrive, and Teams**, then
    navigate and select the checkbox beside **Override the rule
    automatically if they report it as a false positive**.

> ![](./media/image22.png)

19. Under **Incident reports**, set **Use this severity level in admin
    alerts and reports** to **High**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

![](./media/image24.png)

20. Make sure the **Send an alert to admins when a rule match
    occurs** toggle is set to **On**.

21. Make sure the **Send alert every time an activity matches the
    rule** radio button is selected.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

22. Click on the **Save** button.

![](./media/image26.png)

23. Review the rule, then click on the **Next** button.

![](./media/image27.png)

24. Ensure that the **Run the policy in simulation mode** radio button
    and the **Show policy tips while in simulation mode** checkboxes are
    selected. Then, click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

25. In **Review and finish** page, click on the **Submit** button. After
    few seconds, the policy will be successfully created.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

![](./media/image30.png)

**Important Note:** You may encounter **Client Error** because creating
a **block DLP policy** is not possible in this environment due to lab
limitations. In a real-world scenario, this issue will not occur.

![](./media/image31.png)

**Summary**

In this lab, you have created a custom DLP policy in Microsoft Purview
to protect Fabric and Power BI content by detecting sensitive data and
applying restrictions to block external user access. The policy also
enables user notifications and admin alerts.
