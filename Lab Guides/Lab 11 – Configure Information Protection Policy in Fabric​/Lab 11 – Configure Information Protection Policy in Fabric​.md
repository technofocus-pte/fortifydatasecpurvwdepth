# Lab 11 – Configure Information Protection Policy in Fabric​

## Introduction

Information protection tenant settings help you to protect sensitive
information in your Power BI tenant. Allowing and applying sensitivity
labels to content ensures that information is only seen and accessed by
the appropriate users. 

## Objective

- Enable information protection features in Microsoft Fabric through the
  Admin Portal to prepare for sensitivity label enforcement.

## Exercise 1 – Configure Information Protection Settings in Fabric Admin Portal

1.  In the Fabric portal home page, click on the **Settings** icon in
    the command bar, then navigate to **Governance and insights**
    section and click on **Admin portal** link.

    ![](./media/image1.png)

2.  In the Admin portal – Tenant settings, scroll down to **Information
    protection** section.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image2.png)

3.  Click on the play button beside the **Allow users to apply sensitivity
    labels for content.**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image3.png)

4.  Click on the toggle button to enable it. With this setting enabled,
    specified users can apply sensitivity labels from Microsoft Purview
    Information Protection.

    ![](./media/image4.png)

5.  Now, click on the **Apply** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image5.png)

    **Note**: In case, **Apply** button is not highlighted, then select **Specific security groups** radio button and select back the **The entire organization** radio button.
    
6.  You will receive a notification stating – **Tenant settings will be
    applied within the next 15 minutes**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image6.png)

7.  Click on the play icon beside **Apply sensitivity labels from data
    sources to their data in Power BI**

    ![](./media/image7.png)

8.  Click on the toggle button to enable it.

    ![](./media/image8.png)

9.  When this setting is enabled, Power BI semantic models that connect
    to sensitivity-labeled data in supported data sources can inherit
    those labels, so that the data remains classified and secure when
    brought into Power BI.

    Click on the **Apply** button.

    ![](./media/image9.png)

10. You will receive a notification stating – **Tenant settings will be
    applied within the next 15 minutes.**

    ![](./media/image10.png)

11. Click on the Play icon beside **Automatically apply sensitivity
    labels to downstream content**

    ![](./media/image11.png)

12. Click on the toggle button to enable it.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image12.png)

13. With this settings enabled, whenever you change a sensitivity label
    or applied to Fabric content, the label will also be applied to its
    eligible downstream content.

    Click on the **Apply** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image13.png)

14. You will receive a notification stating – Tenant settings will be
    applied within the next 15 minutes.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image14.png)

15. Click on the Play icon beside - **Allow workspace admins to override
    automatically applied sensitivity labels**

    ![](./media/image15.png)

16. Click on the toggle button to enable it.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image16.png)

17. This setting makes it possible for workspace admins to override
    automatically applied sensitivity labels without regard to label
    change enforcement rules.

    Click on the **Apply** button

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image17.png)

18. You will receive a notification stating - Tenant settings will be
    applied within the next 15 minutes.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image18.png)

19. Click on the Play icon beside **Restrict content with protected
    labels from being shared via link with everyone in your
    organization**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image19.png)

20. Click on the toggle button to enable it.

    ![](./media/image20.png)

21. When this setting is enabled, users can't generate a sharing link
    for People in your organization for content with protection settings
    in the sensitivity label.

    Click on the **Apply** button

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image21.png)

22. You will receive a notification stating - Tenant settings will be
    applied within the next 15 minutes.
    
    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

24. Click on the Play icon beside **Domain admins can set default
    sensitivity labels for their domains (preview)**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

24. Click on the toggle button to enable it.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image24.png)

25. Click on the **Apply** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image25.png)

26. You will receive a notification stating - Tenant settings will be
    applied within the next 15 minutes.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

## Summary

In this lab, you’ve enabled various information protection settings in
the Microsoft Fabric Admin Portal to support sensitivity label
application, inheritance, automatic labeling, and admin overrides.


