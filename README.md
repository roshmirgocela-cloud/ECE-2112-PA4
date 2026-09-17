# 💻🔗 ECE-2112-PA4 ⚙️📊
# EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION
# Made by: Roshmir Janylin C. Gocela | 2ECE-B

The content of this repository contains the Programming Assignment 4 for our course "ECE 2112: Advanced Computer Programming and Algorithms" this S.Y. 2026-2027. This project covers three numerical python problems pertaining to Module 4 - Data Wrangling and Data Visualiztion.

---
## 🔑 OBJECTIVES:
The main objectives of this laboratory activity are to:
1. filter tabular data using several categorical and numerical conditions;
2. construct focused DataFrames by selecting relevant features;
3. summarize the relationship between categorical features and a numerical variable; and
4. communicate a data comparison using clear and correctly labeled plots.
---

# 📌PROBLEMS PYTHON DATA ANALYSIS (PANDAS):
### 📍 A. VISAYAS COMMUNICATION DATAFRAME

Create a DataFrame named VisComm containing students whose Hometown is Visayas and whose Track is Communication. Retain only these columns, in the stated order: Name, Gender, Math, Electronics, Average. Both filtering conditions must be applied to the source dataset before the columns are selected, while displaying the resulting DataFrame and its number of rows. 

#### The following functions and methods were used in this problem:
| Command | Function | Description |
| ---  | --- |  --- |
| pd.read_excel()  | df = pd.read_excel('board2.xlsx') |  Reads an Excel file and loads its data into a Pandas DataFrame. |
| df['col'] = | df['Average'] = (df.Math + df.Electronics + ...)/4 |  Creates a new column or assigns computed values to an existing column. |
| df['col'] == 'value'  | (df['Hometown'] == 'Visayas') |  Evaluates a relational equality condition element-wise to generate a boolean Series mask. |
| [['col1', 'col2']]  | [['Name', 'Gender', 'Math', 'Electronics', 'Average']] |  Selects and reorders a specific list of columns from a DataFrame. |
| display()  | display(VisComm) |  Renders a DataFrame in an interactive, formatted tabular view inside the notebook. |
| len()  | len(VisComm) |  Returns the total number of rows present in the DataFrame. |

#### The displayed code resulted in: 
```
df = pd.read_excel('board2.xlsx')
df ['Average'] = (df.Math + df.Electronics + df.GEAS + df.Communication)/4

display (df)

VisComm = df[(df['Hometown'] == 'Visayas') & 
             (df['Track'] == 'Communication')
             ][['Name', 'Gender', 'Math', 'Electronics', 'Average']]

display (VisComm)

print ("Number of rows:", len (VisComm))
```

### 📍B. VISAYAS FEMALE DATAFRAME

Create a second DataFrame named VisFemale containing students whose Hometown is Visayas and whose Gender is Female. Retain only: Name, Track, GEAS, Electronics, Average. Display VisFemale. Then display only the rows of VisFemale whose Average is at least 60. Do not overwrite VisFemale when performing this second filter.

#### The following functions and methods were used in this problem:

| Command | Function | Description |
| ---  | --- |  --- |
| df['col'] == 'value'  | (df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female') |  Generates a boolean mask matching records that meet both location and gender criteria.|
| df[...]  | df[(...) & (...)][['Name', 'Track', ...]] |  Extracts specific records and retains only the requested column subset. |
| df['col'] >= value  | VisFemale['Average'] >= 60 |  Evaluates a relational comparison to identify numeric values greater than or equal to a threshold. |
| df[df['col'] >= value]  | VisFemale[VisFemale['Average'] >= 60] |  Selects matching rows dynamically for display without modifying the original DataFrame.|


#### The displayed code resulted in:
```
VisFemale = df[(df['Hometown']=='Visayas') & (df['Gender'] == 'Female')][['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
display (VisFemale)

print ("\nFemale Students in Visayas whose average in GEAS and Electronics is atleast 60")
display (VisFemale[VisFemale['Average']>=60])
```
### 📍C. CATEGORY-AVERAGE VISUALIZATION

Examine how the recorded Average differs across the three categorical features: Track, Gender, and Hometown. Compute the mean of Average for every category using Pandas and display the three summary tables. Afterward, create one figure containing three bar charts: mean Average by Track, by Gender, and by Hometown. Below the figure, write three concise statements identifying the category with the highest sample mean for each feature.

#### The following functions and methods were used in this problem:

| Command | Function | Description |
| ---  | --- |  --- |
| df.groupby()  | df.groupby('Track') |  Groups DataFrame rows by unique values of a categorical column. |
| ['col'].mean()  | ['Average'].mean() |  Computes the arithmetic average of a numeric column for each grouped category. |
| .reset_index()  | .reset_index() |  Converts the grouped index back into standard DataFrame columns. |
| plt.subplots()  | fig, axes = plt.subplots(1, 3, figsize=(18, 5), sharey=True) |  Initializes a multi-panel figure grid with specified dimensions and aligned y-axes.   |
| fig.suptitle()  | fig.suptitle('Mean of Board Exam Average...', fontsize=16, ...) |  Sets a centered super-title across the entire visualization figure.   |
| axes[i].set_xlabel()  | axes[0].set_xlabel('Track') |  Assigns an axis label to the horizontal(x) of a subplot |
| axes[i].set_ylabel()  | axes[0].set_ylabel('Mean Average Score') |  Assigns an axis label to the vertical (y) axis of a subplot.   |
| axes[i].set_ylim()  | axes[0].set_ylim(0, 100) |  Fixes the numerical boundaries of the y-axis to maintain consistent scaling.   |
| plt.tight_layout()  | plt.tight_layout() |  Automatically adjusts subplot padding and spacing to prevent overlapping elements.   |
| plt.show()  | plt.show() |  Renders the complete figure display.   |
| Series.idxmax()  | mean_track['Average'].idxmax() |  Identifies the row index holding the maximum numerical value in a Series.   |
| df.loc[row, col]  | highest_track = mean_track.loc[..., 'Track'] |  Retrieves the specific category label associated with the identified peak index.   |

#### The displayed code resulted in:
```
mean_track = df.groupby('Track')['Average'].mean().reset_index()
mean_gender = df.groupby('Gender')['Average'].mean().reset_index()
mean_hometown = df.groupby('Hometown')['Average'].mean().reset_index()

print("\nMean Average by Track")
display(mean_track)

print("\nMean Average by Gender")
display(mean_gender)

print("\nMean Average by Hometown")
display(mean_hometown)

display(pd.concat([Mean_Track, Mean_Gender, Mean_Hometown], keys=['Track', 'Gender', 'Hometown' ]))

fig, axes = plt.subplots(1, 3, figsize=(18, 5), sharey=True)
fig.suptitle('Mean of Board Exam Average across the three Categorical Features', fontsize=16, fontweight='bold')

axes[0].bar(mean_track['Track'], mean_track['Average'], color='#8dd3b9')
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Mean Average Score')
axes[0].set_ylim(0, 100)

axes[1].bar(mean_gender['Gender'], mean_gender['Average'], color='#ffffb3')
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Gender')
axes[1].set_ylabel('Mean Average Score')

axes[2].bar(mean_hometown['Hometown'], mean_hometown['Average'], color='#b4aee0')
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown')
axes[2].set_ylabel('Mean Average Score')

plt.tight_layout()
plt.show()

highest_track = mean_track.loc[mean_track['Average'].idxmax(), 'Track']
highest_gender = mean_gender.loc[mean_gender['Average'].idxmax(), 'Gender']
highest_hometown = mean_hometown.loc[mean_hometown['Average'].idxmax(), 'Hometown']

print("The Category with the Highest Sample Mean:")
print(" 1. The Track feature has the highest sample mean is in the category", MT, "with an average of", T)
print(" 2. The Gender feature has the highest sample mean is in the category", MG, "with an average of", G)
print(" 3. The Hometown feature has the highest sample mean is in the category", MH, "with an average of", H)

```

---
 
## ❇️ README File Version History
* September 16, 2026 - Upload .ipynb file
* September 17, 2026 - Update .ipynb file
* September 17, 2026 - Upload README file
* September 17, 2026 - Upload .xlsx file

---
Thank you for reading! To run and verify the solutions, open ECE2112_PA4_GOCELA.ipynb in Jupyter Notebook, JupyterLab, or Google colab, and execute all cells.

