---
lab:
  title: Lab 2 — Detect regulated data with custom sensitive information types, keyword dictionaries, document fingerprinting, and Exact Data Match, and monitor results in Content and Activity Explorer
  description: In this lab we created custom sensitive information types, a keyword dictionary, a document fingerprint, and an Exact Data Match classifier, and monitored classified content in Content and Activity Explorer.
  duration: 30 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft Purview
    - Information Protection
---

# Lab 2 — Detect regulated data with custom sensitive information types, keyword dictionaries, document fingerprinting, and Exact Data Match, and monitor results in Content and Activity Explorer

Contoso Pharmaceuticals cannot protect what it cannot detect. Its most sensitive data takes several different shapes: clinical-trial subject identifiers and investigational compound identifiers that follow fixed patterns, confidential clinical vocabulary that appears in correspondence, standardized forms such as informed-consent documents, and the exact records of enrolled trial participants. Each shape calls for a different detection method. In this lab, acting as Allan Deyoung, you build a coordinated set of classifiers that together recognize Contoso's regulated data — two regular-expression sensitive information types, a keyword-dictionary sensitive information type, a document fingerprint, and an Exact Data Match (EDM) classifier — then verify them explicitly and monitor where classified content lives using Content Explorer and Activity Explorer.

You create the first sensitive information type in the portal to learn the wizard, then create others at scale with PowerShell, the way an administrator manages classifiers in production. Document fingerprinting and EDM each follow their own distinct workflow in the portal. Every classifier is then tested with both a matching and a non-matching sample so its accuracy is proven before it is ever used in a policy.

**Learning outcomes.** After this lab you can:

- Create a regular-expression sensitive information type with supporting keywords in the portal.
- Create sensitive information types at scale with PowerShell, using keyword dictionaries and rule packages.
- Create a document fingerprint from a standard form.
- Create an Exact Data Match classifier that detects exact trial-subject records.
- Test custom classifiers with matching and non-matching samples.
- Monitor classified content using Content Explorer and Activity Explorer.

**Tasks**:

1. Create the Clinical Trial Subject ID sensitive information type
2. Create the Clinical Terms sensitive information type with PowerShell
3. Create the Compound ID sensitive information type with PowerShell
4. Create a document fingerprint from a standard form
5. Create the Clinical Trial Subject EDM classifier
6. Test the sensitive information types
7. Monitor classified content in Content and Activity Explorer

> [!NOTE]
> This lab reuses the `EDM_DataUploaders` security group and the `Allan Deyoung` membership created during Lab 0, and the data files provided with the lab. It does not re-create the group.

## Task 1 – Create the Clinical Trial Subject ID sensitive information type

Contoso identifies clinical-trial participants with a subject ID in the format of `CTS-` followed by six digits, for example `CTS-004512`. Because a subject ID links to a real person's health data, it is regulated under HIPAA and GDPR. In this task, you'll create a custom sensitive information type (SIT) in the portal that recognizes this format supported by nearby clinical keywords. You create this first SIT in the portal to learn the workflow; in the next tasks you'll create others at scale with PowerShell.

1. In **Microsoft Edge**, navigate to **`https://purview.microsoft.com`** and sign in as **Allan Deyoung**, `AllanD@TenantName` (the Tenant Name and account password are provided in the Resources tab).

2. If the **Welcome to the new Microsoft Purview portal** dialog appears, select **Get started**.

3. In the left navigation, select **Solutions** > **Information Protection**.

	![](./media/image1.png)

4. Expand **Classifiers**, then select **Sensitive info types**. On the **Sensitive info types** page, select **+ Create sensitive info type**.

	![](./media/image2.png)

5. On the **Name your sensitive info type** page, enter the following, then select **Next**:

   - **Name**: `Contoso Clinical Trial Subject ID`
   - **Description**: `Detects Contoso clinical-trial subject identifiers (CTS- followed by six digits).`

	![](./media/image3.png)

6. On the **Define patterns for this sensitive info type** page, select **+ Create pattern**.

	![](./media/image4.png)

7. On the **New pattern** flyout, leave **Confidence level** at **Medium confidence**. Select **+ Add primary element**, then select **Regular expression**.

	![](./media/image5.png)

8. On the **Add a regular expression** flyout, enter the following:

   - **ID**: `Subject ID format`
   - **Regular expression**:

```text
   CTS-[0-9]{6}
```

9. Select the radio button for **String match**, then select **Done**.

	![](./media/image6.png)

10. Under **Supporting elements**, select **+ Add supporting elements or group of elements**, then select **Keyword list**.

	![](./media/image7.png)

11. On the **Add a keyword list** flyout, enter the following:

    - **ID**: `Clinical keywords`
    - **Keyword group #1** > **Case insensitive** (one per line):

```text
    subject
    trial
    patient
    protocol
    enrolled
```

12. Select the radio button for **String match**, then select **Done**.

	![](./media/image8.png)

13. Under **Character proximity**, set the **Detect primary AND supporting elements within** value to `300` characters.

14. Select **Create**.

	![](./media/image9.png)

15. Back on the **Define patterns for this sensitive info type** page, select **Next**.

	![](./media/image10.png)

16. On the **Choose the recommended confidence level to show in compliance policies** page, review the default and select **Next**.

	![](./media/image11.png)

17. On the **Review settings and finish** page, review your settings and select **Create**. When the SIT is created, select **Done**.

	![](./media/image12.png)

	![](./media/image13.png)

> [!IMPORTANT]
> This sensitive information type requires a supporting keyword (such as *subject*, *trial*, *patient*, *protocol*, or *enrolled*) within 300 characters of the `CTS-######` value. A bare identifier with no nearby keyword will not match — this is by design, to reduce false positives, and matters when you test the SIT in Task 6.

You have successfully created a sensitive information type that detects Contoso clinical-trial subject identifiers supported by clinical keywords.

## Task 2 – Create the Clinical Terms sensitive information type with PowerShell

In this task, you'll build a sensitive information type that detects Contoso's confidential clinical vocabulary. You first create a keyword dictionary from the clinical terms, capture the dictionary's identity, reference that identity in the provided rule-package file, then import the rule package to create the sensitive information type.

1. On the client VM, open an elevated terminal: right-click the **Start** button and select **Terminal (Administrator)**. Select **Yes** on the User Account Control prompt.

	![](./media/image14.png)

	![](./media/image15.png)

2. Connect to Security & Compliance PowerShell. When the sign-in window appears, sign in as **Allan Deyoung**, `AllanD@TenantName`:

```powershell
   Install-Module ExchangeOnlineManagement
   Import-Module ExchangeOnlineManagement
   Connect-IPPSSession -UserPrincipalName AllanD@TenantName
```

	![](./media/image16.png)

	![](./media/image17.png)

	![](./media/image18.png)

	![](./media/image19.png)

3. Create the keyword dictionary from the confidential clinical terms:

```powershell
   $terms = "influenza`nbronchitis`notitis`nefficacy endpoint`nunblinding`nadverse event`nserious adverse event"
```

	![](./media/image20.png)

```powershell
   $dict = New-DlpKeywordDictionary -Name "Contoso Clinical Terms Dictionary" -Description "Confidential clinical vocabulary for Contoso trials." -FileData ([System.Text.Encoding]::UTF8.GetBytes($terms))
```

	![](./media/image21.png)

   > [!NOTE]
   > The terms are stored in the `$terms` variable separated by `` `n `` (PowerShell's newline character), producing the newline-separated list the dictionary expects. The `-FileData` parameter requires the terms as bytes, which is why the text is wrapped in `[System.Text.Encoding]::UTF8.GetBytes(...)`.

4. Confirm the dictionary was created and capture its identity (GUID). Copy the **Identity** value from the output — you'll paste it into the rule-package file in the next step:

```powershell
   Get-DlpKeywordDictionary -Name "Contoso Clinical Terms Dictionary" | Format-List Name, Identity
```

	![](./media/image22.png)

5. Reference the dictionary in the rule-package file. In **C:\Lab Files**, open `ClinicalTerms-RulePackage.xml` in a text editor such as Notepad. Locate the `<IdMatch>` element, which contains the placeholder `idRef="REPLACE-WITH-DICTIONARY-GUID"`, and replace `REPLACE-WITH-DICTIONARY-GUID` with the **Identity** GUID you copied in step 4 (for example, `idRef="6f2161a1-8055-4672-b1a5-d5953ad56d3a"`). Save the file, keeping its **UTF-16 (Unicode)** encoding.

   > [!IMPORTANT]
   > The keyword dictionary is referenced directly by its GUID in the `<IdMatch>` element — the GUID *is* the reference to the dictionary. The dictionary GUID is unique to your tenant, so this replacement must be done in your own environment; if the tenant is reset, the dictionary receives a new GUID and this step must be repeated. The file must remain UTF-16 (Unicode) encoded or the import will fail.

6. Import the rule package to create the sensitive information type. This uses the edited `ClinicalTerms-RulePackage.xml` file, which now references your dictionary:

```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes("C:\Lab Files\ClinicalTerms-RulePackage.xml"))
```

	![](./media/image23.png)

7. Confirm the new sensitive information type exists:

```powershell
   Get-DlpSensitiveInformationType -Identity "Contoso Clinical Terms" | Format-List Name, Publisher, Type
```

	![](./media/image24.png)

8. Verify the sensitive information type detects the clinical vocabulary. Run a classification test against sample text that contains dictionary terms near a clinical context word:

```powershell
   (Test-DataClassification -TextToClassify "The efficacy endpoint was met; one serious adverse event was recorded for this confidential subject during unblinding." -ClassificationNames "Contoso Clinical Terms").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```
   Confirm the result shows `Contoso Clinical Terms` with a count of at least 1.

	![](./media/image25.png)

   > [!IMPORTANT]
   > Changes to custom sensitive information types can take up to one hour to become active across all locations. If the classification test returns no result immediately after import, wait and retry before concluding the rule package is incorrect — a delayed match is usually propagation, not a configuration error. This timing is indicative, not guaranteed.

You have successfully created a keyword-dictionary sensitive information type that detects Contoso's confidential clinical vocabulary.

## Task 3 – Create the Compound ID sensitive information type with PowerShell

Contoso identifies investigational compounds with a compound ID in the format of `CX-` followed by four digits, for example `CX-2087`. Like the clinical vocabulary in the previous task, this is created at scale with PowerShell from a provided rule package. In this task, you'll upload the rule package that defines the Compound ID sensitive information type, then confirm and test it.

1. On the client VM, open **C:\Lab Files** and verify the provided **CompoundID-RulePackage.xml** file is present.

2. Return to the elevated **Terminal (Administrator)** window, still connected to Security & Compliance PowerShell from Task 2. If the session has timed out, reconnect:

```powershell
   Connect-IPPSSession -UserPrincipalName AllanD@TenantName
```

3. Upload the rule package to create the sensitive information type:

```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes("C:\Lab Files\CompoundID-RulePackage.xml"))
```

	![](./media/image26.png)

4. Confirm the new sensitive information type exists:

```powershell
   Get-DlpSensitiveInformationType -Identity "Contoso Compound ID" | Format-List Name, Publisher, Type
```

	![](./media/image27.png)

5. Verify the sensitive information type detects a compound ID near a context word. Confirm the result lists `Contoso Compound ID` with a count of at least 1:

```powershell
   (Test-DataClassification -ClassificationNames "Contoso Compound ID" -TextToClassify "Investigational compound CX-2087 confidential formulation.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

	![](./media/image28.png)

6. Test with a non-matching sample. The command prints nothing, because `CX-20` has only two digits and no compound identifier is present:

```powershell
   (Test-DataClassification -ClassificationNames "Contoso Compound ID" -TextToClassify "Conference room CX-20 is booked for the afternoon.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

	![](./media/image29.png)

> [!IMPORTANT]
> Like the other custom sensitive information types, the Compound ID pattern requires a supporting context word (such as *compound*, *formulation*, *investigational*, or *confidential*) within 300 characters of the `CX-####` value — a bare identifier with no nearby context word will not match. Changes to custom sensitive information types can take up to one hour to become active; an empty result immediately after upload is usually propagation, not an error. This timing is indicative, not guaranteed.

You have successfully created the Compound ID sensitive information type at scale with PowerShell.

## Task 4 – Create a document fingerprint from a standard form

Contoso uses a standard informed-consent form for its clinical trials. Rather than trying to describe that document with patterns or keywords, you can fingerprint it: Microsoft Purview reads the form's structure and creates a sensitive information type that detects that form and documents based on it. In this task, you'll create a document fingerprint from the provided consent-form template.

1. In **Microsoft Edge**, in the Microsoft Purview portal as **Allan Deyoung**, select **Solutions** > **Information Protection** > **Classifiers** > **Sensitive info types**.

2. On the **Sensitive info types** page, select **+ Create Fingerprint based SIT**.

	![](./media/image30.png)

3. On the **Name your sensitive info type** page, enter the following, then select **Next**:

   - **Name**: `Contoso Consent Form`
   - **Description**: `Detects Contoso clinical-trial informed-consent forms using document fingerprinting.`

	![](./media/image31.png)

4. On the **Upload a file to create a fingerprint for the file** page, select **Upload file**.

5. Select the provided `Clinical Trial Consent Form Template.docx` file from **C:\Lab Files**, then select **Open**.

6. Review the detection threshold at the default, then select **Next**.

	![](./media/image32.png)

7. On the **Review settings and finish** page, review your settings and select **Create**.

	![](./media/image33.png)

8. When the SIT is created, select **Done**.

	![](./media/image34.png)

> [!NOTE]
> Document fingerprinting stores only a hash of the form's structure, not the document itself — the original cannot be reconstructed from the fingerprint. A fingerprint SIT detects both the exact form and documents built from it, and can be used in DLP and auto-labeling policies across Exchange, SharePoint, OneDrive, Teams, and endpoints.

You have successfully created a document-fingerprint sensitive information type from Contoso's standard consent form.

## Task 5 – Create the Clinical Trial Subject EDM classifier

A pattern detects a format; an Exact Data Match classifier detects the exact records in a specific data set, which dramatically reduces false positives — essential for clinical-trial data, where you want to detect real enrolled participants and nothing else. In this task, you'll create an EDM classifier that matches against Contoso's trial-subject registry, using the Subject ID SIT from Task 1 as the primary-element detector, then hash and upload the registry with the EDM Upload Agent. The `EDM_DataUploaders` group and your membership were created in Lab 0.

1. In **Microsoft Edge**, in the Microsoft Purview portal as **Allan Deyoung**, select **Solutions** > **Data classification**, then select **EDM classifiers**.

2. Make sure the **New EDM experience** toggle is set to **On**.

	![](./media/image35.png)

3. Select **+ Create EDM classifier**.

	![](./media/image36.png)

4. On the naming page, enter the following, then select **Next**:

   - **Name**: `Contoso Clinical Trial Subjects`
   - **Description**: `Exact match against the Contoso clinical-trial subject registry.`

	![](./media/image37.png)

5. On the schema-method page, select **Manually define your data structure**, then select **Next**.

	![](./media/image38.png)

6. On the **Define columns** page, add the following four columns. Each must match a header in the provided `ClinicalTrialSubjects.csv` file exactly:

   - `SubjectName`
   - `DateOfBirth`
   - `MedicalRecordNumber`
   - `SubjectID`

7. Select **Next**.

	![](./media/image39.png)

8. On the **Select primary elements** page, locate the **SubjectID** row and expand its **Match mode** dropdown. Under **Sensitive Info type (SIT)**, select the edit (pencil) icon, search for `Contoso`, select the **Contoso Clinical Trial Subject ID** SIT you created in Task 1, then select **Save**. Select the checkbox to designate **SubjectID** as a **Primary element**, then select **Next**.

	![](./media/image40.png)

	![](./media/image41.png)

	![](./media/image42.png)

	![](./media/image43.png)

9. On the **Configure settings for data in selected columns** page, leave **Use the same settings for all columns** set to **On**. Select the option to **Ignore delimiters and punctuation for data in all columns**, then select **Hyphen**, **Underscore**, **Close Parenthesis** and **Open Parenthesis**. Select **Next**.

	![](./media/image44.png)

10. On the **Configure detection rules for primary elements** page, review the defaults, then select **Next**.

	![](./media/image45.png)

11. On the review page, select **Submit**.

	![](./media/image46.png)

12. Note the **schema name** shown on the confirmation page, then select **Done**.

	![](./media/image47.png)

> [!NOTE]
> Wait at least one hour after creating the schema before downloading it in step 17. If the schema is downloaded too soon, the command can fail because it hasn't finished syncing. You can install the EDM Upload Agent (steps below) during the wait. This timing is indicative, not guaranteed.

13. Download the EDM Upload Agent. In **Microsoft Edge**, navigate to **`https://go.microsoft.com/fwlink/?linkid=2088639`** to download the installer.

14. Open the installer. In the setup wizard, select **Next**, accept the license agreement, keep the default destination folder, select **Install**, approve the User Account Control prompt, then select **Finish**.

15. In the elevated terminal, change to the EDM Upload Agent directory:

```powershell
    cd "C:\Program Files\Microsoft\EdmUploadAgent"
```

	![](./media/image48.png)

16. Authorize the agent. When prompted, sign in as **Allan Deyoung**:

```powershell
    .\EdmUploadAgent.exe /Authorize
```

17. Download the schema you created. Replace `<schemaName>` with the schema name you noted in step 12:

```powershell
    .\EdmUploadAgent.exe /SaveSchema /DataStoreName <schemaName> /OutputDir "C:\Lab Files"
```

	![](./media/image49.png)

18. Hash and upload the provided `ClinicalTrialSubjects.csv` file. Replace `<schemaName>` with the same schema name:

```powershell
    .\EdmUploadAgent.exe /UploadData /DataStoreName <schemaName> /DataFile "C:\Lab Files\ClinicalTrialSubjects.csv" /HashLocation "C:\Lab Files" /Schema "C:\Lab Files\<schemaName>.xml"
```

	![](./media/image50.png)

19. Check the upload status. Replace `<schemaName>` with the same schema name, and re-run until the status shows completed:

```powershell
    .\EdmUploadAgent.exe /GetSession /DataStoreName <schemaName>
```

	![](./media/image51.png)

> [!IMPORTANT]
> If the upload fails with a permissions error, the `EDM_DataUploaders` group membership from Lab 0 may still be propagating — wait and retry. The hashing and indexing process is not instant; the session status can take minutes to hours to reach completed.

You have successfully created an EDM classifier and uploaded the trial-subject registry that powers it.

## Task 6 – Test the sensitive information types

Custom classifiers should always be tested before they are used in policies, so that a misconfigured pattern doesn't cause data loss or missed detections. In this task, you'll test each classifier with a matching and a non-matching sample and confirm the results.

> [!NOTE]
> Custom sensitive information types are created immediately but can take **45–60 minutes** to become active in the classification engine that `Test-DataClassification` uses. If your test returns an empty result, this is expected propagation delay, not an error. Continue to the next lab and return to run the verification tests later, either after 45–60 minutes or once you have completed the remaining labs. The Exact Data Match type (`Contoso Clinical Trial Subjects`) can take longer still, as its data must also be uploaded and indexed.

1. On the client VM, open an elevated terminal: right-click the **Start** button and select **Terminal (Administrator)**. Select **Yes** on the User Account Control prompt.

2. Connect to Security & Compliance PowerShell. When the sign-in window appears, sign in as **Allan Deyoung**, `AllanD@TenantName`:

```powershell
   Import-Module ExchangeOnlineManagement
   Connect-IPPSSession -UserPrincipalName AllanD@TenantName
```

3. Test the **Clinical Trial Subject ID** SIT with a matching sample. Confirm the result lists `Contoso Clinical Trial Subject ID` with a count of `1`:

```powershell
   (Test-DataClassification -ClassificationNames "Contoso Clinical Trial Subject ID" -TextToClassify "Trial subject CTS-004512 was enrolled at the study site.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

	![](./media/image52.png)

4. Test the same SIT with a non-matching sample. The command prints nothing, because `CTS-45120` has only five digits:

```powershell
   (Test-DataClassification -ClassificationNames "Contoso Clinical Trial Subject ID" -TextToClassify "Reference code CTS-45120 is unrelated.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

	![](./media/image53.png)

5. Test the **Clinical Terms** SIT with the provided files. In **Microsoft Edge**, in the Microsoft Purview portal, go to **Solutions** > **Information Protection** > **Classifiers** > **Sensitive info types**. Search for `Contoso Clinical Terms`, select it, then select **Test**.

	![](./media/image54.png)

6. On the **Upload file to test** flyout, select **Upload file**, select the provided `ClinicalTerms-Match.txt` from **C:\Lab Files**, then select **Open**. Select **Test**. On the **Match results** page, confirm a match is found, then select **Finish**.

	![](./media/image55.png)

	![](./media/image56.png)

	![](./media/image57.png)

7. Select **Test** again and repeat with `ClinicalTerms-NoMatch.txt`. Confirm the result reports no matches, then select **Finish**.

	![](./media/image58.png)

	![](./media/image59.png)

	![](./media/image60.png)

	![](./media/image61.png)

8. Test the **Compound ID** SIT with a matching sample. Confirm the result lists `Contoso Compound ID` with a count of at least 1:

```powershell
   (Test-DataClassification -ClassificationNames "Contoso Compound ID" -TextToClassify "Investigational compound CX-2087 confidential formulation.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

	![](./media/image62.png)

9. Test the **EDM classifier** with a record from the registry. In the elevated terminal, run the following and confirm the result lists `Contoso Clinical Trial Subjects` with a count of `1`. The values used are a real record in `ClinicalTrialSubjects.csv`:

```powershell
   (Test-DataClassification -ClassificationNames "Contoso Clinical Trial Subjects" -TextToClassify "Subject record: Avery Howell, CTS-004512, MRN-7781422.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

	![](./media/image63.png)

> [!IMPORTANT]
> Each regular-expression and keyword sensitive information type requires a supporting context word near the pattern (for example, *subject* near a `CTS-######` value, or *compound* near a `CX-####` value), so the test samples above deliberately include one. A bare identifier on its own will not match. Unlike a pattern SIT, an EDM classifier must also finish indexing the uploaded hash and propagate across the service before it will match — it is normal for the EDM test in step 9 to return no result on the same day the data is uploaded; re-run it later, as Microsoft advises allowing up to 24 hours. These timings are indicative, not guaranteed.

You have successfully tested the sensitive information types, confirming each detects genuine regulated data while ignoring near-misses.

## Task 7 – Monitor classified content in Content and Activity Explorer

Creating classifiers is only useful if you can see what they find. Content Explorer shows where classified content currently lives across your data estate, and Activity Explorer shows what is happening to that content — labels applied, files shared, and more. In this task, you'll use both to see the classifiers at work.

1. In **Microsoft Edge**, in the Microsoft Purview portal as **Allan Deyoung**, select **Solutions** > **Information Protection** > **Explorers** > **Content explorer**.

	![](./media/image64.png)

2. In the **Content explorer** view, under **Sensitive info types**, locate and select **Contoso Clinical Trial Subject ID**. The right pane lists the SharePoint, OneDrive, and Exchange locations where content matching that classifier has been found.

	![](./media/image65.png)

3. Select an item in the results to see which classifier matched and where the content resides. Review how Content Explorer lets you confirm that your classifier is detecting real content across the estate.

4. In the left navigation, select **Activity explorer**.

	![](./media/image66.png)

5. In the **Activity explorer** view, use the **Filter** control to filter by **Activity type**. Review the activities recorded against classified content — for example, files being accessed, labeled, or shared.

	![](./media/image67.png)

> [!NOTE]
> Content Explorer and Activity Explorer depend on the classification and audit data that Microsoft Purview gathers across your tenant, which is not immediate. Newly created classifiers and recently added content can take several hours to appear, and up to 24–48 hours for a first full scan of existing SharePoint and OneDrive content. If a classifier shows no results yet, it is still scanning. These timings are indicative, not guaranteed.

You have successfully used Content Explorer and Activity Explorer to monitor where classified content lives and what is happening to it.

## Summary

In this lab, you built a coordinated set of classifiers that together detect Contoso Pharmaceuticals' regulated data in its several forms: a regular-expression sensitive information type for subject identifiers, a second regular-expression sensitive information type for investigational compound identifiers, a keyword-dictionary sensitive information type for confidential clinical vocabulary, a document fingerprint for the standard consent form, and an Exact Data Match classifier for exact trial-subject records. You created the first in the portal, the next two at scale with PowerShell, and used the distinct fingerprinting and EDM workflows for the others. You then tested each classifier with matching and non-matching samples and used Content Explorer and Activity Explorer to monitor classified content across the estate. These classifiers are the detection foundation that the labeling, DLP, retention, and AI-protection labs build on.

## Script notes

*Plain-English explanations of every command used in this lab, for verification by a non-technical reader. The code itself lives in the task steps; this section only explains it.*

### Task 2 — connecting and creating a keyword-dictionary classifier

```powershell
Import-Module ExchangeOnlineManagement
Connect-IPPSSession -UserPrincipalName AllanD@TenantName
```

- **What it does:** Loads the management toolset and signs you in to Security & Compliance PowerShell, where classifiers are managed. `IPPS` stands for "Information Protection & Compliance PowerShell."
- **To substitute:** replace `TenantName` with the tenant name from the Resources tab. Sign in as Allan Deyoung when the window appears.
- **What you should see:** the prompt returns with no red error text.

```powershell
$terms = "influenza`nbronchitis`notitis`nefficacy endpoint`nunblinding`nadverse event`nserious adverse event"
$dict = New-DlpKeywordDictionary -Name "Contoso Clinical Terms Dictionary" -Description "Confidential clinical vocabulary for Contoso trials." -FileData ([System.Text.Encoding]::UTF8.GetBytes($terms))
```

- **What it does:** Creates a reusable keyword dictionary — a named list of terms the classifier will look for. The first line stores the list of terms in a variable called `$terms`. The second line creates the dictionary from those terms.
- **The parts, in plain English:** the first line stores the terms in the `$terms` variable, separated by `` `n `` (PowerShell's newline character). `New-DlpKeywordDictionary` is the command that creates the dictionary; `-Name` and `-Description` label it; `-FileData` takes the terms as file data. The `[System.Text.Encoding]::UTF8.GetBytes($terms)` piece converts the text into the bytes the command expects.
- **To substitute:** nothing for the lab; in production you'd use your own terms.
- **What you should see:** the command completes with no red error text.

```powershell
Get-DlpKeywordDictionary -Name "Contoso Clinical Terms Dictionary" | Format-List Name, Identity
```

- **What it does:** Confirms the dictionary exists and shows its **Identity** — a unique ID (GUID). You need this ID because the rule package in the next step refers to the dictionary by it.
- **What you should see:** the dictionary's name and a long GUID value. Note the GUID; you paste it into the rule package.

```powershell
New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes("C:\Lab Files\ClinicalTerms-RulePackage.xml"))
```

- **What it does:** Uploads the edited rule package XML, which creates the `Contoso Clinical Terms` sensitive information type. The rule package ties the keyword dictionary (as the main thing to detect) to a few supporting context words.
- **The `([System.IO.File]::ReadAllBytes("..."))` part** reads the file from disk and hands its contents to the command — think of it as "open this file and use what's inside."
- **To substitute:** confirm the file is in `C:\Lab Files`, that you replaced the placeholder GUID in the `<IdMatch>` element with the GUID from the previous command, and that the file is saved as UTF-16 (Unicode) before running this.
- **What you should see:** the command completes with no red error text.

```powershell
Get-DlpSensitiveInformationType -Identity "Contoso Clinical Terms" | Format-List Name, Publisher, Type
```

- **What it does:** Confirms the new sensitive information type now exists, by asking for it by name.
- **What you should see:** the name, a non-Microsoft publisher, and a type of `Entity`.

```powershell
$test = "The efficacy endpoint was met; one serious adverse event was recorded for this confidential subject during unblinding."
(Test-DataClassification -TextToClassify $test -ClassificationNames "Contoso Clinical Terms").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

- **What it does:** Scans a sample sentence and reports whether the classifier matched, printing a readable line such as `Contoso Clinical Terms: 1`.
- **Why the `(...).ClassificationResults | ForEach-Object {...}` wrapper:** on its own the command returns each result as a hashtable, which `Format-Table` cannot display by column name (it shows an empty table). Looping with `ForEach-Object` and reading the `ClassificationName` and `Count` keys prints a readable result.
- **To substitute:** nothing needs changing; the sample deliberately includes a context word so the SIT matches.

### Task 3 — creating a second sensitive information type from a rule package

```powershell
New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes("C:\Lab Files\CompoundID-RulePackage.xml"))
```

- **What it does:** Uploads the provided `CompoundID-RulePackage.xml`, which creates the `Contoso Compound ID` sensitive information type — a regular-expression pattern (`CX-` followed by four digits) supported by nearby context words. Unlike the Clinical Terms rule package, this one contains no keyword dictionary and needs no GUID replacement.
- **To substitute:** confirm the file is in `C:\Lab Files` and is saved as UTF-16 (Unicode).
- **What you should see:** the command completes with no red error text.

```powershell
Get-DlpSensitiveInformationType -Identity "Contoso Compound ID" | Format-List Name, Publisher, Type
```

- **What it does:** Confirms the new sensitive information type exists.
- **What you should see:** the name, a non-Microsoft publisher, and a type of `Entity`.

```powershell
(Test-DataClassification -ClassificationNames "Contoso Compound ID" -TextToClassify "Investigational compound CX-2087 confidential formulation.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

- **What it does:** Scans a sample sentence and reports whether the Compound ID classifier matched, printing a line such as `Contoso Compound ID: 1`.
- **To substitute:** nothing needs changing; the sample includes both the `CX-2087` pattern and a context word (`compound`, `formulation`), which the SIT requires.

### Task 5 — the EDM Upload Agent commands

```powershell
cd "C:\Program Files\Microsoft\EdmUploadAgent"
.\EdmUploadAgent.exe /Authorize
.\EdmUploadAgent.exe /SaveSchema /DataStoreName <schemaName> /OutputDir "C:\Lab Files"
```

- **What it does:** `cd` moves the terminal into the folder where the EDM Upload Agent is installed (you must run the tool from its own folder). `/Authorize` signs the tool in to your tenant — a sign-in window appears; use Allan Deyoung. `/SaveSchema` downloads the schema definition (the blueprint of your four columns) to `C:\Lab Files`, which the next command needs.
- **`.\`** before the program name means "the program in this current folder."
- **To substitute:** `<schemaName>` — paste the schema name shown on the confirmation page in step 12 (your classifier's name followed by the word *schema*). It appears here and in the next two blocks; use the same value each time.
- **What you should see:** each command reports success. If `/SaveSchema` fails, the schema likely hasn't finished syncing — wait (up to an hour from creation) and retry.

```powershell
.\EdmUploadAgent.exe /UploadData /DataStoreName <schemaName> /DataFile "C:\Lab Files\ClinicalTrialSubjects.csv" /HashLocation "C:\Lab Files" /Schema "C:\Lab Files\<schemaName>.xml"
.\EdmUploadAgent.exe /GetSession /DataStoreName <schemaName>
```

- **What it does:** The first command takes the clear-text registry (`ClinicalTrialSubjects.csv`), scrambles it into a secure one-way "hash" so the real values are never uploaded, and sends that hash to your tenant to power exact-match detection. `/HashLocation` is where it writes the temporary hash file; `/Schema` points to the schema file downloaded in the previous block. The second command checks the upload's progress.
- **To substitute:** `<schemaName>` in three places (twice as the data-store name, once inside the schema file name `<schemaName>.xml`); use the same value from step 12.
- **What you should see:** the upload reports success; re-run the `/GetSession` command until it shows the session completed. This can take minutes to hours.

### Task 6 — testing classifiers

```powershell
(Test-DataClassification -ClassificationNames "Contoso Clinical Trial Subject ID" -TextToClassify "Trial subject CTS-004512 was enrolled at the study site.").ClassificationResults | ForEach-Object { "$($_.ClassificationName): $($_.Count)" }
```

- **What it does:** Scans a sample sentence and reports whether the named classifier matched, printing a readable line such as `Contoso Clinical Trial Subject ID: 1`.
- **Why the `(...).ClassificationResults | ForEach-Object {...}` wrapper:** on its own the command returns each result as a hashtable, which `Format-Table` cannot display by column name (it shows an empty table). Looping with `ForEach-Object` and reading the `ClassificationName` and `Count` keys prints a readable line.
- **To substitute:** nothing needs changing; the matching samples deliberately include a context word, and the non-matching samples print nothing. The same pattern tests the EDM classifier with a real registry record — for EDM, a same-day empty result is expected while the hash indexes and propagates (up to 24 hours).