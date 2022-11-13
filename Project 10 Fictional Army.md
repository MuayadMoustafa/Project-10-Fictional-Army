# Fictional Army - Filtering and Sorting

### Introduction:

This exercise was inspired by this [page](http://chrisalbon.com/python/)

Special thanks to: https://github.com/chrisalbon for sharing the dataset and materials.

### Step 1. Import the necessary libraries


```python
import pandas as pd
```

### Step 2. This is the data given as a dictionary


```python
# Create an example dataframe about a fictional army
raw_data = {'regiment': ['Nighthawks', 'Nighthawks', 'Nighthawks', 'Nighthawks', 'Dragoons', 'Dragoons', 'Dragoons', 'Dragoons', 'Scouts', 'Scouts', 'Scouts', 'Scouts'],
            'company': ['1st', '1st', '2nd', '2nd', '1st', '1st', '2nd', '2nd','1st', '1st', '2nd', '2nd'],
            'deaths': [523, 52, 25, 616, 43, 234, 523, 62, 62, 73, 37, 35],
            'battles': [5, 42, 2, 2, 4, 7, 8, 3, 4, 7, 8, 9],
            'size': [1045, 957, 1099, 1400, 1592, 1006, 987, 849, 973, 1005, 1099, 1523],
            'veterans': [1, 5, 62, 26, 73, 37, 949, 48, 48, 435, 63, 345],
            'readiness': [1, 2, 3, 3, 2, 1, 2, 3, 2, 1, 2, 3],
            'armored': [1, 0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 1],
            'deserters': [4, 24, 31, 2, 3, 4, 24, 31, 2, 3, 2, 3],
            'origin': ['Arizona', 'California', 'Texas', 'Florida', 'Maine', 'Iowa', 'Alaska', 'Washington', 'Oregon', 'Wyoming', 'Louisana', 'Georgia']}
```

### Step 3. Create a dataframe and assign it to a variable called army. 

#### Don't forget to include the columns names in the order presented in the dictionary ('regiment', 'company', 'deaths'...) so that the column index order is consistent with the solutions. If omitted, pandas will order the columns alphabetically.


```python
ar = pd.DataFrame(raw_data,columns=['regiment', 'company', 'deaths', 'battles', 'size', 'veterans', 'readiness', 'armored', 'deserters', 'origin'])
ar
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>523</td>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>Arizona</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>52</td>
      <td>42</td>
      <td>957</td>
      <td>5</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
      <td>California</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>25</td>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
      <td>Texas</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>616</td>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>Florida</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>43</td>
      <td>4</td>
      <td>1592</td>
      <td>73</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>Maine</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>234</td>
      <td>7</td>
      <td>1006</td>
      <td>37</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>Iowa</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>523</td>
      <td>8</td>
      <td>987</td>
      <td>949</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
      <td>Alaska</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>62</td>
      <td>3</td>
      <td>849</td>
      <td>48</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
      <td>Washington</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>62</td>
      <td>4</td>
      <td>973</td>
      <td>48</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>Oregon</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>73</td>
      <td>7</td>
      <td>1005</td>
      <td>435</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Wyoming</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>37</td>
      <td>8</td>
      <td>1099</td>
      <td>63</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>Louisana</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>35</td>
      <td>9</td>
      <td>1523</td>
      <td>345</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Georgia</td>
    </tr>
  </tbody>
</table>
</div>




```python
ar.describe(include="all")
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>12</td>
      <td>12</td>
      <td>12.000000</td>
      <td>12.000000</td>
      <td>12.000000</td>
      <td>12.000000</td>
      <td>12.000000</td>
      <td>12.000000</td>
      <td>12.000000</td>
      <td>12</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>3</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Arizona</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>4</td>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>190.416667</td>
      <td>8.416667</td>
      <td>1127.916667</td>
      <td>174.333333</td>
      <td>2.083333</td>
      <td>0.583333</td>
      <td>11.083333</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>227.027615</td>
      <td>10.849871</td>
      <td>240.241719</td>
      <td>280.254214</td>
      <td>0.792961</td>
      <td>0.514929</td>
      <td>12.324833</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>25.000000</td>
      <td>2.000000</td>
      <td>849.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>41.500000</td>
      <td>3.750000</td>
      <td>983.500000</td>
      <td>34.250000</td>
      <td>1.750000</td>
      <td>0.000000</td>
      <td>2.750000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>62.000000</td>
      <td>6.000000</td>
      <td>1025.500000</td>
      <td>55.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>3.500000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>306.250000</td>
      <td>8.000000</td>
      <td>1174.250000</td>
      <td>141.000000</td>
      <td>3.000000</td>
      <td>1.000000</td>
      <td>24.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>616.000000</td>
      <td>42.000000</td>
      <td>1592.000000</td>
      <td>949.000000</td>
      <td>3.000000</td>
      <td>1.000000</td>
      <td>31.000000</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



### Step 4. Set the 'origin' colum as the index of the dataframe


```python
ar = ar.set_index("origin")
ar
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
    </tr>
    <tr>
      <th>origin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Arizona</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>523</td>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>California</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>52</td>
      <td>42</td>
      <td>957</td>
      <td>5</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>25</td>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>616</td>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>43</td>
      <td>4</td>
      <td>1592</td>
      <td>73</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Iowa</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>234</td>
      <td>7</td>
      <td>1006</td>
      <td>37</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>Alaska</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>523</td>
      <td>8</td>
      <td>987</td>
      <td>949</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
    </tr>
    <tr>
      <th>Washington</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>62</td>
      <td>3</td>
      <td>849</td>
      <td>48</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Oregon</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>62</td>
      <td>4</td>
      <td>973</td>
      <td>48</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Wyoming</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>73</td>
      <td>7</td>
      <td>1005</td>
      <td>435</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Louisana</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>37</td>
      <td>8</td>
      <td>1099</td>
      <td>63</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Georgia</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>35</td>
      <td>9</td>
      <td>1523</td>
      <td>345</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



### Step 5. Print only the column veterans


```python
ar["veterans"]
```




    0       1
    1       5
    2      62
    3      26
    4      73
    5      37
    6     949
    7      48
    8      48
    9     435
    10     63
    11    345
    Name: veterans, dtype: int64



### Step 6. Print the columns 'veterans' and 'deaths'


```python
ar[['veterans' , 'deaths']]
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
      <th>veterans</th>
      <th>deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>523</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>52</td>
    </tr>
    <tr>
      <th>2</th>
      <td>62</td>
      <td>25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>26</td>
      <td>616</td>
    </tr>
    <tr>
      <th>4</th>
      <td>73</td>
      <td>43</td>
    </tr>
    <tr>
      <th>5</th>
      <td>37</td>
      <td>234</td>
    </tr>
    <tr>
      <th>6</th>
      <td>949</td>
      <td>523</td>
    </tr>
    <tr>
      <th>7</th>
      <td>48</td>
      <td>62</td>
    </tr>
    <tr>
      <th>8</th>
      <td>48</td>
      <td>62</td>
    </tr>
    <tr>
      <th>9</th>
      <td>435</td>
      <td>73</td>
    </tr>
    <tr>
      <th>10</th>
      <td>63</td>
      <td>37</td>
    </tr>
    <tr>
      <th>11</th>
      <td>345</td>
      <td>35</td>
    </tr>
  </tbody>
</table>
</div>



### Step 7. Print the name of all the columns.


```python
ar.columns
```




    Index(['regiment', 'company', 'deaths', 'battles', 'size', 'veterans',
           'readiness', 'armored', 'deserters', 'origin'],
          dtype='object')



### Step 8. Select the 'deaths', 'size' and 'deserters' columns from Maine and Alaska


```python
ar.loc[["Maine", "Alaska"], ["deaths", "size", "deserters"]]
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
      <th>deaths</th>
      <th>size</th>
      <th>deserters</th>
    </tr>
    <tr>
      <th>origin</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Maine</th>
      <td>43</td>
      <td>1592</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Alaska</th>
      <td>523</td>
      <td>987</td>
      <td>24</td>
    </tr>
  </tbody>
</table>
</div>



### Step 9. Select the rows 3 to 7 and the columns 3 to 6


```python
ar.iloc[3:7 , 3:6] 
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
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>1592</td>
      <td>73</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>1006</td>
      <td>37</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>987</td>
      <td>949</td>
    </tr>
  </tbody>
</table>
</div>



### Step 10. Select every row after the fourth row and all columns


```python
ar.loc[3:]
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>616</td>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>Florida</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>43</td>
      <td>4</td>
      <td>1592</td>
      <td>73</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>Maine</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>234</td>
      <td>7</td>
      <td>1006</td>
      <td>37</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>Iowa</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>523</td>
      <td>8</td>
      <td>987</td>
      <td>949</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
      <td>Alaska</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>62</td>
      <td>3</td>
      <td>849</td>
      <td>48</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
      <td>Washington</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>62</td>
      <td>4</td>
      <td>973</td>
      <td>48</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>Oregon</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>73</td>
      <td>7</td>
      <td>1005</td>
      <td>435</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Wyoming</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>37</td>
      <td>8</td>
      <td>1099</td>
      <td>63</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>Louisana</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>35</td>
      <td>9</td>
      <td>1523</td>
      <td>345</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Georgia</td>
    </tr>
  </tbody>
</table>
</div>



### Step 11. Select every row up to the 4th row and all columns


```python
ar.loc[0:3]
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>523</td>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>Arizona</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>52</td>
      <td>42</td>
      <td>957</td>
      <td>5</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
      <td>California</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>25</td>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
      <td>Texas</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>616</td>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>Florida</td>
    </tr>
  </tbody>
</table>
</div>



### Step 12. Select the 3rd column up to the 7th column


```python
ar.iloc[: , 3:7] 
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
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>42</td>
      <td>957</td>
      <td>5</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>1592</td>
      <td>73</td>
      <td>2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7</td>
      <td>1006</td>
      <td>37</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8</td>
      <td>987</td>
      <td>949</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>849</td>
      <td>48</td>
      <td>3</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4</td>
      <td>973</td>
      <td>48</td>
      <td>2</td>
    </tr>
    <tr>
      <th>9</th>
      <td>7</td>
      <td>1005</td>
      <td>435</td>
      <td>1</td>
    </tr>
    <tr>
      <th>10</th>
      <td>8</td>
      <td>1099</td>
      <td>63</td>
      <td>2</td>
    </tr>
    <tr>
      <th>11</th>
      <td>9</td>
      <td>1523</td>
      <td>345</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



### Step 13. Select rows where df.deaths is greater than 50


```python
ar["deaths"]>50
```




    0      True
    1      True
    2     False
    3      True
    4     False
    5      True
    6      True
    7      True
    8      True
    9      True
    10    False
    11    False
    Name: deaths, dtype: bool



### Step 14. Select rows where df.deaths is greater than 500 or less than 50


```python
ar[(ar.deaths<50) | (ar.deaths>500)]
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>523</td>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>Arizona</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>25</td>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
      <td>Texas</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>616</td>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>Florida</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dragoons</td>
      <td>1st</td>
      <td>43</td>
      <td>4</td>
      <td>1592</td>
      <td>73</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>Maine</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Dragoons</td>
      <td>2nd</td>
      <td>523</td>
      <td>8</td>
      <td>987</td>
      <td>949</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
      <td>Alaska</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>37</td>
      <td>8</td>
      <td>1099</td>
      <td>63</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>Louisana</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>35</td>
      <td>9</td>
      <td>1523</td>
      <td>345</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Georgia</td>
    </tr>
  </tbody>
</table>
</div>



### Step 15. Select all the regiments not named "Dragoons"


```python
ar[(ar['regiment'] != 'Dragoons')]
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
      <th>origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>523</td>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>Arizona</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>52</td>
      <td>42</td>
      <td>957</td>
      <td>5</td>
      <td>2</td>
      <td>0</td>
      <td>24</td>
      <td>California</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>25</td>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
      <td>Texas</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>616</td>
      <td>2</td>
      <td>1400</td>
      <td>26</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>Florida</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>62</td>
      <td>4</td>
      <td>973</td>
      <td>48</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>Oregon</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Scouts</td>
      <td>1st</td>
      <td>73</td>
      <td>7</td>
      <td>1005</td>
      <td>435</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Wyoming</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>37</td>
      <td>8</td>
      <td>1099</td>
      <td>63</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>Louisana</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Scouts</td>
      <td>2nd</td>
      <td>35</td>
      <td>9</td>
      <td>1523</td>
      <td>345</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Georgia</td>
    </tr>
  </tbody>
</table>
</div>



### Step 16. Select the rows called Texas and Arizona


```python
ar.loc[["Texas","Arizona"]]
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
      <th>regiment</th>
      <th>company</th>
      <th>deaths</th>
      <th>battles</th>
      <th>size</th>
      <th>veterans</th>
      <th>readiness</th>
      <th>armored</th>
      <th>deserters</th>
    </tr>
    <tr>
      <th>origin</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Texas</th>
      <td>Nighthawks</td>
      <td>2nd</td>
      <td>25</td>
      <td>2</td>
      <td>1099</td>
      <td>62</td>
      <td>3</td>
      <td>1</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Arizona</th>
      <td>Nighthawks</td>
      <td>1st</td>
      <td>523</td>
      <td>5</td>
      <td>1045</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>



### Step 17. Select the third cell in the row named Arizona


```python
ar.loc[['Arizona'], ['deaths']]
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
      <th>deaths</th>
    </tr>
    <tr>
      <th>origin</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Arizona</th>
      <td>523</td>
    </tr>
  </tbody>
</table>
</div>



### Step 18. Select the third cell down in the column named deaths


```python
ar.loc['Texas', 'deaths']
```




    25


