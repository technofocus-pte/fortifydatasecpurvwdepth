# Lab 1: Enforce Sensitivity Labeling in Fabric and Power BI using Microsoft Purview

## Objective

- Enable and prioritize a manual sensitivity label policy in Microsoft
  Fabric using Microsoft Purview.

1.  Open an Edge browser address bar and enter the following URL to open
    the Fabric portal -

[**https://app.fabric.microsoft.com**](https://app.fabric.microsoft.com/)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  Enter your tenant credentials.

![](./media/image2.png)

![](./media/image3.png)

3.  In the password field, enter the tenant password. Then, click on the
    **Sign in** button.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image4.png)

4.  On **Welcome to the Fabric view** dialog box, click on the
    **Cancel** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

5.  Click on the profile icon on the command bar.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

6.  Navigate and click on **Free trial** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

7.  On the **Activate your 60-day free Fabric trial capacity**, in the
    **Trial capacity region** ensure that **Default – West US 3** region
    is selected, then click on the **Activate** button.

![](./media/image8.png)

8.  On **Successfully upgraded to a free Microsoft Fabric trial** dialog
    box, click on the **Got it** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  Click on the **Settings** gear box in the command bar.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

10. Navigate to Governance and insights section and click on **Microsoft
    Purview hub (preview)** link.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

11. In case, **Pick an account** dialog box appears, then select your
    tenant ID.

![](./media/image13.png)

12. On **Welcome to Information Protection in the new Microsoft Purview
    portal** dialog box, click on **Get started** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

13. Click on the dropdown beside **Policies**.

![](./media/image15.png)

14. Then, click on **Label publishing policies**.

![](./media/image16.png)

15. In the **Create policy** page, navigate and click on **Choose
    sensitivity label to publish** link.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

16. **Sensitivity label to publish** pane appears on the right side,
    navigate and select the checkbox beside **Confidential**, then click
    on the **Add** button.

![](./media/image18.png)

17. Now, click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

18. On **Assign admin units** page, click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

19. In **Publish to users and groups** page, ensure that the checkbox
    beside **Users and groups** is selected, then click on the **Next**
    button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

20. In the **Policy settings** page, select the checkbox beside
    **Require users to apply a label to their Fabric and Power BI
    content**. Then, click on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

21. On **Default settings for documents – Apply a default label to
    documents** page, click on the **Next** button.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image24.png)

22. On **Default settings for documents – Apply a default label to
    emails** page, click on the **Next** button.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

23. On **Default settings for meetings and calendar events** page, click
    on the **Next** button.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image26.png)

24. On **Default settings for Fabric and Power BI content** page, click
    on the **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

25. In **Name your policy** page, under the **Name** field, enter
    **Manual Labeling – HR Confidential Docs**. Then, click on the
    **Next** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

26. On **Review and finish** page, click on the **Submit** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

27. The policy is successfully created. Now, click on the **Done**
    button.

![](./media/image30.png)

28. In the **Label policies** page, you will see **Manual Labeling – HR
    Confidential Docs** policy is successfully created.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

29. Select **Manual Labeling – HR Confidential Docs**, then click on the
    horizontal ellipsis, navigate and select **Move up** to change the
    Priority.

![](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

30. Again, select **Manual Labeling – HR Confidential Docs**, then click
    on the horizontal ellipsis beside it and select **Move up**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

31. You will notice that **Manual Labeling – HR Confidential Docs**
    priority is now changed to 1.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

**Summary**

In this lab, you’ve activated a Microsoft Fabric trial, accessed the
Microsoft Purview portal, and created a mandatory sensitivity label
policy requiring users to apply the "Confidential" label to Fabric and
Power BI content. The policy was then prioritized for enforcement.
