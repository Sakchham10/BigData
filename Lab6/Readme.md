Market Basket Analysis Summary
This project analyzes the Online Retail dataset to uncover product purchasing patterns using the Apriori and FP-Growth algorithms.

Purpose
The objective was to clean a real-world transactional dataset, mine for frequent itemsets and association rules, and compare the performance of Apriori and FP-Growth.

Key Insights
Top Products: Items like "WHITE HANGING HEART T-LIGHT HOLDER" and various "JUMBO BAG" products were the most frequent purchases, making them key items for the business.

Significant Association Rule: A strong, non-random relationship was found between teacups:
Rule: {GREEN REGENCY TEACUP AND SAUCER} -> {ROSES REGENCY TEACUP AND SAUCER}
This rule's high lift value (~23.5) indicates that customers who buy the green teacup are extremely likely to buy the rose one as well. This is a valuable insight for bundling or recommendations.

Algorithm Performance: A direct comparison showed a clear winner.

Algorithm

Performance

Rationale

Apriori

Slower

Relies on a costly "candidate generation" step that requires multiple scans of the dataset.

FP-Growth

Significantly Faster

Uses a compact FP-Tree data structure, requiring only two scans and avoiding candidate generation.

Conclusion: FP-Growth was over 10 times faster, confirming its superior efficiency for large datasets.

Challenges and Decisions
Data Cleaning: The raw dataset was noisy. Cancelled orders and rows with missing data were removed to ensure the analysis was based on valid purchases.

Setting Support Threshold: Choosing the right min_support was crucial. A value of 2% was selected after experimentation to yield meaningful results without excessive computation time.