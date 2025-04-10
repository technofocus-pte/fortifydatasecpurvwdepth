# 實驗 8 – 探索自適應保護的功能

## 練習 1 - 設置自適應保護

### 任務 1 – 設置自適應保護的風險級別

1.  在 Microsoft Edge 中，打開一個新的 InPrivate 窗口，導航到
    `https://purview.microsoft.com` 幷使用管理員租戶登錄。

2.  從導航欄中，轉到 **Solutions** \> **Insider risk management**。

![](./media/image1.png)

3.  從子導航欄中，選擇 **Adaptive Protection （Preview）**。

![A screenshot of a computer Description automatically
generated](./media/image2.png)

自動生成的計算機 Description 的屏幕截圖

4.  由于我們在啓用**Adaptive Protection**
    時使用了快速啓動選項，因此我們可以看到創建了 2 個 DLP 策略。

![A screenshot of a computer Description automatically
generated](./media/image3.png)

自動生成的計算機 Description 的屏幕截圖

5.  現在，從**Risk levels for Adaptive
    Protection**，然後從下拉列表中選擇 **Data leaks by a user**。

![BrokenImage](./media/image4.png)

6.  在 **Define conditions for risk levels** 下，選擇 **User perform the
    least 3 data exfiltration activities， each ...**
    爲** Elevated **的風險。選擇 **User performs at least 2 data
    exfiltration activities, each…**爲** Moderate **風險。 **Select User
    performs at least 1 data exfiltration activities, each… ** 爲
    **Minor** 風險。然後單擊 **Save**。

![BrokenImage](./media/image5.png)

7.  同樣，您可以在 Insider risk management 下自定義所有可用策略的條件。

8.  現在我們可以爲每個級別自定義 DLP 策略。

### 任務 2 – 探索每個風險級別的默認 DLP 策略

Adaptive Protection

1.  在  Adaptive Protection下，選擇 DLP Polices ，然後選擇 “Endpoint DLP
    的Adaptive Protection Policy。

![BrokenImage](./media/image6.png)


2.  選擇 **Edit**。

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image7.png)

以中等置信度自動生成的計算機屏幕描述的屏幕截圖

3.  點擊 下一步 直到您到達 **Customize advanced DLP rules**。

![A screenshot of a computer Description automatically
generated](./media/image8.png)

自動生成的計算機 Description 的屏幕截圖

4.  檢查針對每個風險級別制定的規則和條件。單擊 **Next**。

5.  在 **Policy mode** 頁面上，選擇 **Turn it on right right
    （立即打開**） 旁邊的單選按鈕。單擊 **Next**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

自動生成的計算機 Description 的屏幕截圖

6.  選擇 **Submit**。

![A screenshot of a computer Description automatically
generated](./media/image9.png)

自動生成的計算機 Description 的屏幕截圖

7.  重複這些步驟以啓用 Teams 和 Exchange DLP 的自適應保護策略。

8.  目前，我們不會創建任何規則或策略，但您可以在完成實驗後探索各種可用選項。
