# ECE-2112-PA4 💻
# EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION
# Made by: Roshmir Janylin C. Gocela | 2ECE-B

The content of this repository contains the Programming Assignment 4 for our course "ECE 2112: Advanced Computer Programming and Algorithms" this S.Y. 2026-2027. This project covers three numerical python problems pertaining to Module 3 - Pandas.

## 📌OBJECTIVES:
The main objectives of this laboratory activity are to:
1. load a CSV dataset into a Pandas DataFrame;
2. select rows and columns using positional and label-based indexing;
3. filter records using conditions on a DataFrame column; and
4. extract a well-defined subset of data without changing the source data.
## 

## ⚙️PROBLEMS: PYTHON DATA ANALYSIS (PANDAS)
### A. POSITIONAL AND LABEL-BASED SLICING 

Download the Data set cars.cvs, then display the shape and complete list of column names of cars. Using positional slicing, create cars 6 to 10 containing rows 6 through 10 of the dataset, where the first data row is row 1. From cars 6 to 10, display only the columns Model, mpg, cyl, hp, and gear, in that order.
### Code

### picture

| Left Aligned | Centered | Right Aligned |
| :---         | :---:    |          ---: |
| Text         | Text     |          Text |

```diff
+ This line will be green
- This line will be red
```
#### The following functions and methods were used in this problem:
```diff
+ this line will be green * `pd.read_csv()` - reads a comma-separated values (CSV) file into a Pandas DataFrame.
* `DataFrame.shape` - returns a tuple representing the dimensionality (rows, columns) of the DataFrame.
* `DataFrame.columns` - retrieves the column labels of the DataFrame.
* `DataFrame.iloc[]` - purely integer-location based indexing for selection by position.
* `DataFrame.loc[]` - purely label-based indexing for selection by label or boolean condition.
```
    * This method is Required for Checks & Verification: 
    ``` The row selection in part (b) must use iloc; the column selection in part (c) must use column labels. ```
    ```
    Shape of cars: (32, 12)

    Total columns: 12 (['Model', 'mpg', 'cyl', 'disp', 'hp', 'drat', 'wt', 'qsec', 'vs', 'am', 'gear', 'carb'])

    Rows extracted in cars_6_to_10: Rows 6 to 10 (Valiant, Duster 360, Merc 240D, Merc 230, Merc 280)

   Columns displayed in Part c: Model, mpg, cyl, hp, gear
    ```

### B. MODEL LOOKUP

Use Boolean indexing on the Model column to look up and display exact records without hardcoding row numbers. For displaying the complete row for Toyota Corolla and For Pontiac Firebird, display only Model, mpg, hp, and wt.

#### The following functions and methods were used in this problem:
* `Series == value - creates a Boolean conditional mask matching target text values.
* `DataFrame.loc[condition]` - extracts complete observation rows meeting the Boolean condition.
* `DataFrame.loc[condition, columns]` - selects specific labeled columns for the matching records.

### C. MULTI-MODEL SUBSETTING

Create a DataFrame named selected_cars containing only the records for Datsun 710, Lotus Europa, and Ferrari Dino. Retain only the columns Model, mpg, cyl, hp, and gear.

#### The following functions and methods were used in this problem:
* `Series.isin(list)` - checks whether each element in the Series is contained in the specified values.
* `DataFrame.loc[condition, columns]` - filters rows satisfying the Boolean condition while projecting designated columns.
* `DataFrame.shape` - returns the tuple representing the dimensionality of the subset.

    * This method is Required for Checks & Verification: 
    ``` The final DataFrame must contain exactly three rows and five columns. ```
    ```
Exact shape of selected_cars: (3, 5)
Models included: Datsun 710, Lotus Europa, and Ferrari Dino
Variables displayed: Model, mpg, cyl, hp, gear
    ```



---
Thank you for reading! To run and verify the solutions, download cars.csv file listed, and open ECE2112_PA3_GOCELA.ipynb in Jupyter Notebook, JupyterLab, or Google colab, and execute all cells.

