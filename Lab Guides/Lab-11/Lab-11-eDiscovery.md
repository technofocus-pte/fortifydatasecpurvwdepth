<!--
lab:
  title: Lab 11 — Preserve, search, and export content with eDiscovery
  description: In this lab we created an eDiscovery case, preserved content with a hold policy, searched for responsive content, reviewed and tagged it, and exported it.
  duration: 15 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - eDiscovery
-->

# Lab 11 — Preserve, search, and export content with eDiscovery

When Contoso Pharmaceuticals faces a legal or regulatory matter — a dispute over the Mark 8 program, a regulatory inquiry, or an internal investigation escalated from insider risk — it must preserve the relevant content so it can't be deleted, search across the estate to find what's responsive, review it, and export it for counsel. Microsoft Purview eDiscovery provides this end-to-end workflow across Exchange, SharePoint, OneDrive, and Teams. In this lab, acting as Allan Deyoung, you'll create an eDiscovery case for a Contoso matter, define the people and locations of interest as data sources, preserve them with a hold policy, search for responsive content, review and tag it in a review set, and export it.

> [!Note]
> Microsoft unified Content Search, eDiscovery (Standard), and eDiscovery (Premium) into a single new eDiscovery experience in the Microsoft Purview portal; the classic standalone experiences were retired in 2025. This lab uses the new unified experience. In it, the people and locations whose data you preserve and search are added as **data sources** — a person is added by name (bringing in their mailbox and OneDrive), and shared locations such as SharePoint sites and Teams are added as location data sources. Premium capabilities such as review sets are available on Microsoft 365 E5, which this environment has.

**Learning outcomes.** After this lab you can:
- Assign eDiscovery permissions to an operator.
- Create an eDiscovery case and add people and locations as data sources.
- Preserve content by creating a hold policy.
- Create and run a search to find responsive content.
- Review and tag content in a review set.
- Export content from a review set.


**Tasks**:

1. Assign eDiscovery permissions
1. Create a case
1. Add data sources to the case
1. Preserve content with a hold policy
1. Create and run a search
1. Review and tag content in a review set
1. Export content from the review set


### Task 1 – Assign eDiscovery permissions

In this task, you'll ensure Allan Deyoung can manage eDiscovery cases by adding him to the eDiscovery Manager role group. You perform this as the Global Administrator.

1. In **Microsoft Edge**, navigate to +++https://purview.microsoft.com+++ and sign in as **MOD Administrator**, `admin@TenantName` (the Tenant Name and password are provided in the Resources tab).

1. In the upper-right corner, select **Settings**, then select **Roles and scopes** > **Role groups**.

1. Select **eDiscovery Manager** from the list, select the name not the checkbox. Then select the **Members** tab from the **eDiscovery Manager** pane.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image1.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image2.png)

1. Expand **Add Managers** and select **Choose users**, select the checkbox next to **Allan Deyoung**, then choose **Select**. Select **Next**, then select **Save**, then **Done**. Confirm the warning.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image3.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image4.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image5.png)

    > [!Note]
    > The eDiscovery Manager role lets Allan create and manage the cases he's a member of. A broader eDiscovery Administrator role can access all cases in the organization; Manager is sufficient for this lab. The people who manage cases don't need an E5 license themselves — E5 licensing applies to the users whose data is placed in a review set. Role changes can take a few minutes to take effect. This timing is indicative, not guaranteed.

    You have successfully assigned Allan Deyoung the eDiscovery Manager role.


### Task 2 – Create a case

An eDiscovery case is the container for everything related to one matter — its data sources, hold policies, searches, review sets, and exports. In this task, you'll create the case for Contoso's legal matter.

1. In **Microsoft Edge**, sign in to the Microsoft Purview portal as **Allan Deyoung**, `AllanD@TenantName`.

1. Select the **eDiscovery** solution card, then in the left navigation select **Cases**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image6.png)

1. Select **Create case** (or **+ Create case**).

1. On the case details page, enter the following, then create the case:

    - **Name**:

        `Mark 8 Program Legal Matter`

    - **Description**:

        `Preservation and collection of content relevant to the Mark 8 program dispute.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image7.png)

    The user who creates the case is automatically added as a member.


1. Open the **Mark 8 Program Legal Matter** case. Note the tabs across the case — **Searches**, **Hold policies**, **Review sets**, **Exports**, and **Data sources** — which correspond to the steps you'll work through in this lab.

    > [!Note]
    > A case can also be created directly from an Insider Risk Management case — connecting the investigation you did in Lab 6 to a formal legal matter here. Data sources from the legacy eDiscovery experience don't carry over to the new experience; they must be added again in the new experience.

    You have successfully created the eDiscovery case.


### Task 3 – Add data sources to the case

In the new eDiscovery experience, you define the people and locations relevant to a matter once as **data sources**, then reuse them across hold policies and searches. In this task, you'll add the people of interest and the Mark 8 SharePoint site.

1. In the **Mark 8 Program Legal Matter** case, select the **Data sources** tab.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image8.png)

1. Select **+ Add** (Add data sources) to open the **Add data sources** flyout.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image9.png)

1. Add the people of interest. In the **Search** box, enter a person's name, alias, or email address, then select **Search**. From the results, select the relevant users — for example **Grady Archie**, **Irvin Sayers**, and **Isaiah Langer**. Adding a person includes their Exchange mailbox and OneDrive account as data sources. You can search for people one after another, or separate multiple entries with a semicolon (`;`).

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image10.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image11.png)

1. Add the shared location. In the same **Search** box, enter the **Mark 8 Project Team** SharePoint site by its name or URL, select **Search**, then select the site from the results.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image12.png)

1. When all the people and the site are selected, select **Add**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image13.png)

1. Confirm the people and the site now appear on the **Data sources** tab.

    > [!Note]
    > Defining data sources once and reusing them is a key efficiency of the new experience: the same people and locations you added here become available when you build the hold policy and the search, so you don't re-enter them each time. Adding a person automatically brings in their mailbox and OneDrive; a SharePoint site is added as a location. This timing is indicative, not guaranteed.

    You have successfully added the case's data sources.


### Task 4 – Preserve content with a hold policy

A hold policy preserves content so it can't be permanently deleted or altered while the matter is active — the cornerstone of defensible eDiscovery. In this task, you'll create a hold policy over the data sources you added and apply it.

1. In the **Mark 8 Program Legal Matter** case, select the **Hold policies** tab, then select **New policy**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image14.png)

1. Enter a **policy name** and **description**, for example:

    - **Name**:

        `Mark 8 preservation hold`

    - **Description**:

        `Preserves the mailboxes, OneDrive accounts, and SharePoint site relevant to the Mark 8 matter.`

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image15.png)


1. On the **Hold policy** tab, under **Data sources**, select **Add sources**. Add the people and the **Mark 8 Project Team** site you added in Task 3. You must add at least one data source. Then select **Save and close**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image16.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image17.png)

1. Leave the **Condition builder** empty so the hold preserves **all content** for the selected data sources.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image18.png)

1. Select **Apply hold** to activate the policy. The policy is created in a **Draft** state and becomes active once the hold is applied.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image19.png)

1. Confirm the policy appears on the **Hold policies** tab and that its status changes from **Draft** to active (this can take some time to process).

    > [!Important]
    > When content is on hold, if a user edits or deletes an item, a preserved copy is retained in a hidden location, so nothing relevant is lost during the matter. A hold policy can take up to 24 hours to fully take effect across all locations. Remove hold policies when a matter closes, so content is no longer preserved unnecessarily. These timings are indicative, not guaranteed.

    You have successfully created and applied a hold policy that preserves the case's data sources.


### Task 5 – Create and run a search

With content preserved, you now search for what's actually responsive to the matter. In this task, you'll create a search across the case's data sources, run it, and commit the results to a review set.

1. In the **Mark 8 Program Legal Matter** case, select the **Searches** tab, then select **Create a search**.

1. Give the search a name, such as `Mark 8 responsive content`, and select **Create**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image20.png)

1. Choose the data sources to search — select the people and the **Mark 8 Project Team** site added to the case in Task 3.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image21.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image22.png)

1. Build the search query with the condition builder. Add conditions to find responsive content — for example, content that **contains the keyword** `CX-2087` or `Mark 8`, or that **matches** the `Contoso Compound ID` sensitive information type. You can combine conditions and narrow by date range.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image23.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image24.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image25.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image26.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image27.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image28.png)

1. Select **Continue**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image29.png)

1. In the **Choose search results**, select **Sample**. Select **Run query**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image30.png)

1. Review the returned statistics — the estimated number of items and the locations with hits — to judge whether the query is scoped correctly. Refine the conditions and run the query again if needed.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image31.png)

1. When satisfied with the results, commit the search to a review set: select the option to **Add to a review set**, choose to create a new review set named `Mark 8 review set`, and confirm.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image32.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image33.png)

    > [!Note]
    > Advanced indexing runs as part of the search process, so the search works against a complete, up-to-date index without a separate reindexing step. Committing a search to a review set copies the responsive items into the review set for detailed examination; large result sets can take time to process. This timing is indicative, not guaranteed.

    You have successfully created and run a search and committed the results to a review set.


### Task 6 – Review and tag content in a review set

The review set is where you examine collected content item by item and mark what's relevant. In this task, you'll review the content and tag it. Notably, content that Contoso encrypted in earlier labs is automatically decrypted here so it can be reviewed.

1. In the **Mark 8 Program Legal Matter** case, select the **Review sets** tab, then select the **Mark 8 review set**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image34.png)

1. Review the items in the set. Select an item to view its content in the viewer. Items protected by Contoso's sensitivity labels or Office 365 Message Encryption (from Labs 1 and 4) are automatically decrypted in the review set so their content is readable for the investigation.

    > [!Note]
    > Decrypting encrypted email attachments into a review set requires the reviewer to hold the **RMS Decrypt** role, which is included with the eDiscovery Manager role assigned in Task 1.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image35.png)

1. On the **All items** tab, you can use the **condition builder** on the command bar to filter the review set with no-code conditions such as keywords, dates, senders, or file types. (For more complex filtering, the **Advanced review set explorer**, currently in preview, supports KQL-based queries — it may not be present in every tenant.)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image36.png)

1. Create the tags you'll use to classify content. On the **All items** tab, open the **tagging panel** (the **Tags** control on the command bar), then add a tag group and the individual tags for this review — for example, a single-select group named `Review decision` containing the tags `Responsive` and `Not responsive`, and a tag `Privileged`. Save the tags.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image37.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image38.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image39.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image40.png)

1. Apply the tags to items as you review them: select an item (or several), then select the appropriate tag in the tagging panel. Repeat as you work through the review set.

    > [!Note]
    > Tags created in the tagging panel are specific to this case and review set. For tags you want to reuse across many cases, create a **tag template** centrally under **Settings** > **eDiscovery** > **Tag templates** instead, then apply it to the review set.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image41.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image42.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image43.png)

1. After tagging, filter the review set to exclude the non-responsive items, so only responsive content moves forward to export.

1. On the **All items** tab, select **Query**. Select **Add conditions**, search for `tag`, and select the **Tags** condition, then select **Apply**.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image44.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image45.png)

1. Set the operator to include the responsive tag — choose the **Equals any of** operator and select the `Responsive` tag as the value.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image46.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image47.png)

1. Select **Run query**. The review set list updates to show only the items that are tagged `Responsive`.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image48.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image49.png)

    > [!Important]
    > Automatic decryption in review sets is a deliberate eDiscovery capability: content encrypted with Microsoft Purview Message Encryption, sensitivity labels, or Azure Rights Management is decrypted when added to a review set so it can be reviewed — which is why the labels you applied earlier don't obstruct a legitimate legal investigation. Access to the review set is still controlled by case membership.

    You have successfully reviewed and tagged content in the review set.


### Task 7 – Export content from the review set

The final step delivers the responsive content to counsel. In this task, you'll export the reviewed items from the review set.

1. In the **Mark 8 review set**, on the **All items** tab, filter to your `Responsive` tag so only responsive items are shown. Select the items.

1. On the command bar, select **Export** (or **Action** > **Export**).

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image50.png)

1. On the export configuration page, you can choose the export options — for example, how to organize the exported data, which file versions to include, and which reports to include — then give the export a name `Mark 8 Responsive eDiscovery` and start it.

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image51.png)

1. Monitor the export's progress on the **Exports** tab of the case (or in the **Process manager**).

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image52.png)

    ![](https://raw.githubusercontent.com/technofocus-pte/fortifydatasecpurvwdepth/refs/heads/main/Lab%20Guides/Lab-11/media/image53.png)

1. When the export completes, download the package within the retention window. Confirm the download includes the exported items, an items report listing every item, and a manifest.

    > [!Important]
    > You must download an export within 30 days after it completes. The download package includes the item content plus reports (an items report and a manifest) that document exactly what was exported — important for defensibility. These timings are indicative, not guaranteed.

    You have successfully exported the responsive content from the review set.


## Summary

In this lab, you ran a complete eDiscovery workflow for Contoso Pharmaceuticals using the new unified eDiscovery experience in Microsoft Purview. You assigned the eDiscovery Manager role to Allan Deyoung, created a case for the Mark 8 program legal matter, and defined the people of interest and the Mark 8 Project Team site as reusable data sources. You preserved those sources with a hold policy, created and ran a search to find responsive content, and committed the results to a review set. You reviewed and tagged the content — seeing that items encrypted by Contoso's sensitivity labels and message encryption are automatically decrypted for legitimate review — and exported the responsive items with their reports for counsel. This end-to-end capability lets Contoso respond defensibly to legal and regulatory matters, and it connects to the insider-risk investigations from earlier in the course, which can escalate directly into an eDiscovery case.
