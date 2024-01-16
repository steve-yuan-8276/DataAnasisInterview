# How to handle the missing value in data cleaning?

Due to survey, coding and input errors, there may be some invalid and missing values in the data that need to be properly handled. Common methods include estimation, casewise deletion, variable deletion and pairwise deletion.

1. Estimation: The simplest method is to replace invalid and missing values with the sample mean, median or mode of a certain variable. This method is simple but does not fully consider the existing information in the data and may have large errors. Another method is to estimate based on answers to other questions by survey respondents through correlation analysis or logical inference between variables. For example, ownership of a product may be related to household income; therefore one can estimate the likelihood of owning this product based on respondents' household income.

2. Casewise deletion involves removing samples containing missing values. Since many questionnaires may contain missing values, this approach may result in a significant reduction in effective sample size and cannot make full use of collected data. Therefore it only applies when key variables are missing or when samples with invalid or missing values account for a small proportion.

3. Variable deletion: If there are many invalid and missing values for a particular variable which is not particularly important for studying problems then it can be considered deleting that variable.This reduces the number of variables available for analysis but does not change sample size.

4. Pairwise Deletion uses special codes (usually 9, 99, 999 etc)to represent invalid andmissingvalues while retaining all variablesand samplesinthe dataset.However,in specific calculations only complete answer samplesare used so different analyses involving differentvariables will have different effective sample sizes.Thisis a conservative approach that maximizes retentionof usable information withinthe dataset


由于调查、编码和录入误差，数据中可能存在一些无效值和缺失值，需要给予适当的处理。常用的处理方法有：估算，整例删除，变量删除和成对删除。

1. 估算(estimation)。最简单的办法就是用某个变量的样本均值、中位数或众数代替无效值和缺失值。这种办法简单，但没有充分考虑数据中已有的信息，误差可能较大。另一种办法就是根据调查对象对其他问题的答案，通过变量之间的相关分析或逻辑推论进行估计。例如，某一产品的拥有情况可能与家庭收入有关，可以根据调查对象的家庭收入推算拥有这一产品的可能性。
2. 整例删除(casewise deletion)是剔除含有缺失值的样本。由于很多问卷都可能存在缺失值，这种做法的结果可能导致有效样本量大大减少，无法充分利用已经收集到的数据。因此，只适合关键变量缺失，或者含有无效值或缺失值的样本比重很小的情况。
3. 变量删除(variable deletion)。如果某一变量的无效值和缺失值很多，而且该变量对于所研究的问题不是特别重要，则可以考虑将该变量删除。这种做法减少了供分析用的变量数目，但没有改变样本量。
4. 成对删除(pairwise deletion)是用一个特殊码(通常是9、99、999等)代表无效值和缺失值，同时保留数据集中的全部变量和样本。但是，在具体计算时只采用有完整答案的样本，因而不同的分析因涉及的变量不同，其有效样本量也会有所不同。这是一种保守的处理方法，最大限度地保留了数据集中的可用信息。
