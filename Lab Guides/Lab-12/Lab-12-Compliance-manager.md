---
lab:
  title: Lab 12 — Assess and improve regulatory compliance posture with Compliance Manager
  description: In this lab we reviewed the compliance score, created a regulatory assessment, and worked improvement actions to strengthen compliance posture.
  duration: 15 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Compliance Manager
---

# Lab 12 — Assess and improve regulatory compliance posture with Compliance Manager

Contoso Pharmaceuticals operates under a dense web of regulation — data protection law, health-information privacy, and industry standards — and it needs a way to measure how well its Microsoft 365 environment meets those obligations, prioritize the gaps, and demonstrate progress to auditors. Microsoft Purview Compliance Manager does this: it translates regulations into concrete improvement actions, measures Contoso's posture as a risk-based compliance score, and tracks the evidence and status of each action. In this lab, acting as Allan Deyoung, you'll review Contoso's compliance score, explore the default baseline assessment, create an assessment based on a regulation that matters to Contoso, work an improvement action through assignment and evidence, and see how the controls you built in earlier labs are automatically credited.

Compliance Manager rewards the work done across this course: many of the improvement actions it recommends are exactly the controls configured in earlier labs — data loss prevention, sensitivity labels, retention, insider risk — and it can detect and credit them automatically.

**Learning outcomes.** After this lab you can:

- Interpret the Compliance Manager compliance score and the default Data Protection Baseline.
- Create an assessment based on a regulatory template.
- Work an improvement action — assign it, add evidence, and update its status.
- Explain automatic versus manual testing of improvement actions.
- Explain how improvement actions contribute to the compliance score.

**Tasks**:

1. Review the compliance score and Data Protection Baseline
2. Create a regulatory assessment
3. Explore improvement actions in the assessment
4. Work an improvement action
5. Understand automatic testing and scoring

## Task 1 – Review the compliance score and Data Protection Baseline

Compliance Manager gives you an immediate posture reading through a compliance score, seeded by a default assessment. In this task, you'll review the score and the baseline that produces it.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **Allan Deyoung**, `AllanD@TenantName` (the Tenant Name and password are provided in the Resources tab).

2. Select the **Compliance Manager** solution card. The **Overview** page appears.

	![](./media/image1.png)

3. Review the **Compliance score** at the top of the Overview page. This percentage reflects how many improvement actions have been implemented and tested, weighted by their risk impact.

	![](./media/image2.png)

4. Review the score breakdown, which separates points achieved through **Microsoft-managed actions** (controls Microsoft operates for its cloud) from **your improvement actions** (controls Contoso is responsible for). Note the **Key improvement actions** listed, which are the highest-impact actions you can take next.

5. In the left navigation, select **Assessments**. Confirm the **Data Protection Baseline** assessment is present — this default assessment is what produced your initial score before any custom assessments were created.

	![](./media/image3.png)

> [!NOTE]
> The Data Protection Baseline is a free assessment that doesn't consume a license, and it seeds your compliance score the first time you use Compliance Manager by collecting signals from your Microsoft 365 solutions. The score is a measure of progress and risk reduction, not a guarantee of compliance or a legal assessment. Signals can take time to be reflected in the score. This timing is indicative, not guaranteed.

You have successfully reviewed the compliance score and the Data Protection Baseline assessment.

## Task 2 – Create a regulatory assessment

To measure against a specific regulation, you create an assessment from a template. In this task, you'll create an assessment based on a regulation relevant to Contoso, and assign it to a group.

1. In Compliance Manager, on the **Assessments** page, select **Add assessment** to start the assessment creation wizard.

	![](./media/image4.png)

2. On the **Base your assessment on a regulation** page, select **Select regulation**. Browse or search the templates (Compliance Manager provides ready-to-use templates for hundreds of regulations). Select a regulation relevant to Contoso — for example, a data-protection or health-information regulation such as **HIPAA/HITECH** — then **Save**. Select **Next**.

	![](./media/image5.png)

	![](./media/image6.png)

	![](./media/image7.png)

> [!NOTE]
> Available templates and certain premium templates vary by licensing. The Data Protection Baseline and the AI baseline templates are free; many industry and regional templates are premium. Choose a template your licensing includes. Compliance Manager also offers premium AI-regulation templates that apply to generative AI apps — relevant when you assess the AI protections configured later in the course.

3. On the assessment details page, enter a name, such as `Contoso data protection assessment`.

4. Assign the assessment to a **group**. Groups organize assessments and let you manage them together; select **Create new group**, such as `Contoso Compliance`, then select **Next**.

	![](./media/image8.png)

5. Designate the **services** in scope for the assessment (the Microsoft 365 services the assessment evaluates), then complete the wizard to create the assessment.

	![](./media/image9.png)

	![](./media/image10.png)

	![](./media/image11.png)

6. Open the newly created **Contoso data protection assessment** and review its structure: it contains **controls** (the requirements from the regulation) and, under each control, the **improvement actions** that satisfy it.

	![](./media/image12.png)

	![](./media/image13.png)

You have successfully created a regulatory assessment for Contoso.

## Task 3 – Explore improvement actions in the assessment

Improvement actions are the heart of Compliance Manager — the concrete, assignable steps that satisfy a regulation. In this task, you'll explore the actions in your assessment.

1. In the **Contoso data protection assessment**, select the **Improvement actions** tab (or select a control to see its actions).

2. Review the columns for each improvement action:

   - **Points achieved** — how many of the action's available points have been earned.
   - **Status** — the implementation status of the action.
   - **Test status** — whether the action has been tested and how.
   - **Group** and **Solution** — which assessment group the action belongs to, and where in Microsoft Purview or Microsoft 365 you perform it.

3. Note that many improvement actions correspond to controls configured earlier in this course — for example, actions relating to data loss prevention, sensitivity labeling, encryption, retention, and insider risk. Compliance Manager centralizes these into a single posture view.

4. Select an individual improvement action to open its details page, which shows the recommended implementation guidance, the points available, and the fields for tracking your work.

	![](./media/image14.png)

	![](./media/image15.png)

You have successfully explored the improvement actions in the assessment.

## Task 4 – Work an improvement action

Improvement actions are meant to be worked — assigned to an owner, implemented, evidenced, and marked tested. In this task, you'll take an improvement action through that workflow.

1. In the **Contoso data protection assessment**, select an improvement action that maps to a control you configured earlier — for example, an action about **Apply sensitivity labels to protect ePHI**.

	![](./media/image16.png)

2. On the action's details page, assign it to an owner: select the option to assign the action, and select a user (for example, **Allan Deyoung**) to be responsible for it.

	![](./media/image17.png)

3. Update the **implementation status** — select **Edit details**, set it to **Implemented** for a control you have configured in this course.

	![](./media/image18.png)

	![](./media/image19.png)

4. Add **evidence**: you can use the option to upload a file or add a note documenting how the control is implemented (for example, a note that the DLP policy from Lab 5 is enforced, or a screenshot of the sensitivity-label policy from Lab 4). Evidence, notes, and status updates are all stored within the improvement action.

5. Update the **test status** — for a manually tested action, set it to reflect that you have verified the control (for example, **Implemented** and tested), which qualifies the action for its points.

	![](./media/image20.png)

	![](./media/image21.png)

6. Select **Save and Close**.

	![](./media/image22.png)

7. Confirm the action's **points achieved** and the assessment's score update to reflect the completed action.

	![](./media/image23.png)

> [!NOTE]
> Storing evidence within the improvement action is what makes Compliance Manager defensible for an audit — an auditor can see not just that an action is marked complete, but the evidence behind it. Score changes from a manually updated action are reflected in the assessment; broader recalculation across the tenant can take up to 24 hours. This timing is indicative, not guaranteed.

You have successfully worked an improvement action through assignment, evidence, and status.

## Task 5 – Understand automatic testing and scoring

Not every action requires manual work — Compliance Manager can detect and credit controls automatically. In this task, you'll review automatic testing and how actions roll up into the score.

1. In the assessment's **Improvement actions**, look for actions with a **Test status** of automatically tested. These are actions Compliance Manager verifies by detecting signals from other Microsoft solutions.

	![](./media/image24.png)

	![](./media/image25.png)

2. Understand how automatic testing works: when Compliance Manager detects a signal that a control is implemented — for example, that endpoints are onboarded, that a DLP policy is enforced, or that a sensitivity-label policy is published — it awards the action's points automatically, without you manually updating it. Many of the controls you configured across this course can be credited this way.

3. Review how points roll up into the score. Each improvement action is worth points based on the risk it mitigates; as actions are implemented and tested — manually or automatically — their points contribute to the control's score, then to the assessment's score, and finally to the overall compliance score.

4. Note the distinction that shapes the score: Microsoft-managed actions are counted once, each technical action Contoso manages is counted once, and each non-technical action is counted once per group. This gives an accurate picture of Contoso's true implementation posture across all its assessments.

> [!NOTE]
> Automatic testing is why doing the earlier labs raises the compliance score without extra effort here: as Compliance Manager detects the DLP, labeling, retention, and insider-risk controls you configured, it credits the corresponding actions. Signal detection is not instant and can take time to reflect. This timing is indicative, not guaranteed.

You have successfully reviewed automatic testing and how improvement actions contribute to the compliance score.

## Summary

In this lab, you used Compliance Manager to assess and improve Contoso Pharmaceuticals' regulatory posture. You reviewed the compliance score and the default Data Protection Baseline that seeds it, created an assessment based on a regulation relevant to Contoso and assigned it to a group, and explored the improvement actions that satisfy the regulation's controls. You worked an improvement action end to end — assigning an owner, setting implementation status, storing evidence, and marking it tested — and reviewed how Compliance Manager automatically tests and credits controls by detecting signals from other Microsoft solutions, including many of the protections you configured earlier in this course. The result is a single, evidence-backed, risk-weighted view of how well Contoso meets its obligations, and a prioritized roadmap for closing the gaps.