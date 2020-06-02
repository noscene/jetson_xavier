```python
# in Eagle run ULP -> select 'mountsmd' for creating file
import pandas as pd

foorprints={ "C0603K"       : {'x':  3.0,  'y':  2.0,   'h': 0.5}, 
             "C0603"        : {'x':  3.0,  'y':  2.0,   'h': 0.5},
             "C0402K"       : {'x':  1.2,  'y':  0.7,   'h': 0.5},
             "R0402"        : {'x':  1.2,  'y':  0.7,   'h': 0.5},
             "ESP-WROOM32"  : {'x': 25.5,  'y': 18.0,   'h': 3.1} }

df = pd.read_csv('test_m104.mnt', sep="\s+", names=["PART","X","Y","R","Value","Footprint"] )
```


```python
df.head(5)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PART</th>
      <th>X</th>
      <th>Y</th>
      <th>R</th>
      <th>Value</th>
      <th>Footprint</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C1</td>
      <td>31.19</td>
      <td>19.94</td>
      <td>270</td>
      <td>470uF</td>
      <td>EIA7343</td>
    </tr>
    <tr>
      <th>1</th>
      <td>C2</td>
      <td>21.99</td>
      <td>23.11</td>
      <td>0</td>
      <td>100n</td>
      <td>C0402K</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C3</td>
      <td>29.20</td>
      <td>27.41</td>
      <td>0</td>
      <td>10uF</td>
      <td>C0603K</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C4</td>
      <td>28.05</td>
      <td>2.24</td>
      <td>0</td>
      <td>100n</td>
      <td>C0402K</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C5</td>
      <td>30.87</td>
      <td>46.37</td>
      <td>270</td>
      <td>10uF</td>
      <td>C0603K</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.groupby(['Footprint'])[['PART','Value']].count().reset_index().head(5)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Footprint</th>
      <th>PART</th>
      <th>Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0603-ARC</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2X03</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C0402K</td>
      <td>6</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C0603</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C0603K</td>
      <td>10</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


