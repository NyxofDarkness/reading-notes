# Reading

## Pandas in 10

Create a Series by passing a list of values, letting pandas create a default integer index:

``` python
In [3]: s = pd.Series([1, 3, 5, np.nan, 6, 8])

In [4]: s
Out[4]: 
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
```

Creating a DataFrame by passing a NumPy array, with a datetime index and labeled columns:

``` python
In [5]: dates = pd.date_range("20130101", periods=6)

In [6]: dates
Out[6]: 
DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

In [7]: df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))
```

Creating a DataFrame by passing a dict of objects that can be converted to series-like:

``` python
In [9]: df2 = pd.DataFrame(
   ...:     {
   ...:         "A": 1.0,
   ...:         "B": pd.Timestamp("20130102"),
   ...:         "C": pd.Series(1, index=list(range(4)), dtype="float32"),
   ...:         "D": np.array([3] * 4, dtype="int32"),
   ...:         "E": pd.Categorical(["test", "train", "test", "train"]),
   ...:         "F": "foo",
   ...:     }
   ...: )
```

DataFrame.to_numpy() gives a NumPy representation of the underlying data. Note that this can be an expensive operation when your DataFrame has columns with different data types, which comes down to a fundamental difference between pandas and NumPy: NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column. 

> DataFrame.to_numpy() does not include the index or column labels in the output.

|Commands|Definition|
|---|---|
|View Data |---|
|df.head(num) | can optionally set number of rows|
|df.tail(num) | can optionally set number of rows|
|df.index | gets indexes|
|df.columns | get column names|
|df.to_numpy() | return numpy representation (expensive for mixed types)|
|df.describe() | quick stats (count, mean, std, min, etc)|
|df.T | transpose|
|df.sort_index(axis=1, ascending=False) | sort by index|
|df.sort_values(by="B") | sort by value(column name)|
|Selection |---|
|df["A"] | Selects column “A”, same as df.A|
|df[0:3] | Selects first 3 rows|
|Selection by label|---|
|df.loc[dates[0]] | Cross section with dates label|
|df.loc[:, ["A", "B"]] | multi-axis by label|
|df.loc["20130102":"20130104", ["A", "B"]] | label slicing, inclusive|
|df.at[dates[0], "A"] | specific value|
|Selection by position |---|
|df.iloc[3] | 3rd row, all columns, transposed. Inclusive.|
|df.iloc[3:5, 0:2] | 3rd-5th row, 0-2 column. Like NumPy/Python.|
|df.iloc[[1, 2, 4], [0, 2]] | List explist row/col to include|
|df.iloc[1:3, :] | Explicit rows|
|df.iloc[:, 1:3] | Explicit col|
|df.iat[1, 1] | Explicit row/col|
|Boolean indexing |---|
|df[df["A"] > 0] | Select rows matching column criteria|
|df[df > 0] | Select all values meeting criteria|
|df[df["E"].isin(["two", "four"])] | Finds rows meeting column criteria|
|Setting |---|
|df["F"] = s1 | add a new column (where s1 is a Series)|
|df.at[dates[0], "A"] | by label|
|df.iat[0, 1] | by position|
|df.loc[:, "D"] = np.array([5] * len(df)) | with numpy array|
|df[df > 0] = - df | turn all values greater than 0 negative|
|Missing Data |---|
|df1.dropna(how="any") | drop downs w/ NaN
|df1.fillna(value=5) | fill missing data
|Operations |---|
|df.mean() | mean per column|
|df.mean(1) | mean per row|
|df.apply(np.cumsum) | apply function to all columns|
|df.apply(lambda x: x.max() - x.min()) | apply function to get 1 val per column|
|s.value_counts() | histogram for series|
|s.str.lower() | lowercase for series |
|Merge |---|
|pd.concat(list of rows) | Concat pandas objects|
|pd.merge(left, right, on="key") | sql style join (left and right are df’s)|
|Grouping| df.groupby("A").sum()|
|Time series |--|
|ts.resample("10Min").sum() | Sampling|
|ts_utc.tz_convert("US/Eastern") | Time zone conversion|
|ts.to_period() | Convert to diff period|
|df["grade"] = df["raw_grade"].astype("category") | Convert raw to catorgoy|
|df["insert grade"].cat.categories | ["very good", "good", "very bad"] |
|df.sort_values(by="grade") | Sort|
|df.groupby("grade").size() | Group by|
|df.to_csv("foo.csv") | write to csv|
|pd.read_csv("foo.csv") | read from csv|
|df.to_excel("foo.xlsx", sheet_name="Sheet1") | write to excel|
|pd.read_excel("foo.xlsx", "Sheet1", index_col=None, na_values=["NA"]) | read from excel|

## [Pandas - Getting Started](https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html)

## [Real Python - Pandas Tutorials](https://realpython.com/learning-paths/pandas-data-science/)

## [What is Pandas YouTube Video](https://www.youtube.com/watch?v=dcqPhpY7tWk&t=391s)

## [Master Pandas](https://towardsdatascience.com/be-a-more-efficient-data-scientist-today-master-pandas-with-this-guide-ea362d27386)

[x] bookmarked!
