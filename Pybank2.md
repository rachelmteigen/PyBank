

```python
import pandas as pd
import numpy as np

```


```python
budget1 = "Resources/budget_data_1.csv"
```


```python
df = pd.read_csv(budget1)
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Oct-12</td>
      <td>1154293</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nov-12</td>
      <td>885773</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dec-12</td>
      <td>-448704</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jan-13</td>
      <td>563679</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Feb-13</td>
      <td>555394</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Mar-13</td>
      <td>631974</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Apr-13</td>
      <td>957395</td>
    </tr>
    <tr>
      <th>7</th>
      <td>May-13</td>
      <td>1104047</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Jun-13</td>
      <td>693464</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Jul-13</td>
      <td>454932</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Aug-13</td>
      <td>727272</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Sep-13</td>
      <td>125016</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Oct-13</td>
      <td>339251</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Nov-13</td>
      <td>78523</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Dec-13</td>
      <td>977084</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Jan-14</td>
      <td>1158718</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Feb-14</td>
      <td>332681</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Mar-14</td>
      <td>-341227</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Apr-14</td>
      <td>173826</td>
    </tr>
    <tr>
      <th>19</th>
      <td>May-14</td>
      <td>742611</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Jun-14</td>
      <td>1189806</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Jul-14</td>
      <td>607363</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Aug-14</td>
      <td>-1172384</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Sep-14</td>
      <td>587993</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Oct-14</td>
      <td>295198</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Nov-14</td>
      <td>-300390</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Dec-14</td>
      <td>468995</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Jan-15</td>
      <td>698452</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Feb-15</td>
      <td>967828</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Mar-15</td>
      <td>-454873</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Apr-15</td>
      <td>375723</td>
    </tr>
    <tr>
      <th>31</th>
      <td>May-15</td>
      <td>1140526</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Jun-15</td>
      <td>83836</td>
    </tr>
    <tr>
      <th>33</th>
      <td>Jul-15</td>
      <td>413189</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Aug-15</td>
      <td>551363</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Sep-15</td>
      <td>1195111</td>
    </tr>
    <tr>
      <th>36</th>
      <td>Oct-15</td>
      <td>657081</td>
    </tr>
    <tr>
      <th>37</th>
      <td>Nov-15</td>
      <td>66659</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Dec-15</td>
      <td>803301</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Jan-16</td>
      <td>-953301</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Feb-16</td>
      <td>883934</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns
```




    Index(['Date', 'Revenue'], dtype='object')




```python
#The total number of months included in the dataset
months = df["Date"].count()
months

```




    41




```python
#The total amount of revenue gained over the entire period
total_revenue = df["Revenue"].sum()
total_revenue
```




    18971412




```python
#The average change in revenue between months over the entire period
average_revenue = df["Revenue"].mean()
print(average_revenue)
```

    462717.3658536585



```python
#The greatest decrease in revenue (date and amount) over the entire period
#max_revenue = df.Revenue.diff().max()
max_revenue = df["Revenue"].max()
max_revenue
```




    1195111




```python
date = df.loc[df["Revenue"] == max_revenue, "Date"]
max_date = date.iloc[0]
max_date
```




    'Sep-15'




```python
#The greatest increase in revenue (date and amount) over the entire per
min_revenue = df["Revenue"].min()
min_revenue
```




    -1172384




```python
min_date = df.loc[df["Revenue"] == min_revenue, "Date"]
min_date_loc = date.iloc[0]
min_date_loc
#min_date
```




    'Sep-15'




```python
print(f" Total Months: {months}\n Total Revenue: {total_revenue}\n Average Revenue Change: {average_revenue}\n Greatest Increase in Revenue: {max_date} {max_revenue}\n Greatest Decrease in Revenue: {min_date_loc} {min_revenue}")
```

     Total Months: 41
     Total Revenue: 18971412
     Average Revenue Change: 462717.3658536585
     Greatest Increase in Revenue: Sep-15 1195111
     Greatest Decrease in Revenue: Sep-15 -1172384



```python

```
