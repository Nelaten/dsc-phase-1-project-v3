## Final Project Submission

Please fill out:
* Student name: 
* Student pace: self paced / part time / full time
* Scheduled project review date/time: 
* Instructor name: 
* Blog post URL:


## * Nelson Muia Mutuku
## * Part time
## * Tuesday, 29th April, 2025
## * Mwikali


```python
# Your code here - remember to use markdown cells for comments as well!
```

## OVERVIEW

##### The company that I work is expanding in to new industries in order to diversify its portfolio. 

##### Specifically, they are interested in purchasing and operating airplanes for commercial and private enterprises, but do not know anything about the potential risks of aircraft. 

##### You are charged with determining which aircraft are the lowest risk for the company to start this new business endeavor. 

##### You must then translate your findings into actionable insights that the head of the new aviation division can use to help decide which aircraft to purchase.

### BUSINESS UNDERSTANDING

The company is venturing into the aviation industry to diversify its portfolio, with plans to operate aircraft for both commercial and private use. However, the leadership lacks expertise in aviation risk, which poses a challenge in selecting suitable aircraft. The objective of this analysis is to identify the lowest-risk aircraft makes, enabling the new aviation division to make informed, data-driven decisions about which models to purchase. This ensures the company enters the market with a focus on safety, reliability, and long-term profitability.

Our stakeholders immediate stakeholders are our directors and generally also our future clients in the new industry.

Through this project, relying on our data analysis we seek to answer the following questions

1. Which is are the safest makes of aircrafts for the industry we want to venture in and particularly for the niches we have earmarked, the Commercial and Private flights markets?
2. Which aircrafts are the most safe among the most common aircraft makes relied upon in the Private/Personal flights markets?
3. Which aircraft makes are the most safe among the most common aircraft makes relied upon in the Commercial/Business flights markets? 

## DATA UNDERSTANDING


```python
# Running of the Pandas library which will be used for Data manipulation and analysis

import pandas as pd
```


```python
# Reading the csv file into a pandas data frame

aviation_data = pd.read_csv('data\Aviation_Data.csv', encoding = 'latin1', low_memory = False)
aviation_data
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
      <th>Event.Id</th>
      <th>Investigation.Type</th>
      <th>Accident.Number</th>
      <th>Event.Date</th>
      <th>Location</th>
      <th>Country</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Airport.Code</th>
      <th>Airport.Name</th>
      <th>...</th>
      <th>Purpose.of.flight</th>
      <th>Air.carrier</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
      <th>Weather.Condition</th>
      <th>Broad.phase.of.flight</th>
      <th>Report.Status</th>
      <th>Publication.Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20001218X45444</td>
      <td>Accident</td>
      <td>SEA87LA080</td>
      <td>1948-10-24</td>
      <td>MOOSE CREEK, ID</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Cruise</td>
      <td>Probable Cause</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20001218X45447</td>
      <td>Accident</td>
      <td>LAX94LA336</td>
      <td>1962-07-19</td>
      <td>BRIDGEPORT, CA</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Unknown</td>
      <td>Probable Cause</td>
      <td>19-09-1996</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20061025X01555</td>
      <td>Accident</td>
      <td>NYC07LA005</td>
      <td>1974-08-30</td>
      <td>Saltville, VA</td>
      <td>United States</td>
      <td>36.922223</td>
      <td>-81.878056</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>IMC</td>
      <td>Cruise</td>
      <td>Probable Cause</td>
      <td>26-02-2007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20001218X45448</td>
      <td>Accident</td>
      <td>LAX96LA321</td>
      <td>1977-06-19</td>
      <td>EUREKA, CA</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Cruise</td>
      <td>Probable Cause</td>
      <td>12-09-2000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>20041105X01764</td>
      <td>Accident</td>
      <td>CHI79FA064</td>
      <td>1979-08-02</td>
      <td>Canton, OH</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>Approach</td>
      <td>Probable Cause</td>
      <td>16-04-1980</td>
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
      <th>90343</th>
      <td>20221227106491</td>
      <td>Accident</td>
      <td>ERA23LA093</td>
      <td>2022-12-26</td>
      <td>Annapolis, MD</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>29-12-2022</td>
    </tr>
    <tr>
      <th>90344</th>
      <td>20221227106494</td>
      <td>Accident</td>
      <td>ERA23LA095</td>
      <td>2022-12-26</td>
      <td>Hampton, NH</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90345</th>
      <td>20221227106497</td>
      <td>Accident</td>
      <td>WPR23LA075</td>
      <td>2022-12-26</td>
      <td>Payson, AZ</td>
      <td>United States</td>
      <td>341525N</td>
      <td>1112021W</td>
      <td>PAN</td>
      <td>PAYSON</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90346</th>
      <td>20221227106498</td>
      <td>Accident</td>
      <td>WPR23LA076</td>
      <td>2022-12-26</td>
      <td>Morgan, UT</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>MC CESSNA 210N LLC</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90347</th>
      <td>20221230106513</td>
      <td>Accident</td>
      <td>ERA23LA097</td>
      <td>2022-12-29</td>
      <td>Athens, GA</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30-12-2022</td>
    </tr>
  </tbody>
</table>
<p>90348 rows × 31 columns</p>
</div>




```python
# Here we inspect the dataframe and check the data-type within each column and also get a glance of the missing values within each column

aviation_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 90348 entries, 0 to 90347
    Data columns (total 31 columns):
     #   Column                  Non-Null Count  Dtype  
    ---  ------                  --------------  -----  
     0   Event.Id                88889 non-null  object 
     1   Investigation.Type      90348 non-null  object 
     2   Accident.Number         88889 non-null  object 
     3   Event.Date              88889 non-null  object 
     4   Location                88837 non-null  object 
     5   Country                 88663 non-null  object 
     6   Latitude                34382 non-null  object 
     7   Longitude               34373 non-null  object 
     8   Airport.Code            50249 non-null  object 
     9   Airport.Name            52790 non-null  object 
     10  Injury.Severity         87889 non-null  object 
     11  Aircraft.damage         85695 non-null  object 
     12  Aircraft.Category       32287 non-null  object 
     13  Registration.Number     87572 non-null  object 
     14  Make                    88826 non-null  object 
     15  Model                   88797 non-null  object 
     16  Amateur.Built           88787 non-null  object 
     17  Number.of.Engines       82805 non-null  float64
     18  Engine.Type             81812 non-null  object 
     19  FAR.Description         32023 non-null  object 
     20  Schedule                12582 non-null  object 
     21  Purpose.of.flight       82697 non-null  object 
     22  Air.carrier             16648 non-null  object 
     23  Total.Fatal.Injuries    77488 non-null  float64
     24  Total.Serious.Injuries  76379 non-null  float64
     25  Total.Minor.Injuries    76956 non-null  float64
     26  Total.Uninjured         82977 non-null  float64
     27  Weather.Condition       84397 non-null  object 
     28  Broad.phase.of.flight   61724 non-null  object 
     29  Report.Status           82508 non-null  object 
     30  Publication.Date        73659 non-null  object 
    dtypes: float64(5), object(26)
    memory usage: 21.4+ MB
    


```python
#Here we are trying to obtain the summary statistics of the dataset and understand the distribution and central tendency of the data.

aviation_data.describe()
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
      <th>Number.of.Engines</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>82805.000000</td>
      <td>77488.000000</td>
      <td>76379.000000</td>
      <td>76956.000000</td>
      <td>82977.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1.146585</td>
      <td>0.647855</td>
      <td>0.279881</td>
      <td>0.357061</td>
      <td>5.325440</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.446510</td>
      <td>5.485960</td>
      <td>1.544084</td>
      <td>2.235625</td>
      <td>27.913634</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>8.000000</td>
      <td>349.000000</td>
      <td>161.000000</td>
      <td>380.000000</td>
      <td>699.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Here we are we use a code that returns the dataframe in the same format but replaces 
# the missing values with "False" and where there are values present with the boolean "True".

aviation_data.isnull()
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
      <th>Event.Id</th>
      <th>Investigation.Type</th>
      <th>Accident.Number</th>
      <th>Event.Date</th>
      <th>Location</th>
      <th>Country</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Airport.Code</th>
      <th>Airport.Name</th>
      <th>...</th>
      <th>Purpose.of.flight</th>
      <th>Air.carrier</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
      <th>Weather.Condition</th>
      <th>Broad.phase.of.flight</th>
      <th>Report.Status</th>
      <th>Publication.Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
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
      <th>90343</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>90344</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>90345</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>90346</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>90347</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>...</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>90348 rows × 31 columns</p>
</div>




```python
aviation_data
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
      <th>Event.Id</th>
      <th>Investigation.Type</th>
      <th>Accident.Number</th>
      <th>Event.Date</th>
      <th>Location</th>
      <th>Country</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Airport.Code</th>
      <th>Airport.Name</th>
      <th>...</th>
      <th>Purpose.of.flight</th>
      <th>Air.carrier</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
      <th>Weather.Condition</th>
      <th>Broad.phase.of.flight</th>
      <th>Report.Status</th>
      <th>Publication.Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20001218X45444</td>
      <td>Accident</td>
      <td>SEA87LA080</td>
      <td>1948-10-24</td>
      <td>MOOSE CREEK, ID</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Cruise</td>
      <td>Probable Cause</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20001218X45447</td>
      <td>Accident</td>
      <td>LAX94LA336</td>
      <td>1962-07-19</td>
      <td>BRIDGEPORT, CA</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Unknown</td>
      <td>Probable Cause</td>
      <td>19-09-1996</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20061025X01555</td>
      <td>Accident</td>
      <td>NYC07LA005</td>
      <td>1974-08-30</td>
      <td>Saltville, VA</td>
      <td>United States</td>
      <td>36.922223</td>
      <td>-81.878056</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>IMC</td>
      <td>Cruise</td>
      <td>Probable Cause</td>
      <td>26-02-2007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20001218X45448</td>
      <td>Accident</td>
      <td>LAX96LA321</td>
      <td>1977-06-19</td>
      <td>EUREKA, CA</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Cruise</td>
      <td>Probable Cause</td>
      <td>12-09-2000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>20041105X01764</td>
      <td>Accident</td>
      <td>CHI79FA064</td>
      <td>1979-08-02</td>
      <td>Canton, OH</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>Approach</td>
      <td>Probable Cause</td>
      <td>16-04-1980</td>
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
      <th>90343</th>
      <td>20221227106491</td>
      <td>Accident</td>
      <td>ERA23LA093</td>
      <td>2022-12-26</td>
      <td>Annapolis, MD</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>29-12-2022</td>
    </tr>
    <tr>
      <th>90344</th>
      <td>20221227106494</td>
      <td>Accident</td>
      <td>ERA23LA095</td>
      <td>2022-12-26</td>
      <td>Hampton, NH</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90345</th>
      <td>20221227106497</td>
      <td>Accident</td>
      <td>WPR23LA075</td>
      <td>2022-12-26</td>
      <td>Payson, AZ</td>
      <td>United States</td>
      <td>341525N</td>
      <td>1112021W</td>
      <td>PAN</td>
      <td>PAYSON</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90346</th>
      <td>20221227106498</td>
      <td>Accident</td>
      <td>WPR23LA076</td>
      <td>2022-12-26</td>
      <td>Morgan, UT</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>MC CESSNA 210N LLC</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90347</th>
      <td>20221230106513</td>
      <td>Accident</td>
      <td>ERA23LA097</td>
      <td>2022-12-29</td>
      <td>Athens, GA</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Personal</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30-12-2022</td>
    </tr>
  </tbody>
</table>
<p>90348 rows × 31 columns</p>
</div>




```python
# At this state I want to see all the 31 columns in the dataset for me to determine which ones are important for my
# analysis based on my intended objective.

aviation_data.columns
```




    Index(['Event.Id', 'Investigation.Type', 'Accident.Number', 'Event.Date',
           'Location', 'Country', 'Latitude', 'Longitude', 'Airport.Code',
           'Airport.Name', 'Injury.Severity', 'Aircraft.damage',
           'Aircraft.Category', 'Registration.Number', 'Make', 'Model',
           'Amateur.Built', 'Number.of.Engines', 'Engine.Type', 'FAR.Description',
           'Schedule', 'Purpose.of.flight', 'Air.carrier', 'Total.Fatal.Injuries',
           'Total.Serious.Injuries', 'Total.Minor.Injuries', 'Total.Uninjured',
           'Weather.Condition', 'Broad.phase.of.flight', 'Report.Status',
           'Publication.Date'],
          dtype='object')




```python
# Clean the aviation data by dropping the columns with more than 20,000 missing values

clean_aviation_data = aviation_data.loc[:, aviation_data.isna().sum() <= 20000]
clean_aviation_data 

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
      <th>Event.Id</th>
      <th>Investigation.Type</th>
      <th>Accident.Number</th>
      <th>Event.Date</th>
      <th>Location</th>
      <th>Country</th>
      <th>Injury.Severity</th>
      <th>Aircraft.damage</th>
      <th>Registration.Number</th>
      <th>Make</th>
      <th>...</th>
      <th>Number.of.Engines</th>
      <th>Engine.Type</th>
      <th>Purpose.of.flight</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
      <th>Weather.Condition</th>
      <th>Report.Status</th>
      <th>Publication.Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20001218X45444</td>
      <td>Accident</td>
      <td>SEA87LA080</td>
      <td>1948-10-24</td>
      <td>MOOSE CREEK, ID</td>
      <td>United States</td>
      <td>Fatal(2)</td>
      <td>Destroyed</td>
      <td>NC6404</td>
      <td>Stinson</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Probable Cause</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20001218X45447</td>
      <td>Accident</td>
      <td>LAX94LA336</td>
      <td>1962-07-19</td>
      <td>BRIDGEPORT, CA</td>
      <td>United States</td>
      <td>Fatal(4)</td>
      <td>Destroyed</td>
      <td>N5069P</td>
      <td>Piper</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Probable Cause</td>
      <td>19-09-1996</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20061025X01555</td>
      <td>Accident</td>
      <td>NYC07LA005</td>
      <td>1974-08-30</td>
      <td>Saltville, VA</td>
      <td>United States</td>
      <td>Fatal(3)</td>
      <td>Destroyed</td>
      <td>N5142R</td>
      <td>Cessna</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>IMC</td>
      <td>Probable Cause</td>
      <td>26-02-2007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20001218X45448</td>
      <td>Accident</td>
      <td>LAX96LA321</td>
      <td>1977-06-19</td>
      <td>EUREKA, CA</td>
      <td>United States</td>
      <td>Fatal(2)</td>
      <td>Destroyed</td>
      <td>N1168J</td>
      <td>Rockwell</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Probable Cause</td>
      <td>12-09-2000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>20041105X01764</td>
      <td>Accident</td>
      <td>CHI79FA064</td>
      <td>1979-08-02</td>
      <td>Canton, OH</td>
      <td>United States</td>
      <td>Fatal(1)</td>
      <td>Destroyed</td>
      <td>N15NY</td>
      <td>Cessna</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>Probable Cause</td>
      <td>16-04-1980</td>
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
      <th>90343</th>
      <td>20221227106491</td>
      <td>Accident</td>
      <td>ERA23LA093</td>
      <td>2022-12-26</td>
      <td>Annapolis, MD</td>
      <td>United States</td>
      <td>Minor</td>
      <td>NaN</td>
      <td>N1867H</td>
      <td>PIPER</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>29-12-2022</td>
    </tr>
    <tr>
      <th>90344</th>
      <td>20221227106494</td>
      <td>Accident</td>
      <td>ERA23LA095</td>
      <td>2022-12-26</td>
      <td>Hampton, NH</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>N2895Z</td>
      <td>BELLANCA</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90345</th>
      <td>20221227106497</td>
      <td>Accident</td>
      <td>WPR23LA075</td>
      <td>2022-12-26</td>
      <td>Payson, AZ</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N749PJ</td>
      <td>AMERICAN CHAMPION AIRCRAFT</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90346</th>
      <td>20221227106498</td>
      <td>Accident</td>
      <td>WPR23LA076</td>
      <td>2022-12-26</td>
      <td>Morgan, UT</td>
      <td>United States</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>N210CU</td>
      <td>CESSNA</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>90347</th>
      <td>20221230106513</td>
      <td>Accident</td>
      <td>ERA23LA097</td>
      <td>2022-12-29</td>
      <td>Athens, GA</td>
      <td>United States</td>
      <td>Minor</td>
      <td>NaN</td>
      <td>N9026P</td>
      <td>PIPER</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30-12-2022</td>
    </tr>
  </tbody>
</table>
<p>90348 rows × 22 columns</p>
</div>




```python
# Here I am inspecting the cleaned dataframe to get a glance missing values within the remaining columns

clean_aviation_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 90348 entries, 0 to 90347
    Data columns (total 22 columns):
     #   Column                  Non-Null Count  Dtype  
    ---  ------                  --------------  -----  
     0   Event.Id                88889 non-null  object 
     1   Investigation.Type      90348 non-null  object 
     2   Accident.Number         88889 non-null  object 
     3   Event.Date              88889 non-null  object 
     4   Location                88837 non-null  object 
     5   Country                 88663 non-null  object 
     6   Injury.Severity         87889 non-null  object 
     7   Aircraft.damage         85695 non-null  object 
     8   Registration.Number     87572 non-null  object 
     9   Make                    88826 non-null  object 
     10  Model                   88797 non-null  object 
     11  Amateur.Built           88787 non-null  object 
     12  Number.of.Engines       82805 non-null  float64
     13  Engine.Type             81812 non-null  object 
     14  Purpose.of.flight       82697 non-null  object 
     15  Total.Fatal.Injuries    77488 non-null  float64
     16  Total.Serious.Injuries  76379 non-null  float64
     17  Total.Minor.Injuries    76956 non-null  float64
     18  Total.Uninjured         82977 non-null  float64
     19  Weather.Condition       84397 non-null  object 
     20  Report.Status           82508 non-null  object 
     21  Publication.Date        73659 non-null  object 
    dtypes: float64(5), object(17)
    memory usage: 15.2+ MB
    


```python
#Here we are trying to obtain the summary statistics of the new dataframe after cleaning it in order 
# to understand the distribution and central tendency of the data.

clean_aviation_data.describe()
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
      <th>Number.of.Engines</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>82805.000000</td>
      <td>77488.000000</td>
      <td>76379.000000</td>
      <td>76956.000000</td>
      <td>82977.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1.146585</td>
      <td>0.647855</td>
      <td>0.279881</td>
      <td>0.357061</td>
      <td>5.325440</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.446510</td>
      <td>5.485960</td>
      <td>1.544084</td>
      <td>2.235625</td>
      <td>27.913634</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>8.000000</td>
      <td>349.000000</td>
      <td>161.000000</td>
      <td>380.000000</td>
      <td>699.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# I entered this code as I was facing a challenge trying to access the colum of 'Aircraft.damage', 
# this ensure there column exists and its the one that I am working with

if 'Aircraft.damage' in clean_aviation_data.columns:
    unique_report = clean_aviation_data['Aircraft.damage'].unique()
    print("Unique values in 'Aircraft.damage' column:", unique_report)
else:
    print("Column 'Aircraft.damage' does not exist in the DataFrame.")
```

    Unique values in 'Aircraft.damage' column: ['Destroyed' 'Substantial' 'Minor' nan 'Unknown']
    


```python
# Here I have decided to drop all rows with missing values under the columns 'Make', 'Aircraft.damage', 'Purpose.of.flight', 'Total.Uninjured'
# since these are columns that contain data that is instrumental for our analysis.

cleaner_av_data = clean_aviation_data.dropna(subset=['Make', 'Aircraft.damage', 'Purpose.of.flight', 'Total.Uninjured', 'Total.Fatal.Injuries', 'Total.Serious.Injuries'])
cleaner_av_data
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
      <th>Event.Id</th>
      <th>Investigation.Type</th>
      <th>Accident.Number</th>
      <th>Event.Date</th>
      <th>Location</th>
      <th>Country</th>
      <th>Injury.Severity</th>
      <th>Aircraft.damage</th>
      <th>Registration.Number</th>
      <th>Make</th>
      <th>...</th>
      <th>Number.of.Engines</th>
      <th>Engine.Type</th>
      <th>Purpose.of.flight</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
      <th>Weather.Condition</th>
      <th>Report.Status</th>
      <th>Publication.Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20001218X45444</td>
      <td>Accident</td>
      <td>SEA87LA080</td>
      <td>1948-10-24</td>
      <td>MOOSE CREEK, ID</td>
      <td>United States</td>
      <td>Fatal(2)</td>
      <td>Destroyed</td>
      <td>NC6404</td>
      <td>Stinson</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Probable Cause</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20001218X45447</td>
      <td>Accident</td>
      <td>LAX94LA336</td>
      <td>1962-07-19</td>
      <td>BRIDGEPORT, CA</td>
      <td>United States</td>
      <td>Fatal(4)</td>
      <td>Destroyed</td>
      <td>N5069P</td>
      <td>Piper</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Probable Cause</td>
      <td>19-09-1996</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20001218X45448</td>
      <td>Accident</td>
      <td>LAX96LA321</td>
      <td>1977-06-19</td>
      <td>EUREKA, CA</td>
      <td>United States</td>
      <td>Fatal(2)</td>
      <td>Destroyed</td>
      <td>N1168J</td>
      <td>Rockwell</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Probable Cause</td>
      <td>12-09-2000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>20041105X01764</td>
      <td>Accident</td>
      <td>CHI79FA064</td>
      <td>1979-08-02</td>
      <td>Canton, OH</td>
      <td>United States</td>
      <td>Fatal(1)</td>
      <td>Destroyed</td>
      <td>N15NY</td>
      <td>Cessna</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>Probable Cause</td>
      <td>16-04-1980</td>
    </tr>
    <tr>
      <th>6</th>
      <td>20001218X45446</td>
      <td>Accident</td>
      <td>CHI81LA106</td>
      <td>1981-08-01</td>
      <td>COTTON, MN</td>
      <td>United States</td>
      <td>Fatal(4)</td>
      <td>Destroyed</td>
      <td>N4988E</td>
      <td>Cessna</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Probable Cause</td>
      <td>06-11-2001</td>
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
      <th>90324</th>
      <td>20221212106444</td>
      <td>Accident</td>
      <td>ERA23LA085</td>
      <td>2022-12-12</td>
      <td>Knoxville, TN</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N783SF</td>
      <td>CESSNA</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Instructional</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>15-12-2022</td>
    </tr>
    <tr>
      <th>90326</th>
      <td>20221213106456</td>
      <td>Accident</td>
      <td>WPR23LA066</td>
      <td>2022-12-12</td>
      <td>Redding, CA</td>
      <td>United States</td>
      <td>Minor</td>
      <td>Substantial</td>
      <td>N415RX</td>
      <td>AIRBUS HELICOPTERS</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Business</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90332</th>
      <td>20221215106463</td>
      <td>Accident</td>
      <td>ERA23LA090</td>
      <td>2022-12-14</td>
      <td>San Juan, PR</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N416PC</td>
      <td>CIRRUS DESIGN CORP</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90336</th>
      <td>20221219106470</td>
      <td>Accident</td>
      <td>ERA23LA091</td>
      <td>2022-12-16</td>
      <td>Brooksville, FL</td>
      <td>United States</td>
      <td>Minor</td>
      <td>Substantial</td>
      <td>N5405V</td>
      <td>CESSNA</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>23-12-2022</td>
    </tr>
    <tr>
      <th>90345</th>
      <td>20221227106497</td>
      <td>Accident</td>
      <td>WPR23LA075</td>
      <td>2022-12-26</td>
      <td>Payson, AZ</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N749PJ</td>
      <td>AMERICAN CHAMPION AIRCRAFT</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
  </tbody>
</table>
<p>68407 rows × 22 columns</p>
</div>




```python
# I wanted to have displayed all the categories under the 'Purpose.of.flight' column so that I can be able to narrow down to a specific purpose for the benefit of my analysis

if 'Purpose.of.flight' in clean_aviation_data.columns:
    unique_report = clean_aviation_data['Purpose.of.flight'].unique()
    print("Unique values in 'Purpose.of.flight' column:", unique_report)
else:
    print("Column 'Purpose.of.flight' does not exist in the DataFrame.")
```

    Unique values in 'Purpose.of.flight' column: ['Personal' nan 'Business' 'Instructional' 'Unknown' 'Ferry'
     'Executive/corporate' 'Aerial Observation' 'Aerial Application'
     'Public Aircraft' 'Skydiving' 'Other Work Use' 'Positioning'
     'Flight Test' 'Air Race/show' 'Air Drop' 'Public Aircraft - Federal'
     'Glider Tow' 'Public Aircraft - Local' 'External Load'
     'Public Aircraft - State' 'Banner Tow' 'Firefighting' 'Air Race show'
     'PUBS' 'ASHO' 'PUBL']
    


```python
# Imputation of data types

# Converting Event.date column data.type to Date-time

cleaner_av_data['Event.Date'] = pd.to_datetime(cleaner_av_data['Event.Date'], errors='coerce')
cleaner_av_data
```

    <ipython-input-15-8d15185e7aaa>:5: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      cleaner_av_data['Event.Date'] = pd.to_datetime(cleaner_av_data['Event.Date'], errors='coerce')
    




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
      <th>Event.Id</th>
      <th>Investigation.Type</th>
      <th>Accident.Number</th>
      <th>Event.Date</th>
      <th>Location</th>
      <th>Country</th>
      <th>Injury.Severity</th>
      <th>Aircraft.damage</th>
      <th>Registration.Number</th>
      <th>Make</th>
      <th>...</th>
      <th>Number.of.Engines</th>
      <th>Engine.Type</th>
      <th>Purpose.of.flight</th>
      <th>Total.Fatal.Injuries</th>
      <th>Total.Serious.Injuries</th>
      <th>Total.Minor.Injuries</th>
      <th>Total.Uninjured</th>
      <th>Weather.Condition</th>
      <th>Report.Status</th>
      <th>Publication.Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20001218X45444</td>
      <td>Accident</td>
      <td>SEA87LA080</td>
      <td>1948-10-24</td>
      <td>MOOSE CREEK, ID</td>
      <td>United States</td>
      <td>Fatal(2)</td>
      <td>Destroyed</td>
      <td>NC6404</td>
      <td>Stinson</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Probable Cause</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20001218X45447</td>
      <td>Accident</td>
      <td>LAX94LA336</td>
      <td>1962-07-19</td>
      <td>BRIDGEPORT, CA</td>
      <td>United States</td>
      <td>Fatal(4)</td>
      <td>Destroyed</td>
      <td>N5069P</td>
      <td>Piper</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>UNK</td>
      <td>Probable Cause</td>
      <td>19-09-1996</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20001218X45448</td>
      <td>Accident</td>
      <td>LAX96LA321</td>
      <td>1977-06-19</td>
      <td>EUREKA, CA</td>
      <td>United States</td>
      <td>Fatal(2)</td>
      <td>Destroyed</td>
      <td>N1168J</td>
      <td>Rockwell</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Probable Cause</td>
      <td>12-09-2000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>20041105X01764</td>
      <td>Accident</td>
      <td>CHI79FA064</td>
      <td>1979-08-02</td>
      <td>Canton, OH</td>
      <td>United States</td>
      <td>Fatal(1)</td>
      <td>Destroyed</td>
      <td>N15NY</td>
      <td>Cessna</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>Probable Cause</td>
      <td>16-04-1980</td>
    </tr>
    <tr>
      <th>6</th>
      <td>20001218X45446</td>
      <td>Accident</td>
      <td>CHI81LA106</td>
      <td>1981-08-01</td>
      <td>COTTON, MN</td>
      <td>United States</td>
      <td>Fatal(4)</td>
      <td>Destroyed</td>
      <td>N4988E</td>
      <td>Cessna</td>
      <td>...</td>
      <td>1.0</td>
      <td>Reciprocating</td>
      <td>Personal</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>IMC</td>
      <td>Probable Cause</td>
      <td>06-11-2001</td>
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
      <th>90324</th>
      <td>20221212106444</td>
      <td>Accident</td>
      <td>ERA23LA085</td>
      <td>2022-12-12</td>
      <td>Knoxville, TN</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N783SF</td>
      <td>CESSNA</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Instructional</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>15-12-2022</td>
    </tr>
    <tr>
      <th>90326</th>
      <td>20221213106456</td>
      <td>Accident</td>
      <td>WPR23LA066</td>
      <td>2022-12-12</td>
      <td>Redding, CA</td>
      <td>United States</td>
      <td>Minor</td>
      <td>Substantial</td>
      <td>N415RX</td>
      <td>AIRBUS HELICOPTERS</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Business</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90332</th>
      <td>20221215106463</td>
      <td>Accident</td>
      <td>ERA23LA090</td>
      <td>2022-12-14</td>
      <td>San Juan, PR</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N416PC</td>
      <td>CIRRUS DESIGN CORP</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
    <tr>
      <th>90336</th>
      <td>20221219106470</td>
      <td>Accident</td>
      <td>ERA23LA091</td>
      <td>2022-12-16</td>
      <td>Brooksville, FL</td>
      <td>United States</td>
      <td>Minor</td>
      <td>Substantial</td>
      <td>N5405V</td>
      <td>CESSNA</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>23-12-2022</td>
    </tr>
    <tr>
      <th>90345</th>
      <td>20221227106497</td>
      <td>Accident</td>
      <td>WPR23LA075</td>
      <td>2022-12-26</td>
      <td>Payson, AZ</td>
      <td>United States</td>
      <td>Non-Fatal</td>
      <td>Substantial</td>
      <td>N749PJ</td>
      <td>AMERICAN CHAMPION AIRCRAFT</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>Personal</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>VMC</td>
      <td>NaN</td>
      <td>27-12-2022</td>
    </tr>
  </tbody>
</table>
<p>68407 rows × 22 columns</p>
</div>




```python
#Checking whether the data-type of the Event.Date has been imputed successfully

cleaner_av_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 68407 entries, 0 to 90345
    Data columns (total 22 columns):
     #   Column                  Non-Null Count  Dtype         
    ---  ------                  --------------  -----         
     0   Event.Id                68407 non-null  object        
     1   Investigation.Type      68407 non-null  object        
     2   Accident.Number         68407 non-null  object        
     3   Event.Date              68407 non-null  datetime64[ns]
     4   Location                68376 non-null  object        
     5   Country                 68207 non-null  object        
     6   Injury.Severity         68374 non-null  object        
     7   Aircraft.damage         68407 non-null  object        
     8   Registration.Number     68196 non-null  object        
     9   Make                    68407 non-null  object        
     10  Model                   68378 non-null  object        
     11  Amateur.Built           68407 non-null  object        
     12  Number.of.Engines       66282 non-null  float64       
     13  Engine.Type             65681 non-null  object        
     14  Purpose.of.flight       68407 non-null  object        
     15  Total.Fatal.Injuries    68407 non-null  float64       
     16  Total.Serious.Injuries  68407 non-null  float64       
     17  Total.Minor.Injuries    68398 non-null  float64       
     18  Total.Uninjured         68407 non-null  float64       
     19  Weather.Condition       67511 non-null  object        
     20  Report.Status           65284 non-null  object        
     21  Publication.Date        54571 non-null  object        
    dtypes: datetime64[ns](1), float64(5), object(16)
    memory usage: 12.0+ MB
    


```python
# Group by 'Make' and 'Event.Date', then count events


fatal_event_counts = cleaner_av_data.groupby(['Make', 'Total.Fatal.Injuries']).size().reset_index(name='Fatal_EventCount')

# Then we group just by 'Make' to get the total number of fatal accidents per make

total_fatal_accidents_by_make = fatal_event_counts.groupby('Make')['Total.Fatal.Injuries'].sum().reset_index()

# Then now Sort in descending order to see which make had the most fatal accidents

sorted_fatal_accidents = total_fatal_accidents_by_make.sort_values('Total.Fatal.Injuries', ascending=False)

sorted_fatal_accidents
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
      <th>Make</th>
      <th>Total.Fatal.Injuries</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>876</th>
      <td>Boeing</td>
      <td>2395.0</td>
    </tr>
    <tr>
      <th>4128</th>
      <td>Mcdonnell Douglas</td>
      <td>897.0</td>
    </tr>
    <tr>
      <th>1787</th>
      <td>Douglas</td>
      <td>602.0</td>
    </tr>
    <tr>
      <th>3739</th>
      <td>Lockheed</td>
      <td>242.0</td>
    </tr>
    <tr>
      <th>295</th>
      <td>Airbus Industrie</td>
      <td>232.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2714</th>
      <td>HODGES SAMUEL J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2713</th>
      <td>HOAC-AUSTRIA</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2710</th>
      <td>HIRN ASSOCIATES LTD</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2708</th>
      <td>HINE T L/JOHNSON R</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>6708</th>
      <td>unknown</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6709 rows × 2 columns</p>
</div>




```python
# This will show us the top 15 riskiest airplane models as per how frequent they are involved in accidents

sorted_fatal_accidents.head(15)
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
      <th>Make</th>
      <th>Total.Fatal.Injuries</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>876</th>
      <td>Boeing</td>
      <td>2395.0</td>
    </tr>
    <tr>
      <th>4128</th>
      <td>Mcdonnell Douglas</td>
      <td>897.0</td>
    </tr>
    <tr>
      <th>1787</th>
      <td>Douglas</td>
      <td>602.0</td>
    </tr>
    <tr>
      <th>3739</th>
      <td>Lockheed</td>
      <td>242.0</td>
    </tr>
    <tr>
      <th>295</th>
      <td>Airbus Industrie</td>
      <td>232.0</td>
    </tr>
    <tr>
      <th>769</th>
      <td>Beech</td>
      <td>163.0</td>
    </tr>
    <tr>
      <th>262</th>
      <td>Aerospatiale</td>
      <td>156.0</td>
    </tr>
    <tr>
      <th>4716</th>
      <td>Piper</td>
      <td>139.0</td>
    </tr>
    <tr>
      <th>1277</th>
      <td>Cessna</td>
      <td>109.0</td>
    </tr>
    <tr>
      <th>1684</th>
      <td>De Havilland</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>1975</th>
      <td>Embraer</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>2140</th>
      <td>Fairchild</td>
      <td>75.0</td>
    </tr>
    <tr>
      <th>779</th>
      <td>Bell</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>949</th>
      <td>British Aerospace</td>
      <td>69.0</td>
    </tr>
    <tr>
      <th>409</th>
      <td>Atr</td>
      <td>68.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# This will show us the top 15 safety airplanes based on how rarely they are involved in accidents

sorted_fatal_accidents.tail(50)
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
      <th>Make</th>
      <th>Total.Fatal.Injuries</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2771</th>
      <td>HURLEY RICHARD A</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2770</th>
      <td>HUNZIKER</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2769</th>
      <td>HUNTHROP</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2768</th>
      <td>HUNTER GEORGE</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2767</th>
      <td>HUNTER</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2766</th>
      <td>HUNT</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2765</th>
      <td>HUNDLEY MICHAEL J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2736</th>
      <td>HOMER</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2734</th>
      <td>HOLST LAWRENCE E</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2678</th>
      <td>HENDERSON MICHAEL E</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2705</th>
      <td>HILLER-TRI-PLEX IND.INC.</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2702</th>
      <td>HILLARD CHARLIE R</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2700</th>
      <td>HIGGINS JOHN H/WILLIAMS JOHN D</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2699</th>
      <td>HIER JAMES A</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2697</th>
      <td>HICKHAM</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2696</th>
      <td>HIBBARD NORMAN E</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2695</th>
      <td>HI-Max</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2693</th>
      <td>HESS JOHN L</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2692</th>
      <td>HERZOG AVIATION</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2691</th>
      <td>HERRICK DAVID A</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2688</th>
      <td>HEREM</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2687</th>
      <td>HERDER MICHAEL</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2686</th>
      <td>HENRY STEVEN J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2685</th>
      <td>HENRY SLOSING</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2684</th>
      <td>HENRY L BERRIER JR</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2683</th>
      <td>HENRIE RAYMOND</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2681</th>
      <td>HENDRYX STEVE/WILEY ROSS</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2680</th>
      <td>HENDRICKS GEORGE DAVID JR</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2704</th>
      <td>HILLER-ROGERSON HELICOPTER</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2706</th>
      <td>HIMMEROEDER HANSGEORG</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2733</th>
      <td>HOLSCLAW FRANCIS E</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2707</th>
      <td>HIMSL VINCENT S</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2732</th>
      <td>HOLMLUND VICTOR P</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2731</th>
      <td>HOLMGREN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2730</th>
      <td>HOLMGREEN JOHN B</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2729</th>
      <td>HOLMES WILLIAM E</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2728</th>
      <td>HOLMES GARY DON</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2727</th>
      <td>HOLM MICHAEL J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2726</th>
      <td>HOLLOMAN L B/HOLLOMAN E M</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2725</th>
      <td>HOLLIER B C</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2724</th>
      <td>HOLLEY CAROL L</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2722</th>
      <td>HOLDEN FRANK JOSEPH</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2721</th>
      <td>HOKE BOBBY F</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2718</th>
      <td>HOFFMAN DAVID K</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2717</th>
      <td>HOFFMAN DAVID J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2714</th>
      <td>HODGES SAMUEL J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2713</th>
      <td>HOAC-AUSTRIA</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2710</th>
      <td>HIRN ASSOCIATES LTD</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2708</th>
      <td>HINE T L/JOHNSON R</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>6708</th>
      <td>unknown</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Step 1: Group by 'Make' and 'Purpose.of.flight', and count
make_purpose_counts = cleaner_av_data.groupby(['Make', 'Purpose.of.flight']).size().reset_index(name='Count')

# Step 2: Group by 'Make' to get total counts (for sorting)
total_by_make = make_purpose_counts.groupby('Make')['Count'].sum().reset_index(name='TotalEvents')

# Step 3: Merge back total counts to original grouped data for sorting
merged = make_purpose_counts.merge(total_by_make, on='Make')

# Step 4: Sort by total events per Make (descending)
sorted_result = merged.sort_values('TotalEvents', ascending=False)

# Step 5: Optional: drop 'TotalEvents' column if you only want counts by purpose
# sorted_result = sorted_result.drop(columns='TotalEvents')

sorted_result
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
      <th>Make</th>
      <th>Purpose.of.flight</th>
      <th>Count</th>
      <th>TotalEvents</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1818</th>
      <td>Cessna</td>
      <td>Skydiving</td>
      <td>13</td>
      <td>17914</td>
    </tr>
    <tr>
      <th>1809</th>
      <td>Cessna</td>
      <td>Flight Test</td>
      <td>3</td>
      <td>17914</td>
    </tr>
    <tr>
      <th>1819</th>
      <td>Cessna</td>
      <td>Unknown</td>
      <td>1326</td>
      <td>17914</td>
    </tr>
    <tr>
      <th>1802</th>
      <td>Cessna</td>
      <td>Aerial Application</td>
      <td>526</td>
      <td>17914</td>
    </tr>
    <tr>
      <th>1803</th>
      <td>Cessna</td>
      <td>Aerial Observation</td>
      <td>153</td>
      <td>17914</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3759</th>
      <td>HUNZIKER</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3758</th>
      <td>HUNTHROP</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3757</th>
      <td>HUNTER GEORGE</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3756</th>
      <td>HUNTER</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8500</th>
      <td>unknown</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>8501 rows × 4 columns</p>
</div>




```python
# Here the objective whas to see the aircraft make with the least number events and also at the same time see what purpose were these flights for

sorted_result.tail(50)
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
      <th>Make</th>
      <th>Purpose.of.flight</th>
      <th>Count</th>
      <th>TotalEvents</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3707</th>
      <td>HOLST LAWRENCE E</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3721</th>
      <td>HOWARD</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3749</th>
      <td>HUGHES CHARLES R</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3732</th>
      <td>HUEBBE</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3731</th>
      <td>HUDSON</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3730</th>
      <td>HUBER HARTMUT</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3729</th>
      <td>HUBBARD WILLIAM H</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3728</th>
      <td>HROSIK GENE</td>
      <td>Positioning</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3727</th>
      <td>HPH SPOL SRO</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3725</th>
      <td>HOWES</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3724</th>
      <td>HOWELL BOB</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3723</th>
      <td>HOWARD M. SHEPHERD</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3720</th>
      <td>HOSTEIN K/HOSTEIN S</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3779</th>
      <td>Halfpap</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3719</th>
      <td>HOSKINS SAMUEL R</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3718</th>
      <td>HOSKINS LONNIE F</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3717</th>
      <td>HOSKINS</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3716</th>
      <td>HOOVER FRANK</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3715</th>
      <td>HOOVER DAVID</td>
      <td>Air Race show</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3714</th>
      <td>HOOPER JAMES A</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3713</th>
      <td>HOOD JOHN SIDNEY</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3710</th>
      <td>HONDA AIRCRAFT</td>
      <td>Executive/corporate</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3709</th>
      <td>HOMER</td>
      <td>Instructional</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3708</th>
      <td>HOLT HERBERT L</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3752</th>
      <td>HUGHES/HELICOPTER ASSOCS INC</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3753</th>
      <td>HUMMEL / FINBERG</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3754</th>
      <td>HUNDLEY MICHAEL J</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3755</th>
      <td>HUNT</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3778</th>
      <td>Halbrook</td>
      <td>Instructional</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3775</th>
      <td>Haggenmacher</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3774</th>
      <td>Hagg</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3773</th>
      <td>Hagerty</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3772</th>
      <td>Hagaman Pitts</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3771</th>
      <td>Haessler</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3770</th>
      <td>Haering Avid Flyer</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3769</th>
      <td>Haecker</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3768</th>
      <td>Hadley</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3767</th>
      <td>Hadaller</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3766</th>
      <td>Hackett/mckown</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3765</th>
      <td>Hackett</td>
      <td>Unknown</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3764</th>
      <td>Haas</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3763</th>
      <td>HYDE WILLIAM R</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3762</th>
      <td>HUTCHINSON KENNETH A</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3761</th>
      <td>HUSTON CHARLES D</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3760</th>
      <td>HURLEY RICHARD A</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3759</th>
      <td>HUNZIKER</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3758</th>
      <td>HUNTHROP</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3757</th>
      <td>HUNTER GEORGE</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3756</th>
      <td>HUNTER</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8500</th>
      <td>unknown</td>
      <td>Personal</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Group by 'Purpose.of.flight' and count occurrences
# Here we will be able to inspect which purpose of flight had highest occurrence for the dataset we are analyzing

purposeflight_counts = cleaner_av_data['Purpose.of.flight'].value_counts().reset_index()

# Rename columns for clarity

purposeflight_counts.columns = ['Purpose.of.flight', 'Count']

# Show the result
purposeflight_counts
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
      <th>Purpose.of.flight</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Personal</td>
      <td>41123</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Instructional</td>
      <td>8719</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Unknown</td>
      <td>5601</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Aerial Application</td>
      <td>4104</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Business</td>
      <td>3457</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Positioning</td>
      <td>1205</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Other Work Use</td>
      <td>937</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Ferry</td>
      <td>724</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Aerial Observation</td>
      <td>660</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Public Aircraft</td>
      <td>523</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Executive/corporate</td>
      <td>447</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Flight Test</td>
      <td>254</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Skydiving</td>
      <td>111</td>
    </tr>
    <tr>
      <th>13</th>
      <td>External Load</td>
      <td>98</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Air Race show</td>
      <td>90</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Public Aircraft - Federal</td>
      <td>78</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Banner Tow</td>
      <td>76</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Public Aircraft - Local</td>
      <td>61</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Public Aircraft - State</td>
      <td>47</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Glider Tow</td>
      <td>43</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Firefighting</td>
      <td>31</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Air Drop</td>
      <td>7</td>
    </tr>
    <tr>
      <th>22</th>
      <td>ASHO</td>
      <td>6</td>
    </tr>
    <tr>
      <th>23</th>
      <td>PUBS</td>
      <td>4</td>
    </tr>
    <tr>
      <th>24</th>
      <td>PUBL</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



### Observations from our analysis

#### Here it can be observed that most of the flights that had being taken as per our dataset is 'Personal', and since our objective is to understand the risk level of the industry, abd determine which investment would be of lower risk for us. It can therefore be observed that as we consider other variables it will be important to ensure most of our investment shoud be directed at Private/Personal services enterprise, more than commercial enterprise.


```python
# Step 1: Filter rows where Purpose.of.flight is 'Personal'
personal_flights = cleaner_av_data[cleaner_av_data['Purpose.of.flight'] == 'Personal']

# Step 2: Count how many times each Make appears in personal flights
make_counts = personal_flights['Make'].value_counts().reset_index()

# Step 3: Rename columns for clarity
make_counts.columns = ['Make', 'PersonalFlightCount']

# Step 4: Show top 20 makes
top_20_makes_personalflight = make_counts.head(20)

top_20_makes_personalflight
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
      <th>Make</th>
      <th>PersonalFlightCount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Cessna</td>
      <td>10597</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Piper</td>
      <td>6394</td>
    </tr>
    <tr>
      <th>2</th>
      <td>CESSNA</td>
      <td>2785</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Beech</td>
      <td>2048</td>
    </tr>
    <tr>
      <th>4</th>
      <td>PIPER</td>
      <td>1836</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Mooney</td>
      <td>703</td>
    </tr>
    <tr>
      <th>6</th>
      <td>BEECH</td>
      <td>668</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Bellanca</td>
      <td>517</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Aeronca</td>
      <td>333</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Champion</td>
      <td>287</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Maule</td>
      <td>271</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Stinson</td>
      <td>258</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Taylorcraft</td>
      <td>234</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Luscombe</td>
      <td>224</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Grumman</td>
      <td>213</td>
    </tr>
    <tr>
      <th>15</th>
      <td>MOONEY</td>
      <td>198</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Bell</td>
      <td>196</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Schweizer</td>
      <td>185</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Boeing</td>
      <td>176</td>
    </tr>
    <tr>
      <th>19</th>
      <td>North American</td>
      <td>176</td>
    </tr>
  </tbody>
</table>
</div>



### Data results on the the most relied upon make of aircraft for Personal flight services.

The data further shows that among all the makes of the aircrafts, the most used for Personal flight services is Cessna,
which takes the lead by a great margin, followed by Piper which also tracks quite far ahead compared to the third most used make.


```python
# Step 1: Filter rows where Purpose.of.flight is 'Business'
biz_flights = cleaner_av_data[cleaner_av_data['Purpose.of.flight'] == 'Business']

# Step 2: Count how many times each Make appears in Business flights
make_counts = biz_flights['Make'].value_counts().reset_index()

# Step 3: Rename columns for clarity
make_counts.columns = ['Make', 'BizFlightCount']

# Step 4: Show top 20 makes
top_20_makes_Bizflight = make_counts.head(20)

top_20_makes_Bizflight
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
      <th>Make</th>
      <th>BizFlightCount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Cessna</td>
      <td>1088</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Piper</td>
      <td>667</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Beech</td>
      <td>388</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bell</td>
      <td>125</td>
    </tr>
    <tr>
      <th>4</th>
      <td>CESSNA</td>
      <td>124</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Mooney</td>
      <td>85</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Hughes</td>
      <td>64</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Bellanca</td>
      <td>50</td>
    </tr>
    <tr>
      <th>8</th>
      <td>PIPER</td>
      <td>49</td>
    </tr>
    <tr>
      <th>9</th>
      <td>BEECH</td>
      <td>46</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Robinson</td>
      <td>36</td>
    </tr>
    <tr>
      <th>11</th>
      <td>De Havilland</td>
      <td>29</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Maule</td>
      <td>24</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Rockwell</td>
      <td>23</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Mitsubishi</td>
      <td>23</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Aero Commander</td>
      <td>22</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Enstrom</td>
      <td>22</td>
    </tr>
    <tr>
      <th>17</th>
      <td>BELL</td>
      <td>19</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Hiller</td>
      <td>17</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Helio</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



### Data results on the the most relied upon make of aircraft for Business flight services.

 In the data above, the top 2 most used makes are similar to those we saw in their former category, though the
third most used brand appears to be different, as in this case its the Beech .

#### A descending list of aircraft makes that are the safest


```python
# Group by 'Make' and 'Event.Date', then count events


minor_event_counts = cleaner_av_data.groupby(['Make', 'Total.Minor.Injuries']).size().reset_index(name='Minor_EventCount')

# Then we group just by 'Make' to get the total number of minor accidents per make

total_minor_accidents_by_make = minor_event_counts.groupby('Make')['Total.Minor.Injuries'].sum().reset_index()

# Then now Sort in descending order to see which make had the most fatal accidents

sorted_minor_accidents = total_minor_accidents_by_make.sort_values('Total.Minor.Injuries', ascending=False)

sorted_minor_accidents
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
      <th>Make</th>
      <th>Total.Minor.Injuries</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>875</th>
      <td>Boeing</td>
      <td>831.0</td>
    </tr>
    <tr>
      <th>4127</th>
      <td>Mcdonnell Douglas</td>
      <td>716.0</td>
    </tr>
    <tr>
      <th>768</th>
      <td>Beech</td>
      <td>143.0</td>
    </tr>
    <tr>
      <th>3738</th>
      <td>Lockheed</td>
      <td>133.0</td>
    </tr>
    <tr>
      <th>1786</th>
      <td>Douglas</td>
      <td>107.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2582</th>
      <td>Gulfstream Aerospace Corp</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2581</th>
      <td>Gulfstream Aerospace</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2578</th>
      <td>Guevremont</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2577</th>
      <td>Grunska Earl J</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3354</th>
      <td>KIRBYBILT AIRCRAFT</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>6708 rows × 2 columns</p>
</div>



A filtered list of the top 20 safest aircraft makes


```python
#Here we sort filter to see the top 20 aircraft makes in the list

sorted_minor_accidents.head(20)
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
      <th>Make</th>
      <th>Total.Minor.Injuries</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>875</th>
      <td>Boeing</td>
      <td>831.0</td>
    </tr>
    <tr>
      <th>4127</th>
      <td>Mcdonnell Douglas</td>
      <td>716.0</td>
    </tr>
    <tr>
      <th>768</th>
      <td>Beech</td>
      <td>143.0</td>
    </tr>
    <tr>
      <th>3738</th>
      <td>Lockheed</td>
      <td>133.0</td>
    </tr>
    <tr>
      <th>1786</th>
      <td>Douglas</td>
      <td>107.0</td>
    </tr>
    <tr>
      <th>295</th>
      <td>Airbus Industrie</td>
      <td>101.0</td>
    </tr>
    <tr>
      <th>1683</th>
      <td>De Havilland</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>1276</th>
      <td>Cessna</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>1974</th>
      <td>Embraer</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>2212</th>
      <td>Fokker</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>778</th>
      <td>Bell</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>4715</th>
      <td>Piper</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>2139</th>
      <td>Fairchild</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2569</th>
      <td>Grumman</td>
      <td>32.0</td>
    </tr>
    <tr>
      <th>1070</th>
      <td>CESSNA</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>6105</th>
      <td>Thunder And Colt</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>262</th>
      <td>Aerospatiale</td>
      <td>28.0</td>
    </tr>
    <tr>
      <th>3682</th>
      <td>Learjet</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>1238</th>
      <td>Cameron</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>712</th>
      <td>Balloon Works</td>
      <td>22.0</td>
    </tr>
  </tbody>
</table>
</div>



### A list of the safest aircraft makes:

#### Through analysis of the data using the pandas library we have been able to identify the aircraft makes which appear to be the most safest,
#### as they have sustained the most minor injuries. We then sorted them list in descending order and were able to see which makes have out performed the rest in this capacity.

## VISUALIZATION OF OUR ANALYSIS RESULTS AND FINDINGS

### 1. A graph showing the top 10 aircraft makes with the that have sustained accidents but encountered minor injuries. 

This will enable us to support our our analysis with a visualization so that the directors of our company can easily understand analysis.


```python
# Here we utilize Matplotlib to visualize our analysis to enable to us to better compare and contrast

import matplotlib.pyplot as plt

# Get the top 10 makes
top_10_makes = sorted_minor_accidents.head(10)

# Create the bar plot
plt.figure(figsize=(10, 6))
plt.bar(top_10_makes['Make'], top_10_makes['Total.Minor.Injuries'], color='green')

# Add titles and labels
plt.title('Top 10 Aircraft Makes with the Most Minor Accidents', fontsize=14)
plt.xlabel('Aircraft Make', fontsize=12)
plt.ylabel('Number of Minor Accidents', fontsize=12)

# Rotate the x-axis labels for better readability
plt.xticks(rotation=45, ha='right')

# Display the plot
plt.tight_layout()
plt.show()

```


    
![png](output_39_0.png)
    


### 2. A horizontal bar graph showing the different aircraft makes and their share of the total Personal flights enterprise

Given that our organization is very keen to diverse its portfolio by buying and operating airplanes for commercial and private enterprises,
it is pertinent for us to identify which aircraft make is most used for Personal flights.


```python
# Here we run a code to generate a horizontal bar graph that demonstates the statement above

# Sort the data in descending order (just in case it's not)
top_20_makes_personalflight = top_20_makes_personalflight.sort_values('PersonalFlightCount', ascending=True)

# Create a horizontal bar plot
plt.figure(figsize=(10, 8))
plt.barh(top_20_makes_personalflight['Make'], top_20_makes_personalflight['PersonalFlightCount'], color='purple')

# Add titles and labels
plt.title('Top 20 Aircraft Makes Used for Personal Flights', fontsize=14)
plt.xlabel('Number of Personal Flights', fontsize=12)
plt.ylabel('Aircraft Make', fontsize=12)

# Add gridlines for easier comparison
plt.grid(axis='x', linestyle='--', alpha=0.7)

# Adjust layout and display the plot
plt.tight_layout()
plt.show()

```


    
![png](output_41_0.png)
    


### 3. A packed bubble visualization showing the top 20 aircraft makes and their share of the Commercial/business flights enterprise.

As we metioned our organization is very keen to diversify its portfolio by buying and operating airplanes for commercial and private enterprises,
in this visualization we attempt to show which make of aircrafts dominate the business flights enterprise. This will enable us to communicate effectively to our directors why we chose specific makes over others.


```python

import numpy as np

# Data
labels = top_20_makes_Bizflight['Make']
sizes = top_20_makes_Bizflight['BizFlightCount']

# Normalize sizes for better visual scaling
scaled_sizes = [size * 10 for size in sizes]

# Generate random positions (for simulation, not perfect packing)
np.random.seed(42)  # for reproducibility
x = np.random.rand(len(labels)) * 100
y = np.random.rand(len(labels)) * 100

# Create the plot
plt.figure(figsize=(16, 10))
scatter = plt.scatter(x, y, s=scaled_sizes, alpha=0.6, c=range(len(labels)), cmap='tab20', edgecolors='black')

# Add labels inside bubbles
for i, label in enumerate(labels):
    plt.text(x[i], y[i], label, ha='left', va='center', fontsize=12)

# Remove axes for clean bubble chart look
plt.axis('off')
plt.title('Top 20 Aircraft Makes Used for Business Flights ', fontsize=16)
plt.show()

```


    
![png](output_43_0.png)
    


## CONCLUSION



My analysis of aircraft makes across safety performance, personal flight usage, and business flight frequency yielded several key insights:

1. Cessna and Beech emerged as the safest aircraft makes, consistently ranking in the top two positions in terms of safety-related metrics. Compared to Boeing and McDonnell Douglas, which showed lower safety performance, Cessna and Beech stand out as more reliable options, especially in a high-risk, emerging industry.

2. Cessna and Beech also dominate both the personal and business flight markets, indicating strong industry reliance and market preference for these makes. Their presence in both key niches aligns well with our organizational objective of targeting these two segments for profitability and market entry.

3. Although Piper and Mooney were competitive in terms of market share for business and personal flights, they did not rank among the top 10 safest aircraft makes. This reduces their attractiveness from a risk mitigation standpoint, which is a crucial factor in our evaluation criteria.

In summary, based on safety, market presence, and strategic alignment with our goals, Cessna and Beech are the most viable makes to prioritize, offering a balanced approach between profitability and risk reduction in this new and uncertain market landscape.




```python
# Saving the cleaned dataset as a CSV file for future use

aviation_data.to_csv(r"data\cleaner_avi_data.csv", index=False)
```
