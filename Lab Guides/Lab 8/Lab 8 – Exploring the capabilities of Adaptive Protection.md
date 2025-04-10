# 实验 8 – 探索自适应保护的功能

## 练习 1 - 设置自适应保护

### 任务 1 – 设置自适应保护的风险级别

1.  在 Microsoft Edge 中，打开一个新的 InPrivate 窗口，导航到
    `https://purview.microsoft.com` 并使用管理员租户登录。

2.  从导航栏中，转到 **Solutions** \> **Insider risk management**。

![](./media/image1.png)

3.  从子导航栏中，选择 **Adaptive Protection （Preview）**。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

自动生成的计算机 Description 的屏幕截图

4.  由于我们在启用**Adaptive Protection**
    时使用了快速启动选项，因此我们可以看到创建了 2 个 DLP 策略。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

自动生成的计算机 Description 的屏幕截图

5.  现在，从**Risk levels for Adaptive
    Protection**，然后从下拉列表中选择 **Data leaks by a user**。

![BrokenImage](./media/image4.png)


6.  在 **Define conditions for risk levels** 下，选择 **User perform the
    least 3 data exfiltration activities， each ...**
    为** Elevated **的风险。选择 **User performs at least 2 data
    exfiltration activities, each…**为** Moderate **风险。 **Select User
    performs at least 1 data exfiltration activities, each… ** 为
    **Minor** 风险。然后单击 **Save**。

![BrokenImage](./media/image5.png)


7.  同样，您可以在 Insider risk management 下自定义所有可用策略的条件。

8.  现在我们可以为每个级别自定义 DLP 策略。

### 任务 2 – 探索每个风险级别的默认 DLP 策略

Adaptive Protection

1.  在  Adaptive Protection下，选择 DLP Polices ，然后选择 “Endpoint DLP
    的Adaptive Protection Policy。

![BrokenImage](./media/image6.png)


2.  选择 **Edit**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image7.png)

以中等置信度自动生成的计算机屏幕描述的屏幕截图

3.  点击 下一步 直到您到达 **Customize advanced DLP rules**。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

自动生成的计算机 Description 的屏幕截图

4.  检查针对每个风险级别制定的规则和条件。单击 **Next**。

5.  在 **Policy mode** 页面上，选择 **Turn it on right right
    （立即打开**） 旁边的单选按钮。单击 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

自动生成的计算机 Description 的屏幕截图

6.  选择 **Submit**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

自动生成的计算机 Description 的屏幕截图

7.  重复这些步骤以启用 Teams 和 Exchange DLP 的自适应保护策略。

8.  目前，我们不会创建任何规则或策略，但您可以在完成实验后探索各种可用选项。
