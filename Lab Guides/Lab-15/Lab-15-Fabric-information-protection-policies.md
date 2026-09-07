---
lab:
  title: Lab 15 — Configure information protection policy in Microsoft Fabric
  description: In this lab we enabled the information protection tenant settings in the Microsoft Fabric Admin portal to support sensitivity label application, inheritance, and admin overrides.
  duration: 15 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Microsoft Fabric
---

# Lab 15 — Configure information protection policy in Microsoft Fabric

## Introduction

For Contoso Pharmaceuticals to protect the sensitive analytics content in its Microsoft Fabric and Power BI estate, the tenant's information-protection settings must be turned on first. These settings let specified users apply sensitivity labels to Fabric content, allow labels to be inherited from source data and flow downstream, and restrict how protected content can be shared — so that Contoso's confidential information is only seen and accessed by the appropriate users. In this lab, acting as Allan Deyoung, you'll enable the information-protection tenant settings in the Fabric Admin portal that prepare Contoso's estate for sensitivity-label enforcement.

This lab configures the tenant-level foundation that the labeling and data-loss-prevention labs in this Fabric cluster build on.

> [!IMPORTANT]
> This lab requires a Microsoft Fabric capacity (the 60-day trial capacity activated earlier in the Fabric cluster is sufficient) and the appropriate Fabric/Power BI administrator permissions to change tenant settings. Some settings shown are only available once labeling is enabled — for example, the sharing-restriction setting requires that applying sensitivity labels is already turned on, which you do first in this lab. This lab covers tenant-level configuration, not the creation of Fabric artifacts.

## Objective

- Enable information protection features in Microsoft Fabric through the Admin Portal to prepare for sensitivity label enforcement.

**Learning outcomes.** After this lab you can:

- Enable the tenant setting that allows users to apply sensitivity labels to Fabric content.
- Enable label inheritance from data sources and to downstream content.
- Allow workspace admins to override automatically applied labels.
- Restrict sharing of content that carries protected labels.
- Enable domain-level default sensitivity labeling.

## Exercise 1 – Configure Information Protection Settings in Fabric Admin Portal

In this exercise, you'll enable each of the information-protection tenant settings that Contoso needs, applying them one at a time in the Fabric Admin portal.

1.  In the Fabric portal home page, click on the **Settings** icon in
    the command bar, then navigate to the **Governance and insights**
    section and click on the **Admin portal** link.

    ![](./media/image1.png)

2.  In the Admin portal – Tenant settings, scroll down to the **Information
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

    **Note**: In case the **Apply** button is not highlighted, then select the **Specific security groups** radio button and select back the **The entire organization** radio button.

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

13. With this setting enabled, whenever a sensitivity label is changed
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

23. Click on the Play icon beside **Domain admins can set default
    sensitivity labels for their domains (preview)**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image23.png)

24. Click on the toggle button to enable it.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image24.png)

25. Click on the **Apply** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image25.png)

26. You will receive a notification stating - Tenant settings will be
    applied within the next 15 minutes.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image26.png)

> [!NOTE]
> Each setting shows a notice that it can take up to 15 minutes to take effect. Together these settings do two things: allow manual labeling of Fabric content, and enable label *inheritance* — both from labeled data sources into Power BI and downstream from a labeled item to content built from it — while the sharing-restriction and domain-default settings govern how protected content is shared and classified by default. This timing is indicative, not guaranteed.

You have successfully enabled the information protection settings in the Fabric Admin portal.

## Summary

In this lab, you enabled the information protection settings in the Microsoft Fabric Admin portal that prepare Contoso Pharmaceuticals' analytics estate for sensitivity-label enforcement — allowing users to apply labels, enabling label inheritance from data sources and to downstream content, allowing workspace admins to override automatically applied labels, restricting the sharing of content with protected labels, and enabling domain-level default labeling. With these tenant-level foundations in place, Contoso's Fabric and Power BI content can be classified and protected consistently with the rest of its data.