---
lab:
  title: Lab 6 — Detect and investigate risky data handling with Insider Risk Management policies, analytics, alerts, and cases
  description: In this lab we configured Insider Risk Management policies, ran analytics, and worked the investigation lifecycle through alerts and cases.
  duration: 30 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Insider Risk Management
---

# Lab 6 — Detect and investigate risky data handling with Insider Risk Management policies, alerts, and cases

Not every threat to Contoso Pharmaceuticals' data comes from outside. A departing researcher might copy compound formulations before leaving, or a user might browse to a risky site and exfiltrate trial data. Insider Risk Management detects these patterns by correlating signals across Microsoft 365 — file activity, device activity, browsing — and scoring them against the sensitive content that matters. In this lab, acting as Allan Deyoung, you'll assign the Insider Risk Management role, create two risk policies that prioritize Contoso's crown-jewel data, and then work the investigation lifecycle the way a real analyst does: triage the alerts a policy generates, and escalate an alert into a case to investigate a user's activity.

This lab builds on the environment prepared in Lab 0 — device onboarding and Insider Risk analytics were already enabled there — and on the classifiers and labels from Labs 2 and 4, which become the priority content that focuses risk scoring on Contoso's most sensitive data.

**Learning outcomes.** After this lab you can:

- Assign the Insider Risk Management role to an operator.
- Create insider risk policies using data-theft and risky-browser-usage templates, with priority content.
- Triage insider risk alerts.
- Escalate an alert to a case and investigate a user's activity.

**Tasks**:

1. Assign the Insider Risk Management role
2. Create a data-theft policy with priority content
3. Create a risky-browser-usage policy
4. Triage insider risk alerts
5. Escalate an alert to a case and investigate

> [!NOTE]
> This lab does not onboard devices or enable analytics. It confirms the role and proceeds to policies and investigation. Insider Risk Management pseudonymizes users by default, so usernames may appear anonymized in analytics and alerts; that is expected privacy behavior.

## Task 1 – Assign the Insider Risk Management role

In this task, you'll add Allan Deyoung to the Insider Risk Management role group so he can create policies and investigate alerts and cases.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **MOD Administrator**, `admin@TenantName` (the Tenant Name and password are provided in the Resources tab).

2. In the upper-right corner, select **Settings**, then in the left navigation select **Roles and scopes**, then select **Role groups**.

	![](./media/image1.png)

3. On the **Role groups for Microsoft Purview solutions** page, select **Insider Risk Management** from the list. Do not select the checkbox, select the name.

	![](./media/image2.png)

4. On the **Insider Risk Management** pane, select the **Members** tab.

	![](./media/image3.png)

5. On the **Members** tab, select **+ Add Member > Choose users**.

	![](./media/image4.png)

6. In the user list, select the checkbox next to **Allan Deyoung**, then choose **Select**.

	![](./media/image5.png)

7. With the user in the list, select **Done**. Then select **Confirm** on the pop-up.

	![](./media/image6.png)

	![](./media/image7.png)

> [!NOTE]
> The Insider Risk Management role group grants the full set of insider-risk permissions — creating policies, and investigating alerts and cases — which is what Allan needs for this lab. Role changes can take a few minutes to take effect. This timing is indicative, not guaranteed.

You have successfully assigned Allan Deyoung the Insider Risk Management role.

## Task 2 – Create a data-theft policy with priority content

Contoso's greatest insider concern is a departing employee taking research or trial data with them. In this task, you'll create a policy from the data-theft template that scores exfiltration activity, focusing that scoring on Contoso's crown-jewel data by designating the Mark 8 site, the research and trial labels, and the compound and subject classifiers as priority content.

1. In **Microsoft Edge**, sign in to the Microsoft Purview portal as **Allan Deyoung**, `AllanD@TenantName`.

2. In the left navigation, select **Solutions** > **Insider Risk Management**.

3. Select **Policies**, then select **+ Create policy** > **Custom policy**.

	![](./media/image8.png)

4. On the **Choose a policy template** page, under **Data theft**, select **Data theft by departing users**, then select **Next**.

	![](./media/image9.png)

5. On the **Name and description** page, enter the following, then select **Next**:

   - **Name**: `Data theft of research and trial data`
   - **Description**: `Scores exfiltration activity by departing users, focused on Contoso research and trial data.`

	![](./media/image10.png)

6. On the **Choose users, groups, & adaptive scopes** page, select **All users, groups, and adaptive scopes**, then select **Next**. On the **Exclude users and groups** page, select **Next**.

	![](./media/image11.png)

	![](./media/image12.png)

7. On the **Decide whether to prioritize content** page, select **I want to prioritize content**, then select the checkboxes for **SharePoint sites**, **Sensitivity labels**, and **Sensitive info types**. Select **Next**.

	![](./media/image13.png)

8. On the **SharePoint sites to prioritize** page, select **Add or edit SharePoint sites**, select the **Mark 8 Project Team** site, select **Add**, then select **Next**.

	![](./media/image14.png)

	![](./media/image15.png)

9. On the **Sensitivity labels to prioritize** page, select **Add or edit sensitivity labels**, select **Highly Confidential – Research** and **Restricted – Trial Data** (from Lab 4), select **Add**, then select **Next**.

	![](./media/image16.png)

	![](./media/image17.png)

10. On the **Sensitive info types to prioritize** page, select **Add or edit sensitive info types**, select **Contoso Compound ID** and **Contoso Clinical Trial Subjects** (from Lab 2), select **Add**, then select **Next**.

	![](./media/image18.png)

	![](./media/image19.png)

11. On the **Decide whether to score only activity with priority content** page, select **Get alerts for all activity**, then select **Next**.

	![](./media/image20.png)

12. On the **Choose triggering event for this policy** page, keep the default triggering event (User account deleted from Microsoft Entra ID), then select **Next**.

	![](./media/image21.png)

13. If you see a message **The indicators needed to create this policy aren't available to select because they're currently turned off for your organization. Turn them on now to continue.**, select **Turn On Indicators** and **Turn on all** the indicators.

	![](./media/image22.png)

	![](./media/image23.png)

14. On the **Indicators** page, ensure the Office and device indicators relevant to exfiltration are selected (for example, downloading from SharePoint, copying to USB, copying to network share, sending email with attachments to external recipients), then select **Next**. 

		![](./media/image24.png)

15. On the **Detection options** and **Choose threshold type for indicators** pages, leave the defaults (or apply the thresholds provided by Microsoft), then select **Next**.

	![](./media/image25.png)

	![](./media/image26.png)

16. On the **Review settings and finish** page, select **Submit**, then select **Done**.

	![](./media/image27.png)

	![](./media/image28.png)

You have successfully created a data-theft policy focused on Contoso's research and trial data.

## Task 3 – Create a risky-browser-usage policy

Exfiltration also happens through the browser — uploading files to personal storage or browsing to risky sites. In this task, you'll create a second policy from the risky-browser-usage template to broaden Contoso's insider-risk coverage.

1. In the Microsoft Purview portal, on the **Insider Risk Management** > **Policies** page, select **+ Create policy** > **Custom policy**.

	![](./media/image29.png)

2. On the **Choose a policy template** page, under **Risky browser usage**, select **Risky browser usage**, review the listed prerequisites, then select **Next**.

	![](./media/image30.png)

3. On the **Name and description** page, enter the following, then select **Next**:

   - **Name**: `Risky browser usage`
   - **Description**: `Detects and scores risky browsing activity across the organization.`

	![](./media/image31.png)

4. On the **Choose users, groups, & adaptive scopes** page, select **All users, groups, and adaptive scopes**, then select **Next**. On the **Exclude users and groups** page, select **Next**.

	![](./media/image32.png)

	![](./media/image33.png)

5. On the **Decide whether to prioritize content** page, select **I don't want to prioritize content right now**, then select **Next**.

	![](./media/image34.png)

6. On the **Choose triggering event for this policy** page, if prompted, select **Turn on indicators**, then **Choose indicators to turn on**, ensure the **Risky browsing indicators** are selected, and select **Save**.

	![](./media/image35.png)

	![](./media/image36.png)

7. Back on the triggering-event page, ensure **User browsed to a potentially risky website** is selected, select the browsing activities that will trigger the policy, then select **Next**.

	![](./media/image37.png)

8. On the remaining pages (thresholds, indicators, threshold type), leave the defaults or apply the thresholds provided by Microsoft, selecting **Next** through each.

	![](./media/image38.png)

	![](./media/image39.png)

	![](./media/image40.png)

9. On the **Review settings and finish** page, select **Submit**, then select **Done**.

	![](./media/image41.png)

	![](./media/image42.png)

> [!NOTE]
> Risky browsing indicators depend on the Microsoft Purview browser extension and device onboarding (enabled in Lab 0). Signals from browsing activity require onboarded devices reporting in. This template may appear labeled as preview in your tenant.

You have successfully created a risky-browser-usage policy.

## Task 4 – Triage insider risk alerts

When a policy scores a user's activity above its thresholds, it generates an alert for an analyst to review. In this task, you'll review the alerts queue and triage an alert. Because organic alerts depend on real scored activity over time, you'll also start scoring for a test user so the policy has activity to evaluate.

1. In the Microsoft Purview portal, on the **Insider Risk Management** > **Policies** page, select the **Data theft of research and trial data** policy, then select **Start scoring activity for users**.

	![](./media/image43.png)

2. In the **Reason for scoring activity** field, enter `Testing the policy`. In the **Scoring activity for this many days** field, select `10 days`. In the **Score activity for these users** field, enter and select a test user (for example, **Isaiah Langer**). Select **Start scoring activity**, then select **Close**.

	![](./media/image44.png)

	![](./media/image45.png)

3. In the left navigation, select **Insider Risk Management** > **Users** > **Alerts(Preview)**.

	![](./media/image46.png)

4. In a populated tenant you can review the **Alerts** queue. Each alert shows the associated policy, the risk severity, and its status.

5. In the alert details, you can review the tabs that support triage — for example **All risk factors**, **Activity explorer**, and **User activity** — to understand what the user did and why it scored.

6. You can also triage the alert by setting its status. You can choose **Confirm** to keep it for further investigation (leading to a case in the next task), or **Dismiss** if the activity is benign. Add an analyst note describing your assessment.

> [!IMPORTANT]
> Alerts appear only after a policy detects and scores qualifying activity, which is not immediate — it can take a day or more for scored activity to surface as an alert, and analytics latency can compound this. If the Alerts queue is empty, allow time and return. Note that Microsoft is rolling out a unified alert experience in preview during 2026, so the exact alerts interface may differ from what is described here. These timings are indicative, not guaranteed.

You have successfully reviewed and triaged an insider risk alert.

## Task 5 – Escalate an alert to a case and investigate (Read Only)

Cases are the heart of Insider Risk Management — where you investigate and act on a user's risky activity. In this task, you'll create a case from an alert and work the investigation, then resolve it. This task is a read only task as you will not be able to get any alerts due to the time and environment constraints.

1. In the Microsoft Purview portal, with a confirmed alert open (from Task 4), select the option to **Create case** (or **Escalate to case**). Give the case a name such as `Investigation – research data exfiltration`, then create it.

2. In the left navigation, select **Insider Risk Management** > **Cases**, then select the case you created.

3. In the case, review the investigation surfaces:

   - **Alerts** — the alerts included in this case for the user.
   - **User activity** — a timeline of the user's risk-relevant activity, showing what content was involved and how it was handled.
   - **Activity explorer** — detailed activity records you can filter to understand the scope.
   - **Notes** — where you record your investigation findings.

4. Add a note documenting your assessment of the user's activity.

5. Take action on the case. Depending on your assessment, you can:

   - **Send the user a notice** — a reminder of policy for inadvertent risk.
   - **Resolve the case as benign** — if the activity is not a genuine risk.
   - **Escalate for an eDiscovery (Premium) investigation** — to transfer the case to a formal legal investigation (this connects to the eDiscovery lab later in the course).

   For this lab, add a resolution note and **Resolve** the case (or send a user notice), then confirm the case status updates.

> [!NOTE]
> Case creation, investigation, and resolution are available immediately once you have an alert to work from — this is the live, in-session part of the lifecycle. The ability to escalate a case to eDiscovery (Premium) links Insider Risk Management to the eDiscovery solution covered later in the course.

You have successfully escalated an alert to a case, investigated the user's activity, and resolved it.

## Summary

In this lab, you configured and operated Insider Risk Management for Contoso Pharmaceuticals end to end. You assigned the Insider Risk Management role to Allan Deyoung, then created two risk policies — a data-theft policy that focuses scoring on the Mark 8 site, the research and trial labels, and the compound and subject classifiers, and a risky-browser-usage policy for broader coverage. You then worked the investigation lifecycle: triaging the alerts a policy generates, and escalating an alert into a case to investigate a user's activity and resolve it. Because insider-risk alerts are latency-gated by design, you started scoring so results build over time, while case investigation is available immediately. These capabilities let Contoso detect and act on risky handling of its most sensitive data from the inside.