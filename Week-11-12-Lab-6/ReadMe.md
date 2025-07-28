# Association Rule Mining with Apriori and FP-Growth with Online Retail UIC data

## Purpose of the Lab

The goal of this lab was to explore **association rule mining** techniques using the **Online Retail dataset**. We aimed to uncover frequently co-purchased items and meaningful product relationships to support business insights, such as product bundling, inventory optimization, and personalized recommendations.

Two popular algorithms were applied:

- **Apriori**
- **FP-Growth**

These were used to extract **frequent itemsets** and **association rules** based on defined minimum support and confidence thresholds.

## Dataset Overview

- Source: UCI Online Retail dataset
- Scope: Transactions from a UK-based online store between 2010–2011
- Key fields: `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country`

## Key Insights

- **FP-Growth outperformed Apriori** in terms of speed and scalability, especially when the minimum support threshold was low (e.g., 0.001).
- Top rules showed **strong complementary purchases**, such as:
  - “POPPY'S PLAYHOUSE BEDROOM” → “POPPY'S PLAYHOUSE LIVINGROOM”
  - “HERB MARKER ROSEMARY” ↔ “HERB MARKER THYME”
- High **lift values** (e.g., > 50) indicated **very strong associations** between certain products.
- Products in the same **series or collection** (e.g., Scandinavian Christmas decorations) appeared frequently in rules with high confidence and support.

---

## Techniques Used

- **Data Preprocessing**:
  - Removed canceled invoices
  - Dropped missing customer IDs
  - Created basket format using `groupby` and one-hot encoding
- **Association Rule Mining**:
  - Used `mlxtend`'s `apriori` and `fpgrowth` functions
  - Generated rules with `confidence`, `support`, and `lift` metrics
- **Visualization**:
  - Plotted support vs confidence and confidence vs lift
  - Adjusted points slightly to avoid overplotting

## Challenges and Decisions

- The **dataset was highly skewed**, with a few items appearing extremely frequently. This required careful selection of `min_support`:
  - Too low → Too many rules, memory/compute problems
  - Too high → Missed meaningful associations
- **Apriori caused kernel crashes** at very low support thresholds (e.g., 0.001) due to its candidate generation strategy.
- To improve separation in scatter plots, a **small offset (±0.003)** was added to confidence values for better visualization.

## Conclusion

Both Apriori and FP-Growth revealed actionable patterns in consumer behavior. However, **FP-Growth is preferred** for large transactional datasets due to its efficiency. Association rule mining can help retailers:
- Recommend related products
- Design product bundles
- Optimize shelf placement or marketing campaigns

