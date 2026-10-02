# Exercise 2 — Active Cost Centers for India

In this exercise, you will build a derived data product for non-blocked cost centers filtered to India. The agent will surface a date-handling constraint and ask how you want to resolve it, then you will refine the result for a specific geography.

**What you will build:** A data product exposing active, non-blocked cost centers for India, with validity dates available for consumers to apply their own as-of-date logic.

**Time:** ~50 minutes

> **Before you begin:** Your solution name includes a participant ID provided by the session owner. Keep it ready.

---

## Exercise 1 — Start the Core Data Product

1. Select **+ New**, then **Data Product**. Keep **Solution** set to **New Solution**.
2. In the **Name** field, enter:

   ```
   DA161 <participant ID> Cost Center Analytics
   ```

   Replace `<participant ID>` with the identifier provided by the session owner.

3. In the **Intent Statement** field, paste the following exactly:

> **Paste this:**
> ```
> Create a derived data product for active cost centers with fields: cost center ID, name, company code, responsible person, validity dates, and status. start with intent-analysis
> ```

4. Leave **Quick Create** unchecked. Click **Create** and wait for the workspace to open.
<br>![New solution with cost center intent statement](images/02_01_0010.png)

✓ **Checkpoint** — You should see: your named solution is open and the cost center request appears in the Joule conversation panel. Wait for source discovery — do not submit a second request.

---

## Exercise 2 — Confirm the Source and Business Goal

1. Review the **Cost Center** source recommendation. The expected source is `sap.s4com:dataProduct:CostCenter:v1`. If you see a different source or changed fields, ask a workshop assistant before continuing.
2. Choose **Create a new derived data product**, then **Multiple consumers (all of the above)**. Select **Submit Answer** after each choice.
<br>![Choosing source type and consumer options](images/02_02_0010.png)

3. When asked what **active** means, choose **Both — validity dates AND status**. This captures the full business meaning.

4. When asked for a measurable business outcome, paste:

> **Paste this:**
> ```
> Reduce time spent on cost center lookups by 50%
> ```

5. Choose **No specific timeline** if asked for a baseline.

✓ **Checkpoint** — You should see: Joule records Cost Center as the source, multiple consumers, the active definition (dates and status), and the business target.

---

## Exercise 3 — Review the Intent and Build Plan

1. Review the **Intent Analysis Summary**. Check that it includes: the Cost Center source, the requested attributes (cost center ID, name, company code, responsible person, validity dates, status), multiple consumers, and the filtering intent.
2. Select **Yes, proceed to PRD** (or **Generate Requirements** if that is the button shown).

3. Verify the generated requirements include:
   - Fields: cost center ID, name, company code, responsible person, validity start and end dates, and status
   - Value: simpler cost center lookup for finance, reporting, agents, and automated processes
   - Scope: derive and filter the available source — creating or editing cost centers and postings is outside scope

4. Proceed to the specification when prompted.

5. When Joule indicates the specification is ready, paste:

> **Paste this:**
> ```
> execute specification/specification.md
> ```

✓ **Checkpoint** — You should see: Intent, Requirements, and Specifications available. Joule begins building `active-cost-centers-data-product` or the equivalent generated asset.

---

## Exercise 4 — Review the Product Metadata

1. Wait for tooling preparation to complete. If Joule reports an error, wait for explicit recovery before continuing. Ask for help if it repeats.

2. Before approving the properties, paste:

> **Paste this:**
> ```
> Can you give a more detailed description?
> ```
<br>![Requesting a more detailed description](images/02_04_0010.png)

3. Check that the revised description explains: purpose, fields, consumers, and the Cost Center source.

4. Verify the proposed properties:

   | Property | Expected value |
   |---|---|
   | Technical Name | `ActiveCostCenters` |
   | Business Name | `Active Cost Centers` |

5. Select **Approve** when the revised properties are presented.

✓ **Checkpoint** — You should see: the message **"Properties approved"** and Joule preparing the schema and authorization information.

---

## Exercise 5 — Date Handling and Authorization

1. Read the filter confirmation. Joule reports that `current_date()` cannot be used inside the generated data product.

2. Select **Omit the date filter (recommended — expose dates as fields for consumers)**. Select **Submit Answer**.
<br>![Choosing to expose validity dates for consumers](images/02_05_0010.png)

3. Keep the status filtering — all seven blocking indicators must be false for a record to pass.

> **What this means:** The product returns non-blocked records and exposes `ValidityStartDate` and `ValidityEndDate`. A consumer must apply: `ValidityStartDate <= chosen as-of date <= ValidityEndDate`. A record can be non-blocked and still be outside its valid date range.

✓ **Checkpoint** — You should see: the consumer-side date approach recorded and both validity dates confirmed as available.

4. Choose **Use recommended only (Cost Center + Controlling Area)** at the authorization question. Select **Submit Answer**.
<br>![Confirming authorization fields](images/02_05b_0010.png)

5. Wait for **"AMS policy injected"** and solution setup to complete.

✓ **Checkpoint** — You should see: an initial summary showing `ActiveCostCentersDimension`, with Cost Center and Controlling Area as the initial policy fields. Joule offers **Approve** or **Make a change**.

---

## Exercise 6 — Refine for India

1. Choose **Make a change**, then **Other (I'll describe)**. Submit the choices, then paste:

> **Paste this:**
> ```
> I would like to filter only active cost centers for India region and exclude blocked entries.
> ```

2. Wait for regeneration.

3. At the policy question, choose **Yes, keep Cost Center + Controlling Area**. Submit.
<br>![Retaining policy fields after India refinement](images/02_06b_0010.png)

4. Check the updated summary against this list:

   - Country = IN
   - All seven blocking indicators = false
   - English names (Language = EN)
   - Country included in the output
   - Both `ValidityStartDate` and `ValidityEndDate` exposed

✓ **Checkpoint** — You should see: the India cost center definition generated with all of the above confirmed.

---

## Exercise 7 — Inspect and Complete the Core Build

1. Under **Solution Artifacts**, select `active-cost-centers-data-product` (or the equivalent generated asset name).

2. In **Objects and Transformations**, inspect `CostCenter`, `CostCenterText`, and the output columns.

3. Select the transformation and choose **View Graphical Transformation** where available. Follow the inputs through join, filter, and projection.
<br>![Graphical transformation view showing join, filter, and projection](images/02_07b_0010.png)

> **Note:** The graphical viewer is read-only. To request edits, use the Joule conversation panel.

4. In the **File tree**, locate:
   - `ActiveCostCenters.dpd`
   - `transformation.cds`
   - `asset.yaml`
   - `solution.yaml`

   File names may vary with the generated identity.

✓ **Checkpoint** — You should see: the India-filtered definition, its source inputs, output fields, policy summary, and generated files all accessible.

---

## Stopping Point

**Finishing the core build:** Read the updated summary. If everything looks correct, choose **Approve — looks good**. Keep your solution identifier.

> **Do not click Deploy.** Deployment is not demonstrated in this session.

Your result in one sentence: *"Non-blocked India cost centers, with validity dates for consumer filtering and reviewed policy fields."*

---

**Continuing to the optional extension:** Keep the current review open and proceed to [Exercise 3 — Planned Budget Extension](../ex3/README.md). You will choose **Make another change** at the start of that exercise.
