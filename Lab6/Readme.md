Market Basket Analysis using Apriori and FP-Growth
This project performs market basket analysis on the Online Retail dataset from the UCI Machine Learning Repository. The goal is to uncover purchasing patterns and associations between products using frequent itemset mining algorithms.

Purpose of the Lab Work
The primary purpose of this lab was to apply, compare, and analyze two fundamental algorithms for frequent itemset mining: Apriori and FP-Growth. The objectives were to:

Process and Clean a real-world transactional dataset to make it suitable for analysis.

Explore the Data to identify key characteristics, such as the most frequently purchased items.

Mine for Frequent Itemsets to discover which groups of items are often bought together.

Generate Association Rules to find probabilistic relationships between items (e.g., "If a customer buys Item A, they are likely to buy Item B").

Compare the Performance and efficiency of the Apriori and FP-Growth algorithms on the same dataset.

Key Insights from the Analysis
The analysis provided several valuable insights into customer purchasing behavior:

1. Most Popular Items
The initial data exploration showed that a few items dominate the sales. The most frequently purchased product was the "WHITE HANGING HEART T-LIGHT HOLDER", followed by various "JUMBO BAG" products. This suggests these items are core to the business and could be central to marketing campaigns.

2. Significant Association Rules
By generating association rules with a minimum confidence of 70%, we uncovered strong purchasing patterns. A key example is:

Rule: {GREEN REGENCY TEACUP AND SAUCER} -> {ROSES REGENCY TEACUP AND SAUCER}

Support (0.03): This combination appears in about 3% of all transactions.

Confidence (~79%): If a customer buys the 'GREEN REGENCY TEACUP', there is a 79% probability they will also buy the 'ROSES REGENCY TEACUP'.

Lift (~23.5): A customer is over 23 times more likely to buy the 'ROSES REGENCY TEACUP' if they have already bought the 'GREEN REGENCY TEACUP' than if they were to buy it randomly.

This high lift value indicates a very strong, non-random association. This insight can be used for product bundling, store layout optimization, or targeted recommendations.

3. Algorithm Comparison
A direct comparison between Apriori and FP-Growth yielded clear performance differences.

Algorithm

Performance

Rationale

Apriori

Slower

Relies on a costly "candidate generation" step, requiring multiple scans of the entire dataset.

FP-Growth

Significantly Faster

Uses a compact FP-Tree data structure, avoiding candidate generation and requiring only two scans of the dataset.

For this dataset, FP-Growth was over 10 times faster than Apriori, confirming its superior efficiency for large datasets.

Challenges Faced and Decisions Made
Data Cleaning: The raw dataset was noisy. It contained over 100,000 rows with missing Description values and numerous cancelled transactions (identified by invoice numbers starting with 'C').

Decision: All rows with missing critical information and all cancelled orders were removed to ensure the analysis was based only on valid, completed purchases.

Setting the Support Threshold: Choosing the min_support value was a critical decision.

A high threshold (e.g., 10%) resulted in very few frequent itemsets, providing little insight.

A very low threshold (e.g., 0.5%) led to a combinatorial explosion of itemsets and extremely long computation times.

Decision: After experimentation, a min_support of 2% was chosen. This provided a meaningful number of frequent itemsets and association rules while keeping the analysis computationally manageable.

Data Transformation: The transactional data needed to be converted into a one-hot encoded format (a transaction-item matrix) for the algorithms to work.

Decision: The pandas library was used to groupby invoices and unstack the items into columns. This is a memory-intensive operation but was feasible for this dataset's size. For significantly larger datasets, more memory-efficient sparse matrix representations would be necessary.
