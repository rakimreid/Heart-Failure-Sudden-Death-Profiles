
<div align = "center">
     <h1> Heart Failure Patient CLustering </h1>]
     
<img src = "https://th.bing.com/th/id/R.252f5ababb3488bdf837b6fe002f86a8?rik=EeYRT83G5smimA&riu=http%3a%2f%2f2romania.com%2fSanatate%2fhealthyheart.gif&ehk=ErQwtyN1%2fdNtDpZ0ElBrNiPL%2bjDENmGhHD0aPvb2OP0%3d&risl=&pid=ImgRaw&r=0" />
</div>


<h2>Background</h2> 

The purpose of this project is to create groupings of at risk for sudden death heart failure patients. This will enable the determination those most at-risk of sudden death and, if desired, predict which group patients belong.

<h2> Part I: Exploratory Data Analysis <img src ="https://th.bing.com/th/id/OIP.j5Vj7VYXdSuB0Cho-HbMpgHaHa?pid=ImgDet&rs=1" height = 25, width = 25 />

</h2>


<h2>Data</h2> 

The data comes from UCI Irvine Machine Learning Repository: https://archive.ics.uci.edu/ml/datasets/Heart+failure+clinical+records

A detailed description of the dataset can be found in the Dataset section of the following paper:

Davide Chicco, Giuseppe Jurman: "Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone". BMC Medical Informatics and Decision Making 20, 16 (2020). [Web Link]

Attribute Information:

Thirteen (13) clinical features:

age: age of the patient (years)
anaemia: decrease of red blood cells or hemoglobin (boolean)
high blood pressure: if the patient has hypertension (boolean)
creatinine phosphokinase (CPK): level of the CPK enzyme in the blood (mcg/L)
diabetes: if the patient has diabetes (boolean)
ejection fraction: percentage of blood leaving the heart at each contraction (percentage)
platelets: platelets in the blood (kiloplatelets/mL)
sex: woman or man (binary)
serum creatinine: level of serum creatinine in the blood (mg/dL)
serum sodium: level of serum sodium in the blood (mEq/L)
smoking: if the patient smokes or not (boolean)
time: follow-up period (days)
[target] death event: if the patient deceased during the follow-up period (boolean)
For more information, please check Table 1, Table 2, and Table 3 of the following paper:

Davide Chicco, Giuseppe Jurman: "Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone". BMC Medical Informatics and Decision Making 20, 16 (2020). [Web Link]

Relevant Papers:

Original dataset version:

Tanvir Ahmad, Assia Munir, Sajjad Haider Bhatti, Muhammad Aftab, and Muhammad Ali Raza: "Survival analysis of heart failure patients: a case study". PLoS ONE 12(7), 0181001 (2017). [Web Link]

Current dataset version on the UCI ML Repository:

Davide Chicco, Giuseppe Jurman: "Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone". BMC Medical Informatics and Decision Making 20, 16 (2020). [Web Link]

Citation Request:

Davide Chicco, Giuseppe Jurman: "Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone". BMC Medical Informatics and Decision Making 20, 16 (2020). [Web Link]

We will use the following variables based on the literature: creatine phosphokinase level, ejection fraction, age and high_blood_pressure.

More information on heart failure is available at the links below:

https://pubmed.ncbi.nlm.nih.gov/10577445/ https://www.aafp.org/pubs/afp/issues/2012/0615/p1161.html


<h2> Part II: Unsupervised Learning

<img src ="https://th.bing.com/th/id/OIP.4u9QjWljrMuY5CL7nGzRkQHaFj?w=273&h=205&c=7&r=0&o=5&dpr=1.3&pid=1.7" height = 25, width = 25 />
</h2>

The models examined are: 
* Gaussian Mixture Model (GMM) w/ PCA
* K-Means w/ PCA 
* DBSCAN w/ PCA 
     
<h3>Unsupervised Model Best Results:</h3>

DBSCAN w/ PCA Results
The silhouette score of the DBSCAN solution with Euclidean: 0.4572246497012825.

Adjusted Rand Index of the DBSCAN solution with Euclidean: 0.003593655067798663.

The silhouette score of the DBSCAN solution with Chebyshev distance: 0.47315988515382557

K-Means w/ PCA Results
Adjusted Rand Index of the KMeans solution: 0.004175926402351372 The silhouette score of the KMeans solution: 0.23125622798405496

GMM w/ PCA Results
Adjusted Rand Index of the GMM solution: 0.020601096841243217 The silhouette score of the GMM solution: 0.22824263534337996
     
     
<h2> Part III: Evaluation & Future Project Ideas 
<img src ="https://th.bing.com/th/id/R.b8644db24930cf9363566896d5253aec?rik=7SL6mGoqlQ0TNQ&riu=http%3a%2f%2fmedia.istockphoto.com%2fvectors%2fsaturn-vector-id165600450%3fk%3d6%26m%3d165600450%26s%3d612x612%26w%3d0%26h%3drEvVMsd4l40ib7bcrQzr1TzjkbLgRpcYPYGpYhJ9Nxo%3d&ehk=KabbCN8zzWnhbNSUIRMIS8eS0lrYNF2gRndPFaAxmOg%3d&risl=&pid=ImgRaw&r=0" height = 25, width = 25 />

</h2> 
     
<h3> Evaluation:</h3>
The DBSCAN w/ PCA and Chebyshev distance performed best. However, Chebyshev distance is known to work well for certain. This distance measure is not known to apply for health data. Chebyshev distance is also known as chessboard distance since this metric is defined on a vector space where the distance between two vectors is the greatest of their differences along any coordinate dimension."

For example, the Chebyshev distance is sometimes used in warehouse logistics. Therefore, I chose the DBSCAN with Euclidean distance since it performed nearly as well. In addition, density is better method of interpreting clusters of disease risk compared to movement along a given space.

In the clusters, those points higher up on the plot have higher amounts and those lower on the plots have lower amounts.

BIRCH, OPTICS and spectral clustering were used to see if other clustering algorithms might be a better fit than K-Means, DBSCAN or GMM. There might be merit to pursuing spectral clustering. BIRCH clustering miscalssified one point while spectral clustering properly classified all the points.

Spectral clustering uses the connectivity between data points to form the clusters -- instead of a distance measure. This appears to work better than the other algorithms tested on a plot.     

<h3> Future Goals</h3>

* Future applications can examine whether spectral clustering or other clustering methods are more effective than the chosen model.

* Distance measures appropriate for medical data may produce better results. 
