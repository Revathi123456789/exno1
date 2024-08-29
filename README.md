# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
# Reading the data set:
```
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("SAMPLEIDS.csv")
df
```
# Output:
<img width="608" alt="Screenshot 2024-08-29 205752" src="https://github.com/user-attachments/assets/da9dc528-ea59-47ae-967a-87d9eb00d339">

# Initializing id=column
```
id=df['M4']
id
```
# output:
<img width="307" alt="pc 2" src="https://github.com/user-attachments/assets/f447219a-c629-45f0-9049-b6c45135b436">

# sns graphs:
<img width="611" alt="pc3" src="https://github.com/user-attachments/assets/16ef0660-6182-49b0-b410-522a9a4d92c5">
<img width="610" alt="pc4" src="https://github.com/user-attachments/assets/571856dc-12f2-4f26-a53a-51be0875b218">
<img width="611" alt="pc5" src="https://github.com/user-attachments/assets/ea9b30fd-aeda-44f7-8c8e-e1a398342429">

# Quantile and IQR:
```
q1=id.quantile(0.25)
q2=id.quantile(0.5)
q3=id.quantile(0.75)
iqr=q3-q1
iqr
```
# Output:
<img width="565" alt="image" src="https://github.com/user-attachments/assets/41844b30-4a84-4c4e-967e-51ec28d5cc51">

# Declaring bounds:
```
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
lower_bound,upper_bound
```
# Output:
<img width="331" alt="image" src="https://github.com/user-attachments/assets/4d1223eb-1ab8-4a35-8789-cb2fdc68e1e8">

# Outliers:
```
outliers=[x for x in id if x<lower_bound or x>upper_bound]
print("Outliers:",outliers)
```
# Output:
<img width="596" alt="image" src="https://github.com/user-attachments/assets/7a7a1fbb-9cf5-453a-9ffc-752df84dc1bf">

# Dropna function to remove any null values:
```
id.dropna()
```
# Output:
<img width="605" alt="image" src="https://github.com/user-attachments/assets/7bc95451-02bb-41a5-b151-a683906e3c76">

# Printing all requird values:
```
print("Q1:",q1)
print("Q2:",q2)
print("Q3:",q3)
print("IQR:",iqr)
print("lower_bound:",lower_bound)
print("upper_bound:",upper_bound)
print("Outliers",outliers)
```
# Output:
<img width="539" alt="image" src="https://github.com/user-attachments/assets/a5f99d2e-eefb-445a-8448-27d6204885c9">

# Checking for any outliers at the end:
```
sns.boxplot(id)

```
# Output:
<img width="608" alt="image" src="https://github.com/user-attachments/assets/63697105-5e6a-4553-85cb-2169f00f16e5">

# Calculating Z_score:
```
import scipy.stats as stats
import pandas as pd
import numpy as np


mean = df['M4'].mean()
std_dev = df['M4'].std()

df['z_score'] = (df['M4'] - mean) / std_dev

print(df)

z = np.abs(stats.zscore(df['M4']))
z
```
# Output:
<img width="289" alt="image" src="https://github.com/user-attachments/assets/bd88aae5-a5a8-41a6-ba16-c1f072cfcf29">


# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.

