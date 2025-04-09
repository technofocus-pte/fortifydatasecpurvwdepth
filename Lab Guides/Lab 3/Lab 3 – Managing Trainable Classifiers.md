# 实验 3 – 管理可训练分类器

## 目的:

Contoso Ltd. 租户包含一个 SharePoint
网站集，该网站集将来将用于存储多个与财务相关的文档和报表。由于这些文档的性质，您需要创建一个可训练的分类器来识别和标记这些文件。为此，您将激活自定义可训练分类器，并在此实验室中创建一个新分类器。

## 练习 1 – 创建可训练分类器

在此任务中，Patti 将创建一个新的可训练分类器，并选择不同的 SharePoint
站点来识别 Contoso Ltd. 创建和存储的典型数据。

1.  在 **Microsoft Edge** 中，打开一个 **New InPrivate Window**，导航到
    `https://purview.microsoft.com` 并使用用户名
    PattiF@WWLx{TENANTPREFIX}.onmicrosoft.com
    和资源选项卡上提供的用户密码以 `Patti Fernandez` 身份登录。

2.  从左侧导航栏中，选择 **Solutions** \> **Data Loss Prevention**。

![A screenshot of a computer Description automatically
generated](./media/image1.png)

自动生成的计算机 Description 的屏幕截图

3.  从左侧窗格中展开 **Classifiers**。从子导航窗格中选择 **Trainable
    Classifiers。+ Create trainable classifier** 以创建新的分类器。

![](./media/image2.png)

4.  在 **Name and describe your trainable classifier**
    页面上输入以下信息：

    - 名字: `Contoso Company Data`

    - 描述:
      `Trainable classifier for company data produced and stored by Contoso Ltd.`

5.  选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

自动生成的计算机 Description 的屏幕截图

8.  选择 **Choose sites** 以打开右侧窗格。

![A screenshot of a computer Description automatically
generated](./media/image4.png)

自动生成的计算机 Description 的屏幕截图

9.  选择以下 SharePoint 站点，然后选择 **Add**。

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

![](./media/image5.png)

10. 等待所选站点显示在列表中，然后选择 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image6.png)

自动生成的计算机 Description 的屏幕截图

11. 在 **Source of the negative sample content page**，选择站点
    **Learn**，然后选择 **Next**。

12. 查看设置，然后选择 **Create trainable classifier**。

![A screenshot of a computer Description automatically
generated](./media/image7.png)

自动生成的计算机 Description 的屏幕截图

13. 当显示消息 Your trainable classifier was created 时，选择 **Done**。

现在正在分析所选 SharePoint 站点中的文档和文件，这可能需要长达 24
小时。准备就绪后，您可以执行以下作。

- Test the classifier

- Review the classifier

- Publish the classifier

您可以浏览已存在的分类器以供进一步查看。

## 总结:

您已成功创建一个自定义可训练分类器，该分类器与 Contoso Ltd. 的现有
SharePoint 站点上存储的文件匹配。
