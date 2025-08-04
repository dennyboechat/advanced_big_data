Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Lab 6: Association Rule Mining with Apriori and FP-Growth

## Lab Purpose

This lab explores association rule mining techniques using the Apriori and FP-Growth algorithms on an Online Retail dataset. It involves analyzing transactional data to identify frequent itemsets and generate meaningful association rules. Seaborn is used to create visualizations that support the interpretation of these patterns. The lab demonstrates how association rule mining can uncover hidden relationships in real-world retail data and how visual tools can enhance the presentation and understanding of insights.

## Key insights and models comparison

Through this lab, one of the key insights was understanding how customers tend to buy certain products together. By applying the Apriori and FP-Growth algorithms to the Online Retail dataset, it became clear that some items, especially those related to home and kitchen decor, are frequently purchased as a group. For example, sets of storage tins or lunch bags with similar designs often appeared in the same transactions. This kind of pattern can be very useful for recommending product bundles or designing promotions around popular item combinations.

Another important takeaway was the difference in performance between the two algorithms. Apriori worked well but took more time because it generates a lot of candidate itemsets and scans the dataset multiple times. FP-Growth, on the other hand, was faster and more efficient since it uses a tree-based structure to find frequent patterns without generating all the candidates. Despite these differences, both methods produced the same frequent itemsets and association rules when using the same thresholds for support and confidence. This shows that the choice of algorithm can impact the efficiency of the analysis but not necessarily the final output.

Lastly, visualizing the results using Seaborn made the insights much easier to interpret. A barplot helped highlight the most common itemsets, while a scatter plot of confidence vs. lift showed which rules were both strong and reliable. These visuals added an extra layer of understanding by making complex data patterns more accessible. Overall, this lab showed how association rule mining can be a powerful tool for analyzing customer behavior and making informed business decisions in a retail setting.