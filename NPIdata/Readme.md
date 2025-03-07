### US Doctor Database Analysis

<p style="font-size: small;">
This project analyzes the publicly available NPI (National Provider Identifier) database for US doctors, identifying active practitioners and visualizing their distribution based on medical taxonomy categories. Outputs may vary depending on the date of data upload.
</p>
---

### Dataset Sources:
- NPI Registry Data:  
`https://download.cms.gov`

---

### Tasks & Implementation:

**1. Load and Organize Monthly Data:**
```
# Load monthly doctor data into DataFrame
import pandas as pd
df = pd.read_csv('monthly_doctor_data.csv')
```

**2. Remove Inactive Doctors:**
```
# Remove doctors listed in the deactivation files
inactive_df = pd.read_csv('deactivation_data.csv')
df = df[~df['NPI'].isin(inactive_df['NPI'])]
```

**3. Count Active Doctors by Practice:**
```
# Count active doctors grouped by taxonomy (practice type)
practice_counts = df['taxonomy'].value_counts()
```

**3. Visualize Doctor Practices (Pie Chart):**
```
import matplotlib.pyplot as plt

practice_counts.plot(kind='pie', autopct='%1.1f%%', figsize=(8,8))
plt.title('Distribution of Doctor Practices')
plt.ylabel('')
plt.show()
```

**4. Find Specific Doctor Records:**
```
# Example query to check for specific doctors
specific_doctors = df[
    (df['Name'].str.contains('Doctor Name')) & 
    (df['Address'].str.contains('Street Address'))
]
print(specific_doctor_records)
```

---

### Running the Project:
- Load monthly datasets and deactivation data.
- Perform data cleaning and removal of inactive doctors.
- Analyze the number of active doctors per medical practice.
- Visualize the results clearly with Pandas and Matplotlib.

---

### Tools & Libraries:
- Python, Pandas, Matplotlib

---

### License:
- For analytical and educational use only. Personal data not used or shared.

---

### References:
- CMS Public Dataset
- Pandas Documentation
- Matplotlib Documentation
