```python
import numpy as np # library to handle data in a vectorized manner

import pandas as pd # library for data analsysis
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', None)

import json # library to handle JSON files

!conda install -c conda-forge geopy --yes 
from geopy.geocoders import Nominatim # convert an address into latitude and longitude values

import requests # library to handle requests
from pandas.io.json import json_normalize # tranform JSON file into a pandas dataframe

# Matplotlib and associated plotting modules
import matplotlib.cm as cm
import matplotlib.colors as colors

# import k-means from clustering stage
from sklearn.cluster import KMeans

# for webscraping import Beautiful Soup 
from bs4 import BeautifulSoup

import xml

!conda install -c conda-forge folium=0.5.0 --yes 
import folium # map rendering library

print('Libraries imported.')
```

    Collecting package metadata (current_repodata.json): ...working... done
    Solving environment: ...working... done
    

    
    
    ==> WARNING: A newer version of conda exists. <==
      current version: 4.8.2
      latest version: 4.9.2
    
    Please update conda by running
    
        $ conda update -n base -c defaults conda
    
    
    

    Collecting package metadata (current_repodata.json): ...working... done
    Solving environment: ...working... failed with initial frozen solve. Retrying with flexible solve.
    Collecting package metadata (repodata.json): ...working... done
    Solving environment: ...working... done
    
    ## Package Plan ##
    
      environment location: C:\Users\HP\Anaconda3
    
      added / updated specs:
        - folium=0.5.0
    
    
    The following packages will be downloaded:
    
        package                    |            build
        ---------------------------|-----------------
        altair-4.1.0               |             py_1         614 KB  conda-forge
        branca-0.4.1               |             py_0          26 KB  conda-forge
        certifi-2019.9.11          |           py37_0         147 KB  conda-forge
        conda-4.9.2                |   py37h03978a9_0         3.0 MB  conda-forge
        folium-0.5.0               |             py_0          45 KB  conda-forge
        python_abi-3.7             |          1_cp37m           4 KB  conda-forge
        vincent-0.4.4              |             py_1          28 KB  conda-forge
        ------------------------------------------------------------
                                               Total:         3.9 MB
    
    The following NEW packages will be INSTALLED:
    
      altair             conda-forge/noarch::altair-4.1.0-py_1
      branca             conda-forge/noarch::branca-0.4.1-py_0
      folium             conda-forge/noarch::folium-0.5.0-py_0
      python_abi         conda-forge/win-64::python_abi-3.7-1_cp37m
      vincent            conda-forge/noarch::vincent-0.4.4-py_1
    
    The following packages will be UPDATED:
    
      conda                       pkgs/main::conda-4.8.2-py37_0 --> conda-forge::conda-4.9.2-py37h03978a9_0
    
    The following packages will be SUPERSEDED by a higher-priority channel:
    
      certifi                                         pkgs/main --> conda-forge
    
    
    
    Downloading and Extracting Packages
    
    certifi-2019.9.11    | 147 KB    |            |   0% 
    certifi-2019.9.11    | 147 KB    | #          |  11% 
    certifi-2019.9.11    | 147 KB    | ########## | 100% 
    
    python_abi-3.7       | 4 KB      |            |   0% 
    python_abi-3.7       | 4 KB      | ########## | 100% 
    
    conda-4.9.2          | 3.0 MB    |            |   0% 
    conda-4.9.2          | 3.0 MB    | 4          |   4% 
    conda-4.9.2          | 3.0 MB    | ##7        |  28% 
    conda-4.9.2          | 3.0 MB    | #####7     |  57% 
    conda-4.9.2          | 3.0 MB    | #########2 |  92% 
    conda-4.9.2          | 3.0 MB    | ########## | 100% 
    
    vincent-0.4.4        | 28 KB     |            |   0% 
    vincent-0.4.4        | 28 KB     | ########## | 100% 
    
    folium-0.5.0         | 45 KB     |            |   0% 
    folium-0.5.0         | 45 KB     | ########## | 100% 
    
    branca-0.4.1         | 26 KB     |            |   0% 
    branca-0.4.1         | 26 KB     | ######1    |  62% 
    branca-0.4.1         | 26 KB     | ########## | 100% 
    
    altair-4.1.0         | 614 KB    |            |   0% 
    altair-4.1.0         | 614 KB    | 2          |   3% 
    altair-4.1.0         | 614 KB    | ########## | 100% 
    Preparing transaction: ...working... done
    Verifying transaction: ...working... done
    Executing transaction: ...working... done
    Libraries imported.
    

    
    
    ==> WARNING: A newer version of conda exists. <==
      current version: 4.8.2
      latest version: 4.9.2
    
    Please update conda by running
    
        $ conda update -n base -c defaults conda
    
    
    


```python
conda update -n base -c defaults conda

```

    Collecting package metadata (current_repodata.json): ...working... done
    Solving environment: ...working... done
    
    ## Package Plan ##
    
      environment location: C:\Users\HP\Anaconda3
    
      added / updated specs:
        - conda
    
    
    The following packages will be downloaded:
    
        package                    |            build
        ---------------------------|-----------------
        altair-4.1.0               |             py_1         484 KB
        backports.functools_lru_cache-1.6.1|     pyhd3eb1b0_0          12 KB
        conda-4.9.2                |   py37haa95532_0         2.9 MB
        conda-package-handling-1.7.2|   py37h76e460a_0         724 KB
        future-0.18.2              |           py37_1         646 KB
        ------------------------------------------------------------
                                               Total:         4.7 MB
    
    The following packages will be REMOVED:
    
      python_abi-3.7-1_cp37m
    
    The following packages will be UPDATED:
    
      conda-package-han~                   1.6.0-py37h62dcd97_0 --> 1.7.2-py37h76e460a_0
      future                                      0.18.2-py37_0 --> 0.18.2-py37_1
    
    The following packages will be SUPERSEDED by a higher-priority channel:
    
      altair                                        conda-forge --> pkgs/main
      conda              conda-forge::conda-4.9.2-py37h03978a9~ --> pkgs/main::conda-4.9.2-py37haa95532_0
    
    The following packages will be DOWNGRADED:
    
      backports.functoo~                             1.6.1-py_0 --> 1.6.1-pyhd3eb1b0_0
    
    
    
    Downloading and Extracting Packages
    
    backports.functools_ | 12 KB     |            |   0% 
    backports.functools_ | 12 KB     | ########## | 100% 
    backports.functools_ | 12 KB     | ########## | 100% 
    
    altair-4.1.0         | 484 KB    |            |   0% 
    altair-4.1.0         | 484 KB    | ##9        |  30% 
    altair-4.1.0         | 484 KB    | ########6  |  86% 
    altair-4.1.0         | 484 KB    | ########## | 100% 
    
    conda-4.9.2          | 2.9 MB    |            |   0% 
    conda-4.9.2          | 2.9 MB    | 7          |   7% 
    conda-4.9.2          | 2.9 MB    | #7         |  18% 
    conda-4.9.2          | 2.9 MB    | ##9        |  29% 
    conda-4.9.2          | 2.9 MB    | ####       |  41% 
    conda-4.9.2          | 2.9 MB    | #####6     |  57% 
    conda-4.9.2          | 2.9 MB    | ######7    |  68% 
    conda-4.9.2          | 2.9 MB    | #######8   |  79% 
    conda-4.9.2          | 2.9 MB    | #########2 |  93% 
    conda-4.9.2          | 2.9 MB    | ########## | 100% 
    
    conda-package-handli | 724 KB    |            |   0% 
    conda-package-handli | 724 KB    | #9         |  20% 
    conda-package-handli | 724 KB    | ####6      |  46% 
    conda-package-handli | 724 KB    | ########1  |  82% 
    conda-package-handli | 724 KB    | ########## | 100% 
    conda-package-handli | 724 KB    | ########## | 100% 
    
    future-0.18.2        | 646 KB    |            |   0% 
    future-0.18.2        | 646 KB    | #9         |  20% 
    future-0.18.2        | 646 KB    | ########## | 100% 
    future-0.18.2        | 646 KB    | ########## | 100% 
    Preparing transaction: ...working... done
    Verifying transaction: ...working... done
    Executing transaction: ...working... done
    
    Note: you may need to restart the kernel to use updated packages.
    


```python
url = requests.get('https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M').text
soup = BeautifulSoup(url,'lxml')
```


```python
table_post = soup.find('table')
fields = table_post.find_all('td')

postcode = []
borough = []
neighbourhood = []

for i in range(0, len(fields), 3):
    postcode.append(fields[i].text.strip())
    borough.append(fields[i+1].text.strip())
    neighbourhood.append(fields[i+2].text.strip())
        
df_pc = pd.DataFrame(data=[postcode, borough, neighbourhood]).transpose()
df_pc.columns = ['Postcode', 'Borough', 'Neighbourhood']
df_pc.head()
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
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1A</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M2A</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Regent Park, Harbourfront</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_pc.head()
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
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1A</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M2A</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Regent Park, Harbourfront</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_pc['Borough'].replace('Not assigned', np.nan, inplace=True)
df_pc.dropna(subset=['Borough'], inplace=True)

df_pc.head()
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
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Regent Park, Harbourfront</td>
    </tr>
    <tr>
      <td>5</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Manor, Lawrence Heights</td>
    </tr>
    <tr>
      <td>6</td>
      <td>M7A</td>
      <td>Downtown Toronto</td>
      <td>Queen's Park, Ontario Provincial Government</td>
    </tr>
  </tbody>
</table>
</div>




```python

df_pcn = df_pc.groupby(['Postcode', 'Borough'])['Neighbourhood'].apply(', '.join).reset_index()
df_pcn.columns = ['Postcode', 'Borough', 'Neighbourhood']
df_pcn
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
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Malvern, Rouge</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Rouge Hill, Port Union, Highland Creek</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood, Morningside, West Hill</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
    </tr>
    <tr>
      <td>5</td>
      <td>M1J</td>
      <td>Scarborough</td>
      <td>Scarborough Village</td>
    </tr>
    <tr>
      <td>6</td>
      <td>M1K</td>
      <td>Scarborough</td>
      <td>Kennedy Park, Ionview, East Birchmount Park</td>
    </tr>
    <tr>
      <td>7</td>
      <td>M1L</td>
      <td>Scarborough</td>
      <td>Golden Mile, Clairlea, Oakridge</td>
    </tr>
    <tr>
      <td>8</td>
      <td>M1M</td>
      <td>Scarborough</td>
      <td>Cliffside, Cliffcrest, Scarborough Village West</td>
    </tr>
    <tr>
      <td>9</td>
      <td>M1N</td>
      <td>Scarborough</td>
      <td>Birch Cliff, Cliffside West</td>
    </tr>
    <tr>
      <td>10</td>
      <td>M1P</td>
      <td>Scarborough</td>
      <td>Dorset Park, Wexford Heights, Scarborough Town...</td>
    </tr>
    <tr>
      <td>11</td>
      <td>M1R</td>
      <td>Scarborough</td>
      <td>Wexford, Maryvale</td>
    </tr>
    <tr>
      <td>12</td>
      <td>M1S</td>
      <td>Scarborough</td>
      <td>Agincourt</td>
    </tr>
    <tr>
      <td>13</td>
      <td>M1T</td>
      <td>Scarborough</td>
      <td>Clarks Corners, Tam O'Shanter, Sullivan</td>
    </tr>
    <tr>
      <td>14</td>
      <td>M1V</td>
      <td>Scarborough</td>
      <td>Milliken, Agincourt North, Steeles East, L'Amo...</td>
    </tr>
    <tr>
      <td>15</td>
      <td>M1W</td>
      <td>Scarborough</td>
      <td>Steeles West, L'Amoreaux West</td>
    </tr>
    <tr>
      <td>16</td>
      <td>M1X</td>
      <td>Scarborough</td>
      <td>Upper Rouge</td>
    </tr>
    <tr>
      <td>17</td>
      <td>M2H</td>
      <td>North York</td>
      <td>Hillcrest Village</td>
    </tr>
    <tr>
      <td>18</td>
      <td>M2J</td>
      <td>North York</td>
      <td>Fairview, Henry Farm, Oriole</td>
    </tr>
    <tr>
      <td>19</td>
      <td>M2K</td>
      <td>North York</td>
      <td>Bayview Village</td>
    </tr>
    <tr>
      <td>20</td>
      <td>M2L</td>
      <td>North York</td>
      <td>York Mills, Silver Hills</td>
    </tr>
    <tr>
      <td>21</td>
      <td>M2M</td>
      <td>North York</td>
      <td>Willowdale, Newtonbrook</td>
    </tr>
    <tr>
      <td>22</td>
      <td>M2N</td>
      <td>North York</td>
      <td>Willowdale, Willowdale East</td>
    </tr>
    <tr>
      <td>23</td>
      <td>M2P</td>
      <td>North York</td>
      <td>York Mills West</td>
    </tr>
    <tr>
      <td>24</td>
      <td>M2R</td>
      <td>North York</td>
      <td>Willowdale, Willowdale West</td>
    </tr>
    <tr>
      <td>25</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>26</td>
      <td>M3B</td>
      <td>North York</td>
      <td>Don Mills</td>
    </tr>
    <tr>
      <td>27</td>
      <td>M3C</td>
      <td>North York</td>
      <td>Don Mills</td>
    </tr>
    <tr>
      <td>28</td>
      <td>M3H</td>
      <td>North York</td>
      <td>Bathurst Manor, Wilson Heights, Downsview North</td>
    </tr>
    <tr>
      <td>29</td>
      <td>M3J</td>
      <td>North York</td>
      <td>Northwood Park, York University</td>
    </tr>
    <tr>
      <td>30</td>
      <td>M3K</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>31</td>
      <td>M3L</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>32</td>
      <td>M3M</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>33</td>
      <td>M3N</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>34</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>35</td>
      <td>M4B</td>
      <td>East York</td>
      <td>Parkview Hill, Woodbine Gardens</td>
    </tr>
    <tr>
      <td>36</td>
      <td>M4C</td>
      <td>East York</td>
      <td>Woodbine Heights</td>
    </tr>
    <tr>
      <td>37</td>
      <td>M4E</td>
      <td>East Toronto</td>
      <td>The Beaches</td>
    </tr>
    <tr>
      <td>38</td>
      <td>M4G</td>
      <td>East York</td>
      <td>Leaside</td>
    </tr>
    <tr>
      <td>39</td>
      <td>M4H</td>
      <td>East York</td>
      <td>Thorncliffe Park</td>
    </tr>
    <tr>
      <td>40</td>
      <td>M4J</td>
      <td>East York</td>
      <td>East Toronto, Broadview North (Old East York)</td>
    </tr>
    <tr>
      <td>41</td>
      <td>M4K</td>
      <td>East Toronto</td>
      <td>The Danforth West, Riverdale</td>
    </tr>
    <tr>
      <td>42</td>
      <td>M4L</td>
      <td>East Toronto</td>
      <td>India Bazaar, The Beaches West</td>
    </tr>
    <tr>
      <td>43</td>
      <td>M4M</td>
      <td>East Toronto</td>
      <td>Studio District</td>
    </tr>
    <tr>
      <td>44</td>
      <td>M4N</td>
      <td>Central Toronto</td>
      <td>Lawrence Park</td>
    </tr>
    <tr>
      <td>45</td>
      <td>M4P</td>
      <td>Central Toronto</td>
      <td>Davisville North</td>
    </tr>
    <tr>
      <td>46</td>
      <td>M4R</td>
      <td>Central Toronto</td>
      <td>North Toronto West,  Lawrence Park</td>
    </tr>
    <tr>
      <td>47</td>
      <td>M4S</td>
      <td>Central Toronto</td>
      <td>Davisville</td>
    </tr>
    <tr>
      <td>48</td>
      <td>M4T</td>
      <td>Central Toronto</td>
      <td>Moore Park, Summerhill East</td>
    </tr>
    <tr>
      <td>49</td>
      <td>M4V</td>
      <td>Central Toronto</td>
      <td>Summerhill West, Rathnelly, South Hill, Forest...</td>
    </tr>
    <tr>
      <td>50</td>
      <td>M4W</td>
      <td>Downtown Toronto</td>
      <td>Rosedale</td>
    </tr>
    <tr>
      <td>51</td>
      <td>M4X</td>
      <td>Downtown Toronto</td>
      <td>St. James Town, Cabbagetown</td>
    </tr>
    <tr>
      <td>52</td>
      <td>M4Y</td>
      <td>Downtown Toronto</td>
      <td>Church and Wellesley</td>
    </tr>
    <tr>
      <td>53</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Regent Park, Harbourfront</td>
    </tr>
    <tr>
      <td>54</td>
      <td>M5B</td>
      <td>Downtown Toronto</td>
      <td>Garden District, Ryerson</td>
    </tr>
    <tr>
      <td>55</td>
      <td>M5C</td>
      <td>Downtown Toronto</td>
      <td>St. James Town</td>
    </tr>
    <tr>
      <td>56</td>
      <td>M5E</td>
      <td>Downtown Toronto</td>
      <td>Berczy Park</td>
    </tr>
    <tr>
      <td>57</td>
      <td>M5G</td>
      <td>Downtown Toronto</td>
      <td>Central Bay Street</td>
    </tr>
    <tr>
      <td>58</td>
      <td>M5H</td>
      <td>Downtown Toronto</td>
      <td>Richmond, Adelaide, King</td>
    </tr>
    <tr>
      <td>59</td>
      <td>M5J</td>
      <td>Downtown Toronto</td>
      <td>Harbourfront East, Union Station, Toronto Islands</td>
    </tr>
    <tr>
      <td>60</td>
      <td>M5K</td>
      <td>Downtown Toronto</td>
      <td>Toronto Dominion Centre, Design Exchange</td>
    </tr>
    <tr>
      <td>61</td>
      <td>M5L</td>
      <td>Downtown Toronto</td>
      <td>Commerce Court, Victoria Hotel</td>
    </tr>
    <tr>
      <td>62</td>
      <td>M5M</td>
      <td>North York</td>
      <td>Bedford Park, Lawrence Manor East</td>
    </tr>
    <tr>
      <td>63</td>
      <td>M5N</td>
      <td>Central Toronto</td>
      <td>Roselawn</td>
    </tr>
    <tr>
      <td>64</td>
      <td>M5P</td>
      <td>Central Toronto</td>
      <td>Forest Hill North &amp; West, Forest Hill Road Park</td>
    </tr>
    <tr>
      <td>65</td>
      <td>M5R</td>
      <td>Central Toronto</td>
      <td>The Annex, North Midtown, Yorkville</td>
    </tr>
    <tr>
      <td>66</td>
      <td>M5S</td>
      <td>Downtown Toronto</td>
      <td>University of Toronto, Harbord</td>
    </tr>
    <tr>
      <td>67</td>
      <td>M5T</td>
      <td>Downtown Toronto</td>
      <td>Kensington Market, Chinatown, Grange Park</td>
    </tr>
    <tr>
      <td>68</td>
      <td>M5V</td>
      <td>Downtown Toronto</td>
      <td>CN Tower, King and Spadina, Railway Lands, Har...</td>
    </tr>
    <tr>
      <td>69</td>
      <td>M5W</td>
      <td>Downtown Toronto</td>
      <td>Stn A PO Boxes</td>
    </tr>
    <tr>
      <td>70</td>
      <td>M5X</td>
      <td>Downtown Toronto</td>
      <td>First Canadian Place, Underground city</td>
    </tr>
    <tr>
      <td>71</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Manor, Lawrence Heights</td>
    </tr>
    <tr>
      <td>72</td>
      <td>M6B</td>
      <td>North York</td>
      <td>Glencairn</td>
    </tr>
    <tr>
      <td>73</td>
      <td>M6C</td>
      <td>York</td>
      <td>Humewood-Cedarvale</td>
    </tr>
    <tr>
      <td>74</td>
      <td>M6E</td>
      <td>York</td>
      <td>Caledonia-Fairbanks</td>
    </tr>
    <tr>
      <td>75</td>
      <td>M6G</td>
      <td>Downtown Toronto</td>
      <td>Christie</td>
    </tr>
    <tr>
      <td>76</td>
      <td>M6H</td>
      <td>West Toronto</td>
      <td>Dufferin, Dovercourt Village</td>
    </tr>
    <tr>
      <td>77</td>
      <td>M6J</td>
      <td>West Toronto</td>
      <td>Little Portugal, Trinity</td>
    </tr>
    <tr>
      <td>78</td>
      <td>M6K</td>
      <td>West Toronto</td>
      <td>Brockton, Parkdale Village, Exhibition Place</td>
    </tr>
    <tr>
      <td>79</td>
      <td>M6L</td>
      <td>North York</td>
      <td>North Park, Maple Leaf Park, Upwood Park</td>
    </tr>
    <tr>
      <td>80</td>
      <td>M6M</td>
      <td>York</td>
      <td>Del Ray, Mount Dennis, Keelsdale and Silverthorn</td>
    </tr>
    <tr>
      <td>81</td>
      <td>M6N</td>
      <td>York</td>
      <td>Runnymede, The Junction North</td>
    </tr>
    <tr>
      <td>82</td>
      <td>M6P</td>
      <td>West Toronto</td>
      <td>High Park, The Junction South</td>
    </tr>
    <tr>
      <td>83</td>
      <td>M6R</td>
      <td>West Toronto</td>
      <td>Parkdale, Roncesvalles</td>
    </tr>
    <tr>
      <td>84</td>
      <td>M6S</td>
      <td>West Toronto</td>
      <td>Runnymede, Swansea</td>
    </tr>
    <tr>
      <td>85</td>
      <td>M7A</td>
      <td>Downtown Toronto</td>
      <td>Queen's Park, Ontario Provincial Government</td>
    </tr>
    <tr>
      <td>86</td>
      <td>M7R</td>
      <td>Mississauga</td>
      <td>Canada Post Gateway Processing Centre</td>
    </tr>
    <tr>
      <td>87</td>
      <td>M7Y</td>
      <td>East Toronto</td>
      <td>Business reply mail Processing Centre, South C...</td>
    </tr>
    <tr>
      <td>88</td>
      <td>M8V</td>
      <td>Etobicoke</td>
      <td>New Toronto, Mimico South, Humber Bay Shores</td>
    </tr>
    <tr>
      <td>89</td>
      <td>M8W</td>
      <td>Etobicoke</td>
      <td>Alderwood, Long Branch</td>
    </tr>
    <tr>
      <td>90</td>
      <td>M8X</td>
      <td>Etobicoke</td>
      <td>The Kingsway, Montgomery Road, Old Mill North</td>
    </tr>
    <tr>
      <td>91</td>
      <td>M8Y</td>
      <td>Etobicoke</td>
      <td>Old Mill South, King's Mill Park, Sunnylea, Hu...</td>
    </tr>
    <tr>
      <td>92</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Mimico NW, The Queensway West, South of Bloor,...</td>
    </tr>
    <tr>
      <td>93</td>
      <td>M9A</td>
      <td>Etobicoke</td>
      <td>Islington Avenue, Humber Valley Village</td>
    </tr>
    <tr>
      <td>94</td>
      <td>M9B</td>
      <td>Etobicoke</td>
      <td>West Deane Park, Princess Gardens, Martin Grov...</td>
    </tr>
    <tr>
      <td>95</td>
      <td>M9C</td>
      <td>Etobicoke</td>
      <td>Eringate, Bloordale Gardens, Old Burnhamthorpe...</td>
    </tr>
    <tr>
      <td>96</td>
      <td>M9L</td>
      <td>North York</td>
      <td>Humber Summit</td>
    </tr>
    <tr>
      <td>97</td>
      <td>M9M</td>
      <td>North York</td>
      <td>Humberlea, Emery</td>
    </tr>
    <tr>
      <td>98</td>
      <td>M9N</td>
      <td>York</td>
      <td>Weston</td>
    </tr>
    <tr>
      <td>99</td>
      <td>M9P</td>
      <td>Etobicoke</td>
      <td>Westmount</td>
    </tr>
    <tr>
      <td>100</td>
      <td>M9R</td>
      <td>Etobicoke</td>
      <td>Kingsview Village, St. Phillips, Martin Grove ...</td>
    </tr>
    <tr>
      <td>101</td>
      <td>M9V</td>
      <td>Etobicoke</td>
      <td>South Steeles, Silverstone, Humbergate, Jamest...</td>
    </tr>
    <tr>
      <td>102</td>
      <td>M9W</td>
      <td>Etobicoke</td>
      <td>Northwest, West Humber - Clairville</td>
    </tr>
  </tbody>
</table>
</div>




```python

df_pcn['Neighbourhood'].replace('Not assigned', "Queen's Park", inplace=True)

df_pcn
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
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Malvern, Rouge</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Rouge Hill, Port Union, Highland Creek</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood, Morningside, West Hill</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
    </tr>
    <tr>
      <td>5</td>
      <td>M1J</td>
      <td>Scarborough</td>
      <td>Scarborough Village</td>
    </tr>
    <tr>
      <td>6</td>
      <td>M1K</td>
      <td>Scarborough</td>
      <td>Kennedy Park, Ionview, East Birchmount Park</td>
    </tr>
    <tr>
      <td>7</td>
      <td>M1L</td>
      <td>Scarborough</td>
      <td>Golden Mile, Clairlea, Oakridge</td>
    </tr>
    <tr>
      <td>8</td>
      <td>M1M</td>
      <td>Scarborough</td>
      <td>Cliffside, Cliffcrest, Scarborough Village West</td>
    </tr>
    <tr>
      <td>9</td>
      <td>M1N</td>
      <td>Scarborough</td>
      <td>Birch Cliff, Cliffside West</td>
    </tr>
    <tr>
      <td>10</td>
      <td>M1P</td>
      <td>Scarborough</td>
      <td>Dorset Park, Wexford Heights, Scarborough Town...</td>
    </tr>
    <tr>
      <td>11</td>
      <td>M1R</td>
      <td>Scarborough</td>
      <td>Wexford, Maryvale</td>
    </tr>
    <tr>
      <td>12</td>
      <td>M1S</td>
      <td>Scarborough</td>
      <td>Agincourt</td>
    </tr>
    <tr>
      <td>13</td>
      <td>M1T</td>
      <td>Scarborough</td>
      <td>Clarks Corners, Tam O'Shanter, Sullivan</td>
    </tr>
    <tr>
      <td>14</td>
      <td>M1V</td>
      <td>Scarborough</td>
      <td>Milliken, Agincourt North, Steeles East, L'Amo...</td>
    </tr>
    <tr>
      <td>15</td>
      <td>M1W</td>
      <td>Scarborough</td>
      <td>Steeles West, L'Amoreaux West</td>
    </tr>
    <tr>
      <td>16</td>
      <td>M1X</td>
      <td>Scarborough</td>
      <td>Upper Rouge</td>
    </tr>
    <tr>
      <td>17</td>
      <td>M2H</td>
      <td>North York</td>
      <td>Hillcrest Village</td>
    </tr>
    <tr>
      <td>18</td>
      <td>M2J</td>
      <td>North York</td>
      <td>Fairview, Henry Farm, Oriole</td>
    </tr>
    <tr>
      <td>19</td>
      <td>M2K</td>
      <td>North York</td>
      <td>Bayview Village</td>
    </tr>
    <tr>
      <td>20</td>
      <td>M2L</td>
      <td>North York</td>
      <td>York Mills, Silver Hills</td>
    </tr>
    <tr>
      <td>21</td>
      <td>M2M</td>
      <td>North York</td>
      <td>Willowdale, Newtonbrook</td>
    </tr>
    <tr>
      <td>22</td>
      <td>M2N</td>
      <td>North York</td>
      <td>Willowdale, Willowdale East</td>
    </tr>
    <tr>
      <td>23</td>
      <td>M2P</td>
      <td>North York</td>
      <td>York Mills West</td>
    </tr>
    <tr>
      <td>24</td>
      <td>M2R</td>
      <td>North York</td>
      <td>Willowdale, Willowdale West</td>
    </tr>
    <tr>
      <td>25</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>26</td>
      <td>M3B</td>
      <td>North York</td>
      <td>Don Mills</td>
    </tr>
    <tr>
      <td>27</td>
      <td>M3C</td>
      <td>North York</td>
      <td>Don Mills</td>
    </tr>
    <tr>
      <td>28</td>
      <td>M3H</td>
      <td>North York</td>
      <td>Bathurst Manor, Wilson Heights, Downsview North</td>
    </tr>
    <tr>
      <td>29</td>
      <td>M3J</td>
      <td>North York</td>
      <td>Northwood Park, York University</td>
    </tr>
    <tr>
      <td>30</td>
      <td>M3K</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>31</td>
      <td>M3L</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>32</td>
      <td>M3M</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>33</td>
      <td>M3N</td>
      <td>North York</td>
      <td>Downsview</td>
    </tr>
    <tr>
      <td>34</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>35</td>
      <td>M4B</td>
      <td>East York</td>
      <td>Parkview Hill, Woodbine Gardens</td>
    </tr>
    <tr>
      <td>36</td>
      <td>M4C</td>
      <td>East York</td>
      <td>Woodbine Heights</td>
    </tr>
    <tr>
      <td>37</td>
      <td>M4E</td>
      <td>East Toronto</td>
      <td>The Beaches</td>
    </tr>
    <tr>
      <td>38</td>
      <td>M4G</td>
      <td>East York</td>
      <td>Leaside</td>
    </tr>
    <tr>
      <td>39</td>
      <td>M4H</td>
      <td>East York</td>
      <td>Thorncliffe Park</td>
    </tr>
    <tr>
      <td>40</td>
      <td>M4J</td>
      <td>East York</td>
      <td>East Toronto, Broadview North (Old East York)</td>
    </tr>
    <tr>
      <td>41</td>
      <td>M4K</td>
      <td>East Toronto</td>
      <td>The Danforth West, Riverdale</td>
    </tr>
    <tr>
      <td>42</td>
      <td>M4L</td>
      <td>East Toronto</td>
      <td>India Bazaar, The Beaches West</td>
    </tr>
    <tr>
      <td>43</td>
      <td>M4M</td>
      <td>East Toronto</td>
      <td>Studio District</td>
    </tr>
    <tr>
      <td>44</td>
      <td>M4N</td>
      <td>Central Toronto</td>
      <td>Lawrence Park</td>
    </tr>
    <tr>
      <td>45</td>
      <td>M4P</td>
      <td>Central Toronto</td>
      <td>Davisville North</td>
    </tr>
    <tr>
      <td>46</td>
      <td>M4R</td>
      <td>Central Toronto</td>
      <td>North Toronto West,  Lawrence Park</td>
    </tr>
    <tr>
      <td>47</td>
      <td>M4S</td>
      <td>Central Toronto</td>
      <td>Davisville</td>
    </tr>
    <tr>
      <td>48</td>
      <td>M4T</td>
      <td>Central Toronto</td>
      <td>Moore Park, Summerhill East</td>
    </tr>
    <tr>
      <td>49</td>
      <td>M4V</td>
      <td>Central Toronto</td>
      <td>Summerhill West, Rathnelly, South Hill, Forest...</td>
    </tr>
    <tr>
      <td>50</td>
      <td>M4W</td>
      <td>Downtown Toronto</td>
      <td>Rosedale</td>
    </tr>
    <tr>
      <td>51</td>
      <td>M4X</td>
      <td>Downtown Toronto</td>
      <td>St. James Town, Cabbagetown</td>
    </tr>
    <tr>
      <td>52</td>
      <td>M4Y</td>
      <td>Downtown Toronto</td>
      <td>Church and Wellesley</td>
    </tr>
    <tr>
      <td>53</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Regent Park, Harbourfront</td>
    </tr>
    <tr>
      <td>54</td>
      <td>M5B</td>
      <td>Downtown Toronto</td>
      <td>Garden District, Ryerson</td>
    </tr>
    <tr>
      <td>55</td>
      <td>M5C</td>
      <td>Downtown Toronto</td>
      <td>St. James Town</td>
    </tr>
    <tr>
      <td>56</td>
      <td>M5E</td>
      <td>Downtown Toronto</td>
      <td>Berczy Park</td>
    </tr>
    <tr>
      <td>57</td>
      <td>M5G</td>
      <td>Downtown Toronto</td>
      <td>Central Bay Street</td>
    </tr>
    <tr>
      <td>58</td>
      <td>M5H</td>
      <td>Downtown Toronto</td>
      <td>Richmond, Adelaide, King</td>
    </tr>
    <tr>
      <td>59</td>
      <td>M5J</td>
      <td>Downtown Toronto</td>
      <td>Harbourfront East, Union Station, Toronto Islands</td>
    </tr>
    <tr>
      <td>60</td>
      <td>M5K</td>
      <td>Downtown Toronto</td>
      <td>Toronto Dominion Centre, Design Exchange</td>
    </tr>
    <tr>
      <td>61</td>
      <td>M5L</td>
      <td>Downtown Toronto</td>
      <td>Commerce Court, Victoria Hotel</td>
    </tr>
    <tr>
      <td>62</td>
      <td>M5M</td>
      <td>North York</td>
      <td>Bedford Park, Lawrence Manor East</td>
    </tr>
    <tr>
      <td>63</td>
      <td>M5N</td>
      <td>Central Toronto</td>
      <td>Roselawn</td>
    </tr>
    <tr>
      <td>64</td>
      <td>M5P</td>
      <td>Central Toronto</td>
      <td>Forest Hill North &amp; West, Forest Hill Road Park</td>
    </tr>
    <tr>
      <td>65</td>
      <td>M5R</td>
      <td>Central Toronto</td>
      <td>The Annex, North Midtown, Yorkville</td>
    </tr>
    <tr>
      <td>66</td>
      <td>M5S</td>
      <td>Downtown Toronto</td>
      <td>University of Toronto, Harbord</td>
    </tr>
    <tr>
      <td>67</td>
      <td>M5T</td>
      <td>Downtown Toronto</td>
      <td>Kensington Market, Chinatown, Grange Park</td>
    </tr>
    <tr>
      <td>68</td>
      <td>M5V</td>
      <td>Downtown Toronto</td>
      <td>CN Tower, King and Spadina, Railway Lands, Har...</td>
    </tr>
    <tr>
      <td>69</td>
      <td>M5W</td>
      <td>Downtown Toronto</td>
      <td>Stn A PO Boxes</td>
    </tr>
    <tr>
      <td>70</td>
      <td>M5X</td>
      <td>Downtown Toronto</td>
      <td>First Canadian Place, Underground city</td>
    </tr>
    <tr>
      <td>71</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Manor, Lawrence Heights</td>
    </tr>
    <tr>
      <td>72</td>
      <td>M6B</td>
      <td>North York</td>
      <td>Glencairn</td>
    </tr>
    <tr>
      <td>73</td>
      <td>M6C</td>
      <td>York</td>
      <td>Humewood-Cedarvale</td>
    </tr>
    <tr>
      <td>74</td>
      <td>M6E</td>
      <td>York</td>
      <td>Caledonia-Fairbanks</td>
    </tr>
    <tr>
      <td>75</td>
      <td>M6G</td>
      <td>Downtown Toronto</td>
      <td>Christie</td>
    </tr>
    <tr>
      <td>76</td>
      <td>M6H</td>
      <td>West Toronto</td>
      <td>Dufferin, Dovercourt Village</td>
    </tr>
    <tr>
      <td>77</td>
      <td>M6J</td>
      <td>West Toronto</td>
      <td>Little Portugal, Trinity</td>
    </tr>
    <tr>
      <td>78</td>
      <td>M6K</td>
      <td>West Toronto</td>
      <td>Brockton, Parkdale Village, Exhibition Place</td>
    </tr>
    <tr>
      <td>79</td>
      <td>M6L</td>
      <td>North York</td>
      <td>North Park, Maple Leaf Park, Upwood Park</td>
    </tr>
    <tr>
      <td>80</td>
      <td>M6M</td>
      <td>York</td>
      <td>Del Ray, Mount Dennis, Keelsdale and Silverthorn</td>
    </tr>
    <tr>
      <td>81</td>
      <td>M6N</td>
      <td>York</td>
      <td>Runnymede, The Junction North</td>
    </tr>
    <tr>
      <td>82</td>
      <td>M6P</td>
      <td>West Toronto</td>
      <td>High Park, The Junction South</td>
    </tr>
    <tr>
      <td>83</td>
      <td>M6R</td>
      <td>West Toronto</td>
      <td>Parkdale, Roncesvalles</td>
    </tr>
    <tr>
      <td>84</td>
      <td>M6S</td>
      <td>West Toronto</td>
      <td>Runnymede, Swansea</td>
    </tr>
    <tr>
      <td>85</td>
      <td>M7A</td>
      <td>Downtown Toronto</td>
      <td>Queen's Park, Ontario Provincial Government</td>
    </tr>
    <tr>
      <td>86</td>
      <td>M7R</td>
      <td>Mississauga</td>
      <td>Canada Post Gateway Processing Centre</td>
    </tr>
    <tr>
      <td>87</td>
      <td>M7Y</td>
      <td>East Toronto</td>
      <td>Business reply mail Processing Centre, South C...</td>
    </tr>
    <tr>
      <td>88</td>
      <td>M8V</td>
      <td>Etobicoke</td>
      <td>New Toronto, Mimico South, Humber Bay Shores</td>
    </tr>
    <tr>
      <td>89</td>
      <td>M8W</td>
      <td>Etobicoke</td>
      <td>Alderwood, Long Branch</td>
    </tr>
    <tr>
      <td>90</td>
      <td>M8X</td>
      <td>Etobicoke</td>
      <td>The Kingsway, Montgomery Road, Old Mill North</td>
    </tr>
    <tr>
      <td>91</td>
      <td>M8Y</td>
      <td>Etobicoke</td>
      <td>Old Mill South, King's Mill Park, Sunnylea, Hu...</td>
    </tr>
    <tr>
      <td>92</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Mimico NW, The Queensway West, South of Bloor,...</td>
    </tr>
    <tr>
      <td>93</td>
      <td>M9A</td>
      <td>Etobicoke</td>
      <td>Islington Avenue, Humber Valley Village</td>
    </tr>
    <tr>
      <td>94</td>
      <td>M9B</td>
      <td>Etobicoke</td>
      <td>West Deane Park, Princess Gardens, Martin Grov...</td>
    </tr>
    <tr>
      <td>95</td>
      <td>M9C</td>
      <td>Etobicoke</td>
      <td>Eringate, Bloordale Gardens, Old Burnhamthorpe...</td>
    </tr>
    <tr>
      <td>96</td>
      <td>M9L</td>
      <td>North York</td>
      <td>Humber Summit</td>
    </tr>
    <tr>
      <td>97</td>
      <td>M9M</td>
      <td>North York</td>
      <td>Humberlea, Emery</td>
    </tr>
    <tr>
      <td>98</td>
      <td>M9N</td>
      <td>York</td>
      <td>Weston</td>
    </tr>
    <tr>
      <td>99</td>
      <td>M9P</td>
      <td>Etobicoke</td>
      <td>Westmount</td>
    </tr>
    <tr>
      <td>100</td>
      <td>M9R</td>
      <td>Etobicoke</td>
      <td>Kingsview Village, St. Phillips, Martin Grove ...</td>
    </tr>
    <tr>
      <td>101</td>
      <td>M9V</td>
      <td>Etobicoke</td>
      <td>South Steeles, Silverstone, Humbergate, Jamest...</td>
    </tr>
    <tr>
      <td>102</td>
      <td>M9W</td>
      <td>Etobicoke</td>
      <td>Northwest, West Humber - Clairville</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_pcn.shape
```




    (103, 3)




```python

df_geo = pd.read_csv('http://cocl.us/Geospatial_data')
df_geo.columns = ['Postcode', 'Latitude', 'Longitude']
```


```python
df_pos = pd.merge(df_pcn, df_geo, on=['Postcode'], how='inner')

df_tor = df_pos[['Borough', 'Neighbourhood', 'Postcode', 'Latitude', 'Longitude']].copy()

df_tor.head()
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
      <th>Borough</th>
      <th>Neighbourhood</th>
      <th>Postcode</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Scarborough</td>
      <td>Malvern, Rouge</td>
      <td>M1B</td>
      <td>43.806686</td>
      <td>-79.194353</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Scarborough</td>
      <td>Rouge Hill, Port Union, Highland Creek</td>
      <td>M1C</td>
      <td>43.784535</td>
      <td>-79.160497</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Scarborough</td>
      <td>Guildwood, Morningside, West Hill</td>
      <td>M1E</td>
      <td>43.763573</td>
      <td>-79.188711</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Scarborough</td>
      <td>Woburn</td>
      <td>M1G</td>
      <td>43.770992</td>
      <td>-79.216917</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
      <td>M1H</td>
      <td>43.773136</td>
      <td>-79.239476</td>
    </tr>
  </tbody>
</table>
</div>




```python

address = 'Toronto, Canada'

geolocator = Nominatim()
location = geolocator.geocode(address)
latitude = location.latitude
longitude = location.longitude
print('The geograpical coordinate of the City of Toronto are {}, {}.'.format(latitude, longitude))
```


    ---------------------------------------------------------------------------

    ConfigurationError                        Traceback (most recent call last)

    <ipython-input-14-972883036441> in <module>
          1 address = 'Toronto, Canada'
          2 
    ----> 3 geolocator = Nominatim()
          4 location = geolocator.geocode(address)
          5 latitude = location.latitude
    

    ~\Anaconda3\lib\site-packages\geopy\geocoders\nominatim.py in __init__(self, timeout, proxies, domain, scheme, user_agent, ssl_context, adapter_factory)
        112                 'overriding the default `user_agent`: '
        113                 '`geopy.geocoders.options.default_user_agent = "my-application"`.'
    --> 114                 % self.headers['User-Agent']
        115             )
        116 
    

    ConfigurationError: Using Nominatim with default or sample `user_agent` "geopy/2.0.0" is strongly discouraged, as it violates Nominatim's ToS https://operations.osmfoundation.org/policies/nominatim/ and may possibly cause 403 and 429 HTTP errors. Please specify a custom `user_agent` with `Nominatim(user_agent="my-application")` or by overriding the default `user_agent`: `geopy.geocoders.options.default_user_agent = "my-application"`.



```python
# create map of New York using latitude and longitude values
map_toronto = folium.Map(location=[latitude, longitude], zoom_start=10)

# add markers to map
for lat, lng, borough, neighborhood in zip(df_tor['Latitude'], df_tor['Longitude'], df_tor['Borough'], df_tor['Neighbourhood']):
    label = '{}, {}'.format(neighborhood, borough)
    label = folium.Popup(label, parse_html=True)
    folium.CircleMarker(
        [lat, lng],
        radius=3,
        popup=label,
        color='green',
        fill=True,
        fill_color='#3199cc',
        fill_opacity=0.3,
        parse_html=False).add_to(map_toronto)  
    
map_toronto
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-15-3f213e1abc04> in <module>
          1 # create map of New York using latitude and longitude values
    ----> 2 map_toronto = folium.Map(location=[latitude, longitude], zoom_start=10)
          3 
          4 # add markers to map
          5 for lat, lng, borough, neighborhood in zip(df_tor['Latitude'], df_tor['Longitude'], df_tor['Borough'], df_tor['Neighbourhood']):
    

    NameError: name 'latitude' is not defined



```python

```
