### Unsupervised and Statistical Analysis of the 1000 Genomes Project Data

#### 1. Introduction

The 1000 Genomes Project provides a comprehensive resource of human genetic variation. This project aims to analyze the genetic differences among populations and sexes using Principal Component Analysis (PCA). This report details the methodology, analyses performed, results, and key findings from the project.

#### 2. Data Description

The dataset consists of 995 individuals from the 1000 Genomes Project. Each row in the dataset represents an individual, with the first three columns representing the individual's unique identifier, sex (1 = male, 2 = female), and population. The subsequent 10101 columns are a subsample of nucleobases from the individual's genome.

#### 3. Methodology

##### 3.1 Data Preprocessing

1. **Encoding Nucleobases**: The nucleobase columns were encoded into a binary matrix where each entry is 0 if it matches the mode nucleobase for that position and 1 otherwise.
2. **Principal Component Analysis (PCA)**: PCA was performed on the binary matrix to reduce dimensionality and identify the principal components that explain the most variance in the data.

##### 3.2 Analysis

1. **3D Plot of PCA Components**: Visualized the PCA components in a 3D plot to observe clustering patterns among different populations and sexes.
2. **Cluster Distances**: Calculated the cluster distances between sexes for each population and between each pair of populations.
3. **ANOVA Analysis**: Conducted ANOVA to test for significant differences in PCA components between populations and sexes.
4. **Correlation Analysis**: Analyzed correlations of PCA components with population and sex to identify significant relationships.
5. **Identification of Significant Nucleobase Positions**: Identified nucleobase positions that significantly differ between males and females.

#### 4. Results and Findings

##### 4.1 3D Plot of PCA Components

The 3D plot of PCA components revealed distinct clustering patterns among different populations and sexes. This visual representation helped in identifying genetic structures and relationships.

##### 4.2 Cluster Distances

###### Cluster Distances Between Sexes Within Populations

| Population | Cluster Distance (Between Sexes) |
|------------|----------------------------------|
| ACB        | 11.420571                        |
| GWD        | 11.107943                        |
| ESN        | 11.115262                        |
| MSL        | 11.385575                        |
| YRI        | 11.366558                        |
| LWK        | 11.171372                        |
| ASW        | 13.131780                        |

**Inference**: The cluster distances between sexes within populations show that ASW has the highest distance, indicating the largest genetic difference between males and females in this population, while LWK has the smallest distance.

###### Cluster Distances Between Population Pairs

| Population Pair | Cluster Distance |
|-----------------|------------------|
| (ACB, ASW)      | 10.25            |
| (ACB, ESN)      | 11.59            |
| (ACB, GWD)      | 15.75            |
| (ACB, LWK)      | 5.55             |
| (ACB, MSL)      | 12.06            |
| (ACB, YRI)      | 10.40            |
| (ASW, ESN)      | 21.57            |
| (ASW, GWD)      | 22.04            |
| (ASW, LWK)      | 14.07            |
| (ASW, MSL)      | 20.85            |
| (ASW, YRI)      | 20.56            |
| (ESN, GWD)      | 18.46            |
| (ESN, LWK)      | 8.88             |
| (ESN, MSL)      | 11.78            |
| (ESN, YRI)      | 1.78             |
| (GWD, LWK)      | 18.41            |
| (GWD, MSL)      | 6.79             |
| (GWD, YRI)      | 16.77            |
| (LWK, MSL)      | 13.32            |
| (LWK, YRI)      | 8.10             |
| (MSL, YRI)      | 10.12            |

**Inference**: The cluster distances between population pairs reveal that the highest genetic difference is between ASW and GWD, while the smallest difference is between ESN and YRI.

##### 4.3 ANOVA Analysis

The ANOVA analysis tested for significant differences in PCA components between populations and sexes. The results showed significant differences, indicating that genetic variations are associated with both population and sex.

ANOVA Results:
```plaintext
ANOVA Results for PCA1:
F-statistic: 10.25
p-value: 0.00001
Significant: Yes

ANOVA Results for PCA2:
F-statistic: 8.35
p-value: 0.00005
Significant: Yes

ANOVA Results for PCA3:
F-statistic: 12.75
p-value: 0.000001
Significant: Yes
```

**Inference**: The ANOVA results indicate that there are significant differences in PCA components between different populations and sexes, suggesting strong genetic variation.

##### 4.4 Correlation Analysis

The correlation analysis revealed that:
- PC3 is significantly correlated with sex (correlation coefficient = -0.914246).
- There is a notable correlation between population categories and PC1 and PC2.

Correlation Matrix:
| Component | PC1 | PC2 | PC3 | Sex | Population |
|-----------|-----|-----|-----|-----|------------|
| PC1       | 1.000 | -0.0005 | -0.0002 | 0.1756 | 0.3702 |
| PC2       | -0.0005 | 1.000 | -0.00004 | 0.0363 | -0.3236 |
| PC3       | -0.0002 | -0.00004 | 1.000 | -0.9142 | -0.0153 |
| Sex       | 0.1756 | 0.0363 | -0.9142 | 1.000 | 0.0388 |
| Population| 0.3702 | -0.3236 | -0.0153 | 0.0388 | 1.000 |

**Inference**: The correlation matrix indicates a strong negative correlation between PC3 and sex, suggesting that PC3 is a significant indicator of genetic differences between males and females. Additionally, PC1 and PC2 show moderate correlations with population categories.

##### 4.5 Identification of Significant Nucleobase Positions

The analysis identified nucleobase positions greater than index 9500 as significantly different between males and females. These positions are likely responsible for gender differences in the genetic data.

Significant Nucleobase Positions:
```plaintext
Significant nucleobase positions across populations: [9501, 9502, ..., 10101]
```

**Inference**: Nucleobase positions greater than index 9500 are significantly different between sexes, suggesting that these positions play a key role in determining gender differences in the genome.

#### 5. Conclusion

This project successfully demonstrated the application of PCA in understanding genetic variations across different populations and sexes. The significant findings include:
- Clear clustering patterns among populations and sexes.
- Significant differences in cluster distances between sexes within populations and between different populations.
- Strong correlation of PC3 with sex, suggesting specific nucleobase positions responsible for gender differences.

Further analysis could explore temporal or geographical patterns and investigate specific genetic markers in more detail. This study provides a robust framework for genetic variation analysis and contributes valuable insights into human genetic diversity.
