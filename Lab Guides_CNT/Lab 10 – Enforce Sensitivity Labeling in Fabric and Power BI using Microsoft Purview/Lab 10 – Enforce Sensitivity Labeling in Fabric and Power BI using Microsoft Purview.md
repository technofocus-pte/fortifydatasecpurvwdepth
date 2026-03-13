**实验室 10 – 使用 Microsoft Purview 在 Fabric 和 Power BI 中强制执行敏感性标签**

**介绍**

租户必须启用 Microsoft Purview 信息保护（Fabric 和 Power BI，包括 Power BI Desktop）中的敏感标签。启用敏感性标签时：

- 组织内指定的用户和安全组可以对其 Fabric 内容应用敏感性标签。在Fabric服务中，这意味着任何Fabric商品。在Power BI Desktop中，指的是他们的.pbix文件。

- 在仪式中，所有组织成员都能看到这些标签。在桌面版中，只有组织中被发布标签的成员才能看到标签。

**目标**

1.  在 Microsoft Fabric 中使用 Microsoft Purview 启用并优先设置手动敏感性标签策略。

**练习 1 – 激活 Microsoft Fabric 试用并访问 Purview Hub**

1.  打开Edge浏览器地址栏，输入以下URL即可打开Fabric门户 - https://app.fabric.microsoft.com

<img src="media/image1.png" style="width:6.26806in;height:4.21667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**注释**: 如果你直接进入织物传送门，那就跳过步骤#2和3.

2.  输入您的租户凭证.

<img src="media/image2.png" style="width:6.26806in;height:4.86597in" />

<img src="media/image3.png" style="width:6.26806in;height:4.37778in" />

3.  在密码字段输入租户密码。然后，点击**登录**按钮。

<img src="media/image4.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

4.  在**“欢迎进入织物视图**”对话框中，点击**取消**按钮。

<img src="media/image5.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  点击命令栏上的个人资料图标.

<img src="media/image6.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  点击**并点击  Free trial** 按钮.

<img src="media/image7.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  在“**激活你的60天免费Fabric试用容量**”中，在**试用容量区域**中确保**选择了默认-西美国3**地区，然后点击**激活**按钮。

<img src="media/image8.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  在**成功升级到免费的 Microsoft Fabric 试用**对话框后，点击**“已获取”**按钮。

<img src="media/image9.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  点击 命令栏中的设置齿轮框。

<img src="media/image10.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. 进入治理与洞察部分，点击 **Microsoft Purview 中心（预览）**链接。然后，在 **Microsoft Purview 中心（预览）**页面，点击**并点击信息保护**瓷砖。

<img src="media/image11.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image12.png" style="width:6.26806in;height:3.69028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. 如果**出现“选择账户**”对话框，然后选择租户ID.

<img src="media/image13.png" style="width:6.26806in;height:3.78958in" />

12. 在**新的 Microsoft Purview 门户对话框中的“欢迎使用信息保护”**中，点击**“开始**”按钮。

<img src="media/image14.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**练习 2 – 为Fabric和Power BI创建并配置敏感标签策略**

1.  在信息保护栏目中，点击“政策”旁的下拉菜单。

<img src="media/image15.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  然后，点击**标签发布政策**。在**标签发布政策**页面，点击“**发布标签**”。

<img src="media/image16.png" style="width:6.26806in;height:3.68611in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  在**创建政策**页面，点击**选择敏感标签以发布**链接。

<img src="media/image17.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  **Sensitivity label to publish** 出现在右侧，导航并选择“机密”旁边的复选框，然后点击**“添加**”按钮。

<img src="media/image18.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  现在，点击**“下一**页”按钮。

<img src="media/image19.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  在**“分配管理单元**”页面，点击**“下一步**”按钮。

<img src="media/image20.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  在**“发布给用户和组”页面，确保选中**了“用户和组**”旁的复选框** ，然后点击**“下一**页”按钮。

<img src="media/image21.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  在**策略设置**页面，选择**“要求用户为其 Fabric 和 Power BI 内容应用标签”旁的复选框**。然后，点击**“下一步**”按钮。

<img src="media/image22.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image23.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  关于**文档默认设置——为文档页面应用默认标签**，点击**“下一步**”按钮。

<img src="media/image24.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

10. 在**文档默认设置中——给邮件页面应用默认标签**，点击**“下一步**”按钮。

<img src="media/image25.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

11. 在**会议和日历活动的默认设置**页面，点击**“下一步**”按钮。

<img src="media/image26.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

12. 在**Fabric和Power BI内容页面的默认设置**中，点击**“下一步**”按钮。

<img src="media/image27.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. 在**“命名你的保单**”页面，在**“姓名**”栏下输入“手动标签——人力资源保密文档。然后，点击**“下一步**”按钮。

<img src="media/image28.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. 在**审核与完成**页面，点击**提交**按钮。

<img src="media/image29.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. 该政策成功制定。现在，点击**“完成**”按钮。

<img src="media/image30.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. 在**标签政策**页面，您将看到**手动标签——人力资源保密文件**政策已成功创建。

<img src="media/image31.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. 选择**“手动标签——人力资源保密文档**”，然后点击水平省略号，导航并选择**“向上移动**”以更改优先级。

<img src="media/image32.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image33.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. 同样，选择**“手动标签——人力资源保密文档**”，然后点击旁边的横向省略号，选择**“向上移动**”。

<img src="media/image34.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. 您会注意到**，手动标签——人力资源机密文件的**优先级现在改为1。

<img src="media/image35.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**总结**

在这个实验室里，你激活了 Microsoft Fabric 试用，访问了 Microsoft Purview 门户，并创建了强制性的敏感性标签策略，要求用户对 Fabric 和 Power BI 内容应用“机密”标签。该政策随后被优先执行。
