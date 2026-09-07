---
lab:
  title: Lab 10 — Investigate data security incidents with Data Security Investigations
  description: In this lab we set up Data Security Investigations, created an investigation, and used AI-powered analysis to find, review, and mitigate exposed content.
  duration: 20 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Data Security Investigations
---

# Lab 10 — Investigate data security incidents with Data Security Investigations

When Contoso Pharmaceuticals suspects that sensitive data has been exposed — pre-publication Mark 8 results surfaced through an overshared site, a compound identifier pasted into an external tool — the security team needs to know not just *where* data moved, but *what* it contained, how sensitive it is, and the risk it creates. Data Security Investigations (DSI) answers those questions using generative AI to reason over the actual content of emails, Teams messages, documents, and AI-app prompts across the Microsoft 365 estate, then lets the team mitigate directly — purging exposed items or revoking access. In this lab, acting as Allan Deyoung, you'll set up DSI, create an investigation into Contoso's data-exposure incident, use AI-powered analysis to find and score the exposed content, and drive remediation through a mitigation plan.

> [!IMPORTANT]
> **This lab requires an Azure subscription and incurs real costs.** Unlike the other labs in this course, Data Security Investigations does **not** run on Microsoft 365 E5 alone. It uses a pay-as-you-go billing model: you must associate DSI with a valid Azure subscription (in the same tenant as your Microsoft Purview account), and you are billed for data storage and AI compute (Data Security Investigation Compute Units) as you use them. Costs can accumulate quickly — an investigation holding tens of gigabytes can cost hundreds to over a thousand US dollars per month. **Task 1 sets up this billing. If you do not have an Azure subscription with Owner access, you cannot complete this lab beyond Task 1.** Delete investigations when finished to stop storage charges. These figures are indicative and change over time.

**Learning outcomes.** After this lab you can:

- Configure Data Security Investigations prerequisites, including Azure billing and roles.
- Create an investigation and scope it to a data security incident.
- Use AI-powered deep content analysis to find and categorize exposed data.
- Review AI-generated risk findings for an incident.
- Drive remediation of exposed content through a mitigation plan.

**Tasks**:

1. Set up billing and roles for Data Security Investigations
2. Create an investigation and scope it
3. Run AI-powered analysis on the investigation
4. Review the findings
5. Mitigate the exposed content

## Task 1 – Set up billing and roles for Data Security Investigations

DSI's AI analysis and storage are billed to an Azure subscription, not to your Microsoft 365 licenses. In this task, you'll accept the terms, assign the DSI roles, and connect DSI to an Azure subscription for billing. This task is the prerequisite gate for the entire lab.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **MOD Administrator**, `admin@TenantName` (the Tenant Name and password are provided in the Resources tab). A Global Administrator is required for initial setup, and you must be an **Owner** of the Azure subscription you will use for billing.

2. Select the **Data Security Investigations** solution card. If this is the first time accessing DSI, read the **Privacy Statement**, confirm you accept the terms, and select **Get started**.

3. In the left navigation, select **Overview**. In the **Setup tasks** section, select **Assign roles to your team members**.

4. On the **Role assignment** flyout, in the **Administrators** field select **Allan Deyoung**, and in the **Investigators** field select **Allan Deyoung** (and any analysts who will run investigations). Select **Confirm**.

> [!NOTE]
> The **Data Security Investigations Admins** role group manages the solution and all investigations; the **Investigators** role group can work only the investigations they're assigned to. Assigning Allan to both lets him both configure DSI and run the investigation in this lab.

5. Back in the **Setup tasks** section, select the task to **configure billing**. On the billing configuration page, associate DSI with your **Azure subscription**: select the subscription (it must be in the same tenant as your Purview account) and the resource group DSI should use for its resources. Confirm the billing setup.

> [!IMPORTANT]
> Billing must be configured before you can create or open an investigation — DSI will block access to any investigation until a valid Azure subscription is attached. If you later enable proactive AI insights from Data Security Posture Management, storage and AI costs accrue continuously while that toggle is on, because the auto-created investigation refreshes every 24 hours. Configure billing deliberately and monitor the in-product cost estimator and usage dashboard.

6. After setup completes, confirm that users with DSI roles receive a notification (through the Microsoft Purview Notification Center and email) that the solution is ready.

You have successfully set up billing and roles for Data Security Investigations.

## Task 2 – Create an investigation and scope it

With DSI set up, you'll open an investigation into Contoso's data-exposure incident. In this task, you'll create an investigation using full draft mode — which gives the most control over data sources and scope — and target the users and time window relevant to the incident.

1. In the Microsoft Purview portal, signed in as **Allan Deyoung** (who now holds the DSI roles), select **Data Security Investigations** > **Investigations**.

2. Review the **Investigations dashboard**, which lists the investigations you can access, with their names, descriptions, and status. Select **+ Create investigation**.

3. Choose the creation method. DSI can create investigations from a **Microsoft Defender XDR incident**, an **Insider Risk Management case** (such as the case you created in Lab 6), or **Data Security Posture Management insights** — or manually. For full control, select **Full draft mode**.

> [!NOTE]
> Being able to launch a DSI investigation directly from an Insider Risk Management case or a Defender XDR incident is what ties DSI into the rest of the course: when the Lab 6 insider-risk case or a Defender incident needs deep content analysis, you escalate it into DSI rather than starting from scratch.

4. On the investigation details page, enter:

   - **Name**: `Mark 8 data exposure investigation`
   - **Description**: `Investigates exposure of pre-publication Mark 8 results and compound CX-2087 data during the AI pilot incident.`

   The user who creates the investigation is automatically added as a member.

5. Configure the investigation scope — the data sources and query. Add the data sources relevant to the incident (for example, the mailboxes and sites of the users involved, such as Grady Archie and Isaiah Langer), and set a time window covering the incident.

6. Define the initial query to focus the collection — for example, content containing `CX-2087`, the `Contoso Compound ID` sensitive information type, or referencing Mark 8. Save the investigation scope.

> [!IMPORTANT]
> The data you add to an investigation scope is copied into DSI's Azure-backed storage and billed per gigabyte per month while the investigation is active. Scope tightly — by user, time, and query — to control both cost and noise. Costs are prorated, so deleting an investigation when finished stops further storage charges.

You have successfully created and scoped the Mark 8 data exposure investigation.

## Task 3 – Run AI-powered analysis on the investigation

This is what distinguishes DSI from a keyword search: it reasons over the *content* of the collected data to identify sensitivity and risk, not just metadata. In this task, you'll run the AI analysis over the investigation's data.

1. In the **Mark 8 data exposure investigation**, after the collected data has been indexed, start the AI-powered **deep content analysis**.

2. Use DSI's AI capabilities to examine the content:

   - **Categorize** the collected items by the kind of sensitive data they contain.
   - Run a **semantic search** to find conceptually related content even when the wording differs — DSI can match meaning across dozens of languages (for example, finding a concept expressed as "mot de passe" when searching for "password").
   - Apply a **custom examination focus area** to prioritize the sensitive information most relevant to this incident — for example, focusing the analysis on compound identifiers and pre-publication results rather than general content.

3. Allow DSI to calculate **risk scores** for the items, which rank the collected content by how sensitive and risky it is.

> [!NOTE]
> AI analysis consumes Data Security Investigation Compute Units billed to your Azure subscription, and processing runs on demand. When AI features run, data is temporarily copied to tenant-isolated regional storage within the Microsoft compliance boundary, retained for at most 48 hours, and is not used to train Microsoft's foundation models. Analysis results and the underlying data graph can take 24–48 hours to become fully available after setup. These timings are indicative, not guaranteed.

You have successfully run AI-powered analysis on the investigation.

## Task 4 – Review the findings

The value of the analysis is in what it surfaces. In this task, you'll review the AI-generated findings to understand the scope and severity of the Mark 8 exposure.

1. In the investigation, open the analysis results. Review the items DSI identified as sensitive, sorted by risk score, and read the AI's categorization of what each item contains.

2. Examine a high-risk item to see how DSI establishes context around the information — confirming, for example, that a document contains pre-publication Mark 8 efficacy data or the CX-2087 compound identifier, and noting who had access to it.

3. Use the findings to answer the investigation's core questions: what sensitive data was exposed, how sensitive it is, who could access it, and therefore what the risk to Contoso is. This content-level understanding — not just "a file moved" — is the outcome DSI provides.

You have successfully reviewed the investigation's findings.

## Task 5 – Mitigate the exposed content

An investigation should end in containment. In this task, you'll drive remediation of the exposed content through DSI's mitigation plan, which acts as the investigation's action tracker.

1. In the investigation, select confirmed risky items from the findings and add them to the **Mitigation Plan** — DSI's internal tracker that bridges AI findings and human action.

2. For the items in the mitigation plan, choose the appropriate remediation actions available in DSI, for example:

   - **Purge** exposed items — remove every instance of a specific high-value file or email that was distributed to multiple users.
   - **Revoke access** or coordinate credential actions for the identities involved.

3. Track each item's remediation state in the plan — for example, marking items **In-progress** and then **Complete** as they are remediated — so the investigation has a clear record of what was contained.

4. Optionally, export the mitigation plan (including risk scores and metadata) as a CSV for reporting to Contoso's leadership.

> [!IMPORTANT]
> Purging an item deletes it from the user's mailbox or location, but the copy held in the DSI investigation scope (in Azure storage) remains until you delete the investigation. To remove the collected evidence and stop storage charges, delete the investigation when the incident is fully resolved. If billing was blocked and you cannot open an investigation through the portal to delete it, an administrator can remove it with PowerShell by connecting with `Connect-IPPSSession` and using `Get-ComplianceCase -CaseType DataSecurityInvestigation` and `Remove-ComplianceCase`.

You have successfully mitigated the exposed content through the investigation's mitigation plan.

## Summary

In this lab, you used Data Security Investigations to investigate Contoso Pharmaceuticals' Mark 8 data-exposure incident from detection to containment. You set up DSI's prerequisites — accepting the terms, assigning the DSI roles, and, critically, connecting DSI to an Azure subscription for its pay-as-you-go storage and AI-compute billing. You created an investigation in full draft mode, scoped it to the users, time window, and content relevant to the incident, then ran AI-powered deep content analysis to categorize the collected data, search it semantically, and score its risk. You reviewed the findings to understand what sensitive data was exposed and how serious it was, and drove remediation through the mitigation plan, purging exposed content and tracking each action to completion. Because DSI is billed against an Azure subscription rather than included with E5, this lab depends on that subscription being attached, and investigations should be deleted when finished to stop ongoing storage costs.
