# AB_Testing
 
The concept of AB Test is based on providing the 'controlled experiment' conditions, which we also encounter in academic studies, in order to make a healthier decision between any two strategies and examining the results. “What is the AB test in practice?” The question can be answered as experiments in which only one of several variables is changed and which variant performs better under equal conditions.

### Independent Two-Sample T-Test

As for the group averages;
1. Establish Hypotheses
2. Assumption Check
- 1. Normality Assumption --> the distributions of the relevant groups are normal. **(test with shapiro)**
![image](https://user-images.githubusercontent.com/121626776/224813646-3e28f912-e804-40ec-b886-f879e2224318.png)


- 2. Variance Homogeneity --> the distribution of variances of the two groups is similar to each other. **(test with levene)** 
<img src="https://user-images.githubusercontent.com/121626776/225084895-0d4ad724-25be-4d32-9e88-3a1e116e8280.png" width="300" >


3. Application of the Hypothesis
- 1. If assumptions are met: independent two-sample t-test (parametric test)

test_stat, pvalue = ttest_ind(df.loc[df["smoker"] == "Yes", "total_bill"],
                              df.loc[df["smoker"] == "No", "total_bill"],
                              equal_var=True)
                              
**!! If there is a normality assumption but no variance homogeneity assumption, equal_var=False should be written and the operation should be done.**                                                   

- 2. If assumptions are not provided: mannwhitneyu test (non-parametric test)

test_stat, pvalue = mannwhitneyu(df.loc[df["smoker"] == "Yes", "total_bill"],
                                 df.loc[df["smoker"] == "No", "total_bill"])

4. Interpret results based on p-value

A P-value less than 0.05 is deemed to be statistically significant, meaning the null hypothesis should be rejected in such a case.


![image](https://user-images.githubusercontent.com/121626776/224809792-b50548b2-8f2c-41fa-b041-1145e48f7227.png)


### Two Sample Ratio Test

Proportions_ztest can be used.

![image](https://user-images.githubusercontent.com/121626776/224810304-b0888f37-55a8-40c7-8032-e59cf74db6a2.png)


### ANOVA (Analysis of Variance)

It is used to compare the mean of more than two groups.

- Assumptions provided: one way anova **(f_oneway)**

- If assumptions are not provided: the kruskal algorithm

![Ekran görüntüsü 2023-03-13 222900](https://user-images.githubusercontent.com/121626776/224814379-f6fd49be-b082-4ee2-a157-efe24d8ab86a.png)

![image](https://user-images.githubusercontent.com/121626776/224814639-bce63911-e894-40ed-a9f8-66b2bd222ec2.png)

