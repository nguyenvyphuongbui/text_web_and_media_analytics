# text_web_and_media_analytics
The methodology you will use for Assignment 2 includes the following tasks:
• Task 1 – Design a BM25-based IR model (BM25) that ranks documents in each data collection using the corresponding topic (query) for all 50 data collections.
• Task 2 – Design a Jelinek-Mercer based Language Model (JM_LM) that ranks documents in each data collection using the corresponding topic (query) for all 50 data collections. • Task 3 – Based on the knowledge you gained from this unit, design a pseudo-relevance model (My_PRM) to rank documents in each data collection using the corresponding topic (query) for all 50 data collections.
• Task 4 – Use Python to implement three models: BM25, JM_LM and My_PRM, and test them on the given 50 data collections for the corresponding 50 queries (topics).
• Task 5 – Use three effectiveness measures to evaluate the three models.
• Task 6 – Recommend a model based on significance test and your analysis.

Data Collection
It is a subset of RCV1 data collection. It is only for IFN647 students who will be supervised by Prof. Yuefeng Li. Please do not release this data collection to others.
Data_Collection.zip file – It includes 50 Datasets (folders “Data_C101” to “Data_C150”) for 50 queries R101 to R150. “the50Queries.txt” file – It contains definitions for 50 queries (numbered from R101 to R150) for the 50 data collections, where each <top> element (<top>...</top>) defines a query (topic), including query number (<num>), title (<title>), description (<desc>) and narrative (<narr>).
“EvaluationBenchmark.zip” file – It includes relevance judgements (where file “dataset101.txt” is the benchmark for data collection “Data_C101”, etc.) for all documents used in the 50 data collections (datasets), where "1" in the third column of each .txt file indicates that the document (the second column) is relevant to the corresponding query (the first column); and “0” means the document is non-relevant.

Assignment Specification

Task 1: Design a BM25-based IR model (BM25) that ranks documents in each data collection using the corresponding topic (query) for all 50 data collections. 
Inputs: 50 long queries (topics) in the50Queries.txt and the corresponding 50 data collections (Data_C101, Data_C102, ..., Data_C150).
Output: 50 ranked document files (e.g., for Query R107, the output file name is “BM25_R107Ranking.dat”) for all 50 data collections and save them in the folder “RankingOutputs”.
For each long query (topic) Q, you need to use the following equation to calculate a score for each document D in the corresponding data collection (dataset): where Q is the title of the long query, k1 = 1.2, k2=500, b = 0.75, K = k1*((1-b) + b*dl /avdl), dl is document D’s length and avdl is the average length of a document in the dataset, the base of the log function is 10. Note that BM25 values can be negative, and you may need to update the above equation to produce non-negative values but keep the resulting documents in the same rank order.
Formally describe your design for BM25 in an algorithm to rank documents in each data collection using corresponding query (topic) for all 50 data collections. When you use the BM25 score to rank the documents of each data collection, you also need to answer what the query feature function and document feature function are.

Task 2: Design a Jelinek-Mercer based Language Model (JM_LM) that ranks documents in each data collection using the corresponding topic (query) for all 50 data collections.
Inputs: 50 long queries (topics) in the50Queries.txt and the corresponding 50 data collections (Data_C101, Data_C102, ..., Data_C150).
Output: 50 ranked document files (e.g., for Query R107, the output file name is “JM_LM_R107Ranking.dat”) for all 50 data collections and save them in the folder “RankingOutputs”.
For each long query (topic) Rx, you need to use the following equation to calculate a conditional probability for each document D in the corresponding data collection (dataset): where fqid is the number of times query word qi occurs in document D, |D| is the number of word occurrences in D, is the number of times query word qi occurs in the data collection Data_Cx, |Data_Cx| is the total number of word occurrences in data collection Data_Cx, and parameter λ = 0.4.
Formally describe your design for JM_LM in an algorithm to rank documents in each data collection using corresponding query (topic) for all 50 data collections. When you use the probabilities to rank the documents of each data collection, you also need to answer what the query feature function and document feature function are.

Task 3. Based on the knowledge you gained from this unit, design a pseudo-relevance model (My_PRM) to rank documents in each data collection using the corresponding topic (query) for all 50 data collections.
Inputs: 50 long queries (topics) in the50Queries.txt and the corresponding 50 data collections (Data_C101, Data_C102, ..., Data_C150). 
Output: 50 ranked document files (e.g., for Query R107, the output file name is “My_PRM_R107Ranking.dat”) for all 50 data collections and save them in the folder “RankingOutputs”.
Formally describe your design for My_PRM in an algorithm to rank documents in each data collection using corresponding query (topic) for all 50 data collections. Your approach should be generic that means it is feasible to be used for other topics (queries). You also need to discuss the differences between My_PRM and the other two models (BM25 and JM_LM).

Task 4. Use Python to implement three models: BM25, JM_LM and My_PRM, and test them on the given 50 data collections for the corresponding 50 queries (topics).
Design Python programs to implement these three models. You can use a .py file (or a .ipynb file) for each model. For each long query, your python programs will produce ranked results and save them into .dat files. For example, for query R107, you can save the ranked results of three models into “BM25_R107Ranking.dat”, “JM_LM_R107Ranking.dat”, and “My_PRM_R107Ranking.dat”, respectively by using the following format, where the first column is the document id (the itemid in the corresponding XML document) and the second column is the document score (or probability).

Describe the Python package or module (or any open-source software) you used; and the data structures used to represent a single document and a set of documents for each model (you can use different data structures for different models).
You also need to test the three models on the given 50 data collections for the 50 queries (topics) by printing out the top 15 documents for each data collection (in descending order). The output will also be put in the appendix of your final report.

Task 5. Use three effectiveness measures to evaluate the three models.
In this task, you need to use the relevance judgments (EvaluationBenchmark.zip) to compare with the ranking outputs in the folder of “RankingOutputs” for the selected effectiveness metric for the three models.
You need to use the following three different effectiveness measures to evaluate the document ranking results you saved in the folder “RankingOutputs”.
(1) Average precision (and MAP),
(2) Precision@10 (and their average), and
(3) Discounted cumulative gain at rank position 10 (p = 10), DCG10 (and their average)
where reli = 1 if the document at position i is relevant; otherwise, it is zero.
Evaluation results can be summarized in tables or graphs. 

Task 6. Recommend a model based on significance test and your analysis.
You need to conduct a significance test to compare models. You can choose a t-test to perform a significance test on the evaluation results (e.g., in Tables 1, 2 and 3). You can compare models between BM25 and JM_LM, BM25 and My_PRM and JM_LM and My_PRM. Based on t-test results (p-value and t-statistic), you can recommend a model (You want the proposed "My_RPM" to be the best because it is your own model). You can perform the t-test using a single effectiveness measure or multiple measures. Generally, using more effectiveness measures provides stronger evidence against the null hypothesis.
Note that if the t-test is unsatisfactory, you can use the evaluation results to refine My_PRM mode. For example, you can adjust parameter settings or update your design and implementation.
