# Accessing Data within Pandas

## Introduction
In this lesson, we're going to dig into various methods for accessing data from our Pandas Series and DataFrames.

## Objectives

You will be able to:

- Use pandas methods and attributes to access information about a dataset   
- Index pandas dataframes with .loc, .iloc, and column names   
- Use a boolean mask to index pandas series and dataframes 




## Importing pandas and the data

First, let's make sure we import `pandas` as `pd`.

> In the cell below, type the code to import the pandas library with the standard alias.

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">import pandas as pd
    </code></pre>
</details>



```python
# replace this comment with the code to import the pandas library and set the standard alias
```

To show how to access data with Pandas, let's use the `wine` dataset in the scikit-learn library. Don't worry about the code below. We're essentially just making sure you have access to the `wine` dataset.

The data contained in the wine dataset are the results of a chemical analysis of wines grown in Italy. It contains the quantities of 13 wine constituents. 

> To load the dataset, import the `load_wine` function from the `sklearn.datasets` library by typing in the following code:

`from sklearn.datasets import load_wine`

> Then we we will load the dataset by calling the function and assigning it to the variable `data` by typing the following code:

`data = load_wine()`

> Finally, we will create a DataFrame from `data` by typing in the following code:

`df = pd.DataFrame(data.data, columns=data.feature_names)`


```python
# replace this comment with the code to import pandas and set the alias

# replace this comment with the code to load the data and assign it to the variable

# replace this comment with the code to create a DataFrame from the data

```


```python
import pandas as pd
from sklearn.datasets import load_wine
data = load_wine()
df = pd.DataFrame(data.data, columns=data.feature_names)
```

Great! Our data set is now stored in the variable `df`. As you know, you can look at its elements by using `df` or `print(df)`.

> In the cell below, print the DataFrame `df` to check that our code worked.

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">print(df)
    </code></pre>
</details>


```python
# replace this comment with the code to print out the DataFrame we just created
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>malic_acid</th>
      <th>ash</th>
      <th>alcalinity_of_ash</th>
      <th>magnesium</th>
      <th>total_phenols</th>
      <th>flavanoids</th>
      <th>nonflavanoid_phenols</th>
      <th>proanthocyanins</th>
      <th>color_intensity</th>
      <th>hue</th>
      <th>od280/od315_of_diluted_wines</th>
      <th>proline</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>14.23</td>
      <td>1.71</td>
      <td>2.43</td>
      <td>15.6</td>
      <td>127.0</td>
      <td>2.80</td>
      <td>3.06</td>
      <td>0.28</td>
      <td>2.29</td>
      <td>5.64</td>
      <td>1.04</td>
      <td>3.92</td>
      <td>1065.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13.20</td>
      <td>1.78</td>
      <td>2.14</td>
      <td>11.2</td>
      <td>100.0</td>
      <td>2.65</td>
      <td>2.76</td>
      <td>0.26</td>
      <td>1.28</td>
      <td>4.38</td>
      <td>1.05</td>
      <td>3.40</td>
      <td>1050.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>13.16</td>
      <td>2.36</td>
      <td>2.67</td>
      <td>18.6</td>
      <td>101.0</td>
      <td>2.80</td>
      <td>3.24</td>
      <td>0.30</td>
      <td>2.81</td>
      <td>5.68</td>
      <td>1.03</td>
      <td>3.17</td>
      <td>1185.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>14.37</td>
      <td>1.95</td>
      <td>2.50</td>
      <td>16.8</td>
      <td>113.0</td>
      <td>3.85</td>
      <td>3.49</td>
      <td>0.24</td>
      <td>2.18</td>
      <td>7.80</td>
      <td>0.86</td>
      <td>3.45</td>
      <td>1480.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>13.24</td>
      <td>2.59</td>
      <td>2.87</td>
      <td>21.0</td>
      <td>118.0</td>
      <td>2.80</td>
      <td>2.69</td>
      <td>0.39</td>
      <td>1.82</td>
      <td>4.32</td>
      <td>1.04</td>
      <td>2.93</td>
      <td>735.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>173</th>
      <td>13.71</td>
      <td>5.65</td>
      <td>2.45</td>
      <td>20.5</td>
      <td>95.0</td>
      <td>1.68</td>
      <td>0.61</td>
      <td>0.52</td>
      <td>1.06</td>
      <td>7.70</td>
      <td>0.64</td>
      <td>1.74</td>
      <td>740.0</td>
    </tr>
    <tr>
      <th>174</th>
      <td>13.40</td>
      <td>3.91</td>
      <td>2.48</td>
      <td>23.0</td>
      <td>102.0</td>
      <td>1.80</td>
      <td>0.75</td>
      <td>0.43</td>
      <td>1.41</td>
      <td>7.30</td>
      <td>0.70</td>
      <td>1.56</td>
      <td>750.0</td>
    </tr>
    <tr>
      <th>175</th>
      <td>13.27</td>
      <td>4.28</td>
      <td>2.26</td>
      <td>20.0</td>
      <td>120.0</td>
      <td>1.59</td>
      <td>0.69</td>
      <td>0.43</td>
      <td>1.35</td>
      <td>10.20</td>
      <td>0.59</td>
      <td>1.56</td>
      <td>835.0</td>
    </tr>
    <tr>
      <th>176</th>
      <td>13.17</td>
      <td>2.59</td>
      <td>2.37</td>
      <td>20.0</td>
      <td>120.0</td>
      <td>1.65</td>
      <td>0.68</td>
      <td>0.53</td>
      <td>1.46</td>
      <td>9.30</td>
      <td>0.60</td>
      <td>1.62</td>
      <td>840.0</td>
    </tr>
    <tr>
      <th>177</th>
      <td>14.13</td>
      <td>4.10</td>
      <td>2.74</td>
      <td>24.5</td>
      <td>96.0</td>
      <td>2.05</td>
      <td>0.76</td>
      <td>0.56</td>
      <td>1.35</td>
      <td>9.20</td>
      <td>0.61</td>
      <td>1.60</td>
      <td>560.0</td>
    </tr>
  </tbody>
</table>
<p>178 rows × 13 columns</p>
</div>



---
#### Expected Output
<pre><code>a pandas DataFrame with 178 rows and 13 columns and the following column names:
alcohol  malic_acid   ash  alcalinity_of_ash  magnesium  total_phenols 
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
<img src="images/df_example.png">
</details>

---


Now, what if you want to see only a few lines of the data, based on certain constraints? You'll learn how to access data in this lesson!

## Methods and attributes to access data information

It won't be a surprise that our `df` object is a Pandas DataFrame object. Let's verify this using the `type()` function: 
> In the cell below, use the `type()` function to check the data type of `df`

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">type(df)
    </code></pre>
</details>


```python
# replace this comment with the code to check the data type of `df`
```

---
#### Expected Output
<pre><code>pandas.core.frame.DataFrame
</code></pre>
---

There are some methods and attributes associated with Pandas objects (both DataFrames *and* series!) which make retrieving information from the data particularly easy. Some commonly used methods:
- `.head()`
- `.tail()`

And attributes:
- `.index`
- `.columns`
- `.dtypes`
- `.shape`

### Some methods: `.head()`, `.tail()`, and `.info()`

By using `.head()` and `.tail()`, you can select the first $n$ rows from your dataframe. The default $n$ is 5, but you can change this value inside the parentheses. For example:

> In the cell below, type the code to show the first 5 rows of `df` using the `head()` method:

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.head()
    </code></pre>
</details>


```python
# replace this comment with the code to display the first 5 rows of df
```

---
#### Expected Output
<pre><code>the first 5 lines of the DataFrame with indices 0-4
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
<img src="images/head_example.png">
</details>

---

> In the cell below, type the code to display the last three rows of `df` using the `.tail()` method adding the value `3` to override the default value of the _n-rows_ parameter:
<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.tail(3)
    </code></pre>
</details>


```python
# replace this comment with the code to display the last 3 rows of df
```

---
#### Expected Output
<pre><code>the last 3 lines of the DataFrame with indices 175-177
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
<img src="images/tail_example.png">
</details>

---


To get a concise summary of the dataframe, you can use `.info()`: 

> In the cell below, type the code to display a summary of `df` by using the `.info()` method:

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.info()
    </code></pre>
</details>


```python
# replace this comment with the code to display a summary of df
```

---
#### Expected Output
<pre><code>a summary of the DataFrame df
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
    <pre><code language="python">&lt;class 'pandas.core.frame.DataFrame'&gt;
RangeIndex: 178 entries, 0 to 177
Data columns (total 13 columns):
 #   Column                        Non-Null Count  Dtype  
---  ------                        --------------  -----  
 0   alcohol                       178 non-null    float64
 1   malic_acid                    178 non-null    float64
 2   ash                           178 non-null    float64
 3   alcalinity_of_ash             178 non-null    float64
 4   magnesium                     178 non-null    float64
 5   total_phenols                 178 non-null    float64
 6   flavanoids                    178 non-null    float64
 7   nonflavanoid_phenols          178 non-null    float64
 8   proanthocyanins               178 non-null    float64
 9   color_intensity               178 non-null    float64
 10  hue                           178 non-null    float64
 11  od280/od315_of_diluted_wines  178 non-null    float64
 12  proline                       178 non-null    float64
dtypes: float64(13)
memory usage: 18.2 KB
    </code></pre>
</details>

---

### Some attributes

Using `.index`, you can access the index or row labels of the DataFrame.

> In the cell below, type the code to display the information about the index using the `.index` attribute:

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.index
    </code></pre>
</details>


```python
# replace this comment with the code to display information about the index of df
```


---
#### Expected Output
<pre><code>RangeIndex(start=0, stop=178, step=1)
</code></pre>
---

Using `.columns`, you can access the column labels of the DataFrame.

> In the cell below, type the code to display the column information of `df` using the `.columns` attribute:

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.columns
    </code></pre>
</details>


```python
# replace this comment with the code to display information about the columns of df  
```

---
#### Expected Output
<pre><code>Index(['alcohol', 'malic_acid', 'ash', 'alcalinity_of_ash', 'magnesium',
       'total_phenols', 'flavanoids', 'nonflavanoid_phenols',
       'proanthocyanins', 'color_intensity', 'hue',
       'od280/od315_of_diluted_wines', 'proline'],
      dtype='object')
</code></pre>
---

Using `.dtypes` returns the data types of all columns in the DataFrame (compare with `.info()`!)

> In the cell below, type the code to display the data types of each column in `df` using the `.types` attribute:

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.types
    </code></pre>
</details>


```python
# replace this comment with the code to display the data types in df
```

---
#### Expected Output
<pre><code>alcohol                         float64
malic_acid                      float64
ash                             float64
alcalinity_of_ash               float64
magnesium                       float64
total_phenols                   float64
flavanoids                      float64
nonflavanoid_phenols            float64
proanthocyanins                 float64
color_intensity                 float64
hue                             float64
od280/od315_of_diluted_wines    float64
proline                         float64
dtype: object
</code></pre>
---

`.shape` returns a tuple representing the dimensionality  (in `(rows, columns)` ) of the DataFrame.

> In the cell below, type the code to display the shape of `df` using the `.shape` attribute:

<details>
    <summary>
        <b><u>Reveal Code</u></b>
    </summary>
    <pre><code language="python">df.shape
    </code></pre>
</details>


```python
# replace this comment with the code to display the shape of df
```

---
#### Expected Output
<pre><code>(178, 13)
</code></pre>
---

## Selecting DataFrame information

In the previous section, we deliberately omitted 2 very important attributes:
- `.iloc`, which is a Pandas DataFrame indexer used for integer-location based indexing / selection by position 
- `.loc`, which has two use cases:
       - Selecting by label / index
       - Selecting with a boolean / conditional lookup


### `.iloc`

You can use `.iloc` to select single rows. To select the 4th row, you can use `.iloc[3]` like:

> In the cell below, type the following code to select the 4th row of df:

`df.iloc[3]`


```python
# replace this comment with the code to select the 4th row of df
```

---
#### Expected Output
<pre><code>alcohol                           14.37
malic_acid                         1.95
ash                                2.50
alcalinity_of_ash                 16.80
magnesium                        113.00
total_phenols                      3.85
flavanoids                         3.49
nonflavanoid_phenols               0.24
proanthocyanins                    2.18
color_intensity                    7.80
hue                                0.86
od280/od315_of_diluted_wines       3.45
proline                         1480.00
Name: 3, dtype: float64
</code></pre>

---

You can use a colon to select several rows. Note that you'll use a structure `.iloc[a:b]` where the row with index `a` will be included in the selection and the row with index `b` is excluded.

> In the cell below, type the following code to select the rows of `df` with the indicies of 5-7"

`df.iloc[5:8]`


```python
# replace this comment with the code to display the rows with the indicies of 5-7
df.iloc[5:8]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>malic_acid</th>
      <th>ash</th>
      <th>alcalinity_of_ash</th>
      <th>magnesium</th>
      <th>total_phenols</th>
      <th>flavanoids</th>
      <th>nonflavanoid_phenols</th>
      <th>proanthocyanins</th>
      <th>color_intensity</th>
      <th>hue</th>
      <th>od280/od315_of_diluted_wines</th>
      <th>proline</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>14.20</td>
      <td>1.76</td>
      <td>2.45</td>
      <td>15.2</td>
      <td>112.0</td>
      <td>3.27</td>
      <td>3.39</td>
      <td>0.34</td>
      <td>1.97</td>
      <td>6.75</td>
      <td>1.05</td>
      <td>2.85</td>
      <td>1450.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>14.39</td>
      <td>1.87</td>
      <td>2.45</td>
      <td>14.6</td>
      <td>96.0</td>
      <td>2.50</td>
      <td>2.52</td>
      <td>0.30</td>
      <td>1.98</td>
      <td>5.25</td>
      <td>1.02</td>
      <td>3.58</td>
      <td>1290.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>14.06</td>
      <td>2.15</td>
      <td>2.61</td>
      <td>17.6</td>
      <td>121.0</td>
      <td>2.60</td>
      <td>2.51</td>
      <td>0.31</td>
      <td>1.25</td>
      <td>5.05</td>
      <td>1.06</td>
      <td>3.58</td>
      <td>1295.0</td>
    </tr>
  </tbody>
</table>
</div>



---
#### Expected Output
<pre><code>a section of the DataFrame df with the rows 5,6, and 7
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
    <img src="images/iloc_5-8.png">
</details>

---

Next, you can use `,` to perform *column* selections based on their index as well. The command below selects full columns 3-6:

> In the cell below, type the following code to select columns 3-6 of `df`:

`df.iloc[:, 3:7]`


```python
# replace this comment with the code to select columns 3-6 of df
df.iloc[:, 3:7]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcalinity_of_ash</th>
      <th>magnesium</th>
      <th>total_phenols</th>
      <th>flavanoids</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>15.6</td>
      <td>127.0</td>
      <td>2.80</td>
      <td>3.06</td>
    </tr>
    <tr>
      <th>1</th>
      <td>11.2</td>
      <td>100.0</td>
      <td>2.65</td>
      <td>2.76</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.6</td>
      <td>101.0</td>
      <td>2.80</td>
      <td>3.24</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.8</td>
      <td>113.0</td>
      <td>3.85</td>
      <td>3.49</td>
    </tr>
    <tr>
      <th>4</th>
      <td>21.0</td>
      <td>118.0</td>
      <td>2.80</td>
      <td>2.69</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>173</th>
      <td>20.5</td>
      <td>95.0</td>
      <td>1.68</td>
      <td>0.61</td>
    </tr>
    <tr>
      <th>174</th>
      <td>23.0</td>
      <td>102.0</td>
      <td>1.80</td>
      <td>0.75</td>
    </tr>
    <tr>
      <th>175</th>
      <td>20.0</td>
      <td>120.0</td>
      <td>1.59</td>
      <td>0.69</td>
    </tr>
    <tr>
      <th>176</th>
      <td>20.0</td>
      <td>120.0</td>
      <td>1.65</td>
      <td>0.68</td>
    </tr>
    <tr>
      <th>177</th>
      <td>24.5</td>
      <td>96.0</td>
      <td>2.05</td>
      <td>0.76</td>
    </tr>
  </tbody>
</table>
<p>178 rows × 4 columns</p>
</div>



---
#### Expected Output
<pre><code>a section of the df DataFrame with 178 rows and 4 columns
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
    <img src="images/iloc_3-7.png">
</details>

---

Last but not least, you can perform column and row selections at once:

> In the cell below, type the following code to display rows 5-9 and columns 3-8 using the `iloc` attribute:

`df.iloc[5:10]`


```python
# replace this comment with the code to display the desired portion of df
df.iloc[5:10, 3:9]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcalinity_of_ash</th>
      <th>magnesium</th>
      <th>total_phenols</th>
      <th>flavanoids</th>
      <th>nonflavanoid_phenols</th>
      <th>proanthocyanins</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>15.2</td>
      <td>112.0</td>
      <td>3.27</td>
      <td>3.39</td>
      <td>0.34</td>
      <td>1.97</td>
    </tr>
    <tr>
      <th>6</th>
      <td>14.6</td>
      <td>96.0</td>
      <td>2.50</td>
      <td>2.52</td>
      <td>0.30</td>
      <td>1.98</td>
    </tr>
    <tr>
      <th>7</th>
      <td>17.6</td>
      <td>121.0</td>
      <td>2.60</td>
      <td>2.51</td>
      <td>0.31</td>
      <td>1.25</td>
    </tr>
    <tr>
      <th>8</th>
      <td>14.0</td>
      <td>97.0</td>
      <td>2.80</td>
      <td>2.98</td>
      <td>0.29</td>
      <td>1.98</td>
    </tr>
    <tr>
      <th>9</th>
      <td>16.0</td>
      <td>98.0</td>
      <td>2.98</td>
      <td>3.15</td>
      <td>0.22</td>
      <td>1.85</td>
    </tr>
  </tbody>
</table>
</div>



---
#### Expected Output
<pre><code>a section of the df DataFrame containing rows 5-9 and columns 3-8
</code></pre>
<details>
    <summary>
        <b><u>Click to Expand Complete Output</u></b>
    </summary>
    <img src="images/iloc_rows_columns.png">
</details>

---

### `.loc`

 #### a) `.loc` label-based indexing

You can `.loc` to select columns based on their (row index and) column name. Examples:

> In the cell below, type the following code to display the information in the `magnesium` column:

`df.loc[:, 'magnesium']`


```python
# replace this comment with the code to display the desired portion of df
df.loc[:, 'magnesium']
```


```python
# -EXPECTED OUTPUT-
# a portion of df which includes 178 rows of the magnesium column
```

An alternative method here is simply calling `df['magnesium']`!

> In the cell below, type the following code to select rows 7-16 of just the `magnesium` column:

`df.loc[7:16, 'magnesium']`


```python
df.loc[7:16, 'magnesium']
```

#### b) boolean indexing using `.loc`

Sometimes you'd like to select certain rows in your dataset based on the value for a certain variable. Imagine you'd like to create a new DataFrame that only contains the wines with an alcohol percentage below 12. This can be done as follows:


```python
df.loc[df['alcohol'] < 12]
```

You can verify that simply using `df[df['alcohol'] < 12]`, you can obtain the same result!

However, the .`loc` attribute is useful if you'd only want the color intensity for the wines with an alcohol percentage below 12. You can obtain the result as follows:


```python
df.loc[df['alcohol'] < 12, ['color_intensity']]
```

## Selectors for series

Until now we've only really discussed Pandas DataFrames. Most of these methods and selectors are also applicable to Pandas Series. See how you can convert a one-column DataFrame into a Pandas Series:


```python
# Let's save our color intensity dataframe into an object col_intensity
col_intensity = df['color_intensity']
```


```python
type(col_intensity)
```

Note how `col_intensity` is now a Pandas *Series*.

Many of the commands discussed before are readily applicable to series:


```python
col_intensity[0:3]
```


```python
# Or col_intensity.loc[col_intensity > 8]
col_intensity[col_intensity > 8] 
```

## Changing and setting values in DataFrames and series

### Changing values

Imagine that for some reason, you're not interested in the color intensity values for color intensities above 10, and simply want to set all color intensities to 10 when they are bigger than 10. You can use a selector method and then assign it a new value, just like this:


```python
df.loc[df['color_intensity'] > 10, 'color_intensity'] = 10
```

### Creating new columns

Now imagine that we want to create a new column named, "shade" which has a value, "light" when the `color_intensity` is below 7, and, "dark" when the intensity is > 7. This can be done as follows:


```python
df.loc[df['color_intensity'] > 7, 'shade'] = 'dark'
df.loc[df['color_intensity'] <= 7, 'shade'] = 'light'
```

If you now look at the output of `df.shape`, you will notice that `df` now has 14 columns. 


```python
df.shape
```

## Summary

We've introduced a range of techniques for accessing information in Pandas Series and DataFrames, selecting rows and columns, changing values, and creating new columns! Now, it's time for some practice! Let's start working on a lab where you will get a chance to practice some of these methods!
