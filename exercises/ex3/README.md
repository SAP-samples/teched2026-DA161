# Exercise 3 — Planned Budget Extension *(Optional)*

> **This exercise is optional.** Complete [Exercise 2](../ex2/README.md) through the core stopping point checkpoint before continuing here.

In this exercise, you will extend your India cost center data product with planned budget amounts from a second source. The agent will surface a data gap — no actual cost posting data is available — and ask you to decide how to proceed. You will add Financial Planning Entry Item, approve the aggregation scope, inspect the result, and review a mock preview.

**What you will add:** Planned budget amounts per cost center, drawn from Financial Planning Entry Item data.

**Time:** ~20 minutes, followed by about 5 minutes for the recap

**Keep these distinctions clear:**
- The extension provides **planned** amounts across all planning periods. It does **not** calculate budget utilization, because the search finds no actual cost posting source.
- Preview rows are simulated test data, not live customer data.
- This exercise ends at a reviewed definition. Deployment and live-data testing are separate activities.

The extension needs the **Financial Planning Entry Item** source. Joule searches for it during the exercise. Ask a workshop assistant if it is unavailable. For a structured question, choose the answer and select **Submit Answer**, and compare the meaning when Joule's wording varies. If something fails or looks different from the screenshots, see [Troubleshooting](#troubleshooting) at the end of this exercise.

---

## Exercise 8 — Discover the Budget Source Gap

**Goal:** Request the metric and evaluate the source gap.

1. At the review question in your existing solution, choose **Make another change**, then **Other (I'll describe)**. Submit the choices, then paste:

> **Paste this:**
> ```
> I would like to see budget utilization percentages.
> ```

   If you already approved the core build, send the request in its existing conversation.

2. Read the agent's response. Cost Center master data does not contain the actual and planned amounts needed to calculate utilization.

3. Choose **Search for a cost posting or planning data product to add as a second source**. Submit.
<br>![Choosing to search for an additional source](images/03_01b_0010.png)

4. Review **Financial Planning Entry Item** (`sap.s4com:dataProduct:FinancialPlanningEntryItem:v1`). The expected version is 1.3.0. This source provides planned data by cost center, fiscal year, and GL account.

> **Note:** The agent finds no actual cost posting source. Planned data supports a planned amount result, but cannot supply a utilization percentage on its own.

✓ **Checkpoint** — You should see: Joule offering planned budget amounts as a supported alternative. You have not yet approved a utilization calculation.

> **Discuss:** Would a planned amount answer the original question? Only partly. The next choice deliberately changes the result you agree to build.

### Approve the planned amount aggregation

**Goal:** Approve the supported result and its planning scope.

5. Choose **Add Financial Planning Entry Item — expose planned budget amounts per cost center**. Submit.

6. Choose **Yes — restructure as an aggregation cube with planned amounts**. Submit.

> **What changes:** The output shifts from descriptive master data (a dimension) to grouped planned amounts (a cube). Joule joins planning data using Cost Center and Controlling Area and sums `AmountInCompanyCodeCurrency`.

7. When asked about fiscal-year scope, choose **Total planned budget across all periods** (220,000 in the example). Submit.
<br>![Choosing all-period planning scope](images/03_01c_0010.png)

> **What this means:**
> - Totals combine all available planning periods and categories, not a single fiscal year.
> - The grouping keeps the cost center context, the validity information, and `CompanyCodeCurrency`. Multiple validity periods or currencies can produce multiple rows for a cost center.
> - Keep the currency with the total. Do not combine different currencies without an explicit conversion rule.
>
> The 100,000 + 120,000 = 220,000 example is simulated test data, not a business result.

8. Wait for regeneration and policy updates. Before you advance, check that Joule reports no unresolved error. If it does, see [Troubleshooting](#troubleshooting).

✓ **Checkpoint** — You should see: the approved extension containing planned amounts with currency, with India and blocking filters retained.

---

## Exercise 9 — Inspect the Enriched Definition

**Goal:** Check the regenerated graph columns and the policy summary.

1. Reselect the artifact after regeneration — the viewer may still show the old dimension.

2. Find **FinancialPlanningEntryItem** alongside **CostCenter** and **CostCenterText** in the transformation graph.

3. Locate these output columns:
   - `CompanyCodeCurrency`
   - `TotalPlannedAmountInCompanyCodeCurrency`
   - Record count fields

4. Confirm that **Country** and both **validity dates** remain in the output.
<br>![Enriched output with Financial Planning Entry Item added](images/03_02b_0010.png)

5. Read the current policy summary. After enrichment the policy fields should be: **Cost Center**, **Controlling Area**, and **Company Code**.

✓ **Checkpoint** — You should see: the final transformation graph, output columns, and policy summary all reflecting the added planning source. The demo output is named `Active Cost Centers with Planned Budget` with transformation `ActiveCostCentersBudgetCube`.

---

## Exercise 10 — Preview, Approve, and Explain Your Result

**Goal:** Finish the extension with a reviewed definition.

1. Choose **Yes, show me a preview**. Read the label that marks the data as simulated test data — this is mock data, not live customer data. The demo shows five sample rows.
<br>![SIMULATED/TEST preview rows for India cost centers with planned budget](images/03_03_0010.png)

   Only part of the wide table may be visible. Inspect the output column list for the planned amount and the currency. Do not infer hidden values.

2. Verify the following before approving:

   - [ ] Cost Center and Financial Planning Entry Item are the sources
   - [ ] India filter and all blocking filters are retained; both validity dates remain exposed
   - [ ] Planned amount and currency are present with the approved all-period scope
   - [ ] Policy fields and descriptions match the enriched definition
   - [ ] The preview is clearly identified as simulated test data

   > If the metadata still promises automatic "valid today" filtering or utilization percentages, request a correction before approving.

3. Choose **Approve — data product is ready**. Submit and wait for Joule's completion summary.

> **Do not click Deploy.** Deployment is not demonstrated in this session.

✓ **Checkpoint** — You should see: the generated definition approved and available for inspection. Stop here.

### Explain what you built

*"I created a definition for non-blocked India cost centers with planned amounts in company code currency. Consumers apply date validity. The totals span all planning periods; they are not utilization percentages. I inspected the definition and the mock preview."*

Keep your solution identifier and follow the session owner's retention or cleanup instructions.

---

## Troubleshooting

Find your latest successful checkpoint. Read the current Joule question before you enter another prompt or start a duplicate build. An unresolved generation error is not a passed checkpoint.

| If you see... | What to do |
|---|---|
| Access or creation fails | Ask a workshop assistant to confirm the assigned URL, account, and permissions. |
| A source is missing or changed | Check the identifier and fields with the assistant. Do not substitute an unrelated source. |
| Joule is waiting | Scroll to the latest question. Choose the answer and select **Submit Answer**. |
| A tooling or generation error | Wait for explicit recovery. Ask for help if it repeats or stops. Do not run manual setup commands. |
| A different choice or question than in this guide | Match the business meaning. Ask for help when the source, filters, grouping, or policy would change. |
| The viewer shows old output | Reselect the artifact after regeneration and confirm the latest properties. |
| Amounts are not visible in the preview | Inspect the output column list and the transformation. The sample table may be partially visible. |
| You are behind the group | Tell the assistant your last checkpoint. Finish what you can; the extension is optional. |

If the sources, policy fields, or totals are unclear, keep the review open and ask the assistant before you approve.

---

## Summary

You have completed the full workshop. You built and extended a data product that:

- Filters active, non-blocked cost centers for India
- Exposes validity dates for consumer-side date filtering
- Includes planned budget amounts from a second source, totalled across all planning periods
- Applies a reviewed authorization policy (Cost Center, Controlling Area, Company Code)

**Your result in one sentence:** *"I created a definition for non-blocked India cost centers with planned amounts in company code currency. Consumers apply date validity. The totals span all planning periods and are not utilization percentages."*

**Closing questions to think about:**
- Which active condition is applied by the product, and which one by the consumer?
- What extra source would utilization need beyond planned amounts?
- What does one aggregated row represent, and which periods does it cover?
- What would you still validate on live data before operational use?

> **Next steps:** Deployment and live-data testing are the next stage of the roadmap. Keep your solution identifier and follow the session owner's instructions for retention or cleanup.

---

## Reference

### Prompt used in this exercise

| Step | Prompt |
|---|---|
| Exercise 8 — budget request | `I would like to see budget utilization percentages.` |

### Choices to remember

Search for another source → Financial Planning Entry Item → planned amount aggregation → all periods → inspect the regenerated policy → mock preview → approval.

### Find your generated work

| Artifact | Purpose |
|---|---|
| `intent.md` and requirements | Business purpose, consumers, fields, and scope. |
| `specification/specification.md` | The build checklist. |
| `ActiveCostCenters.dpd` | Generated data product definition. |
| `transformation.cds` | Projection, filters, joins, and aggregation. |
| `asset.yaml` and `solution.yaml` | Asset and solution descriptors, including source references. |

**Key terms:** PRD means Product Requirements Document. AMS refers to the generated authorization policy configuration. A *dimension* describes cost centers; this extension aggregates planned amounts. File names can vary with the generated identity.
