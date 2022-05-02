# Challenge 6

## Housing in San Francisco
---
***Library Imports Needed***

* import pandas as pd
* import hvplot.pandas
* from pathlib import Path
* from bokeh.models import HoverTools (optional - to change the scientific notation on geo map)

***Analysis***


To analyze the San Francisco's sale price per sq/ft and the gross rent for the years 2010-2016 we  the census csv file was used. 

With the provided data, I was able to create a DataFrame and a graph to visualize the data and get a better understanding.

The DataFrame was grouped by year using the following code:
```python
housing_units_by_year = sfo_data_df.groupby('year').mean('housing_units')
```

The data was visualized as a bar graph as follows
```python
housing_units_by_year.hvplot.bar(x='year',
                                 y='housing_units',
                                 title='San Francisco Housing 2010-2016',
                                 rot=90,
                                 color='blue',
                                 hover_color='orange',
                                 frame_width=500,
                                 frame_height=200,
                                 ylim=(365000,385000)).opts(yformatter='%.0f')
```
producing the below:

![zoomed-housing-units-by-year](Images/zoomed-housing-units-by-year.png)


The data was further filtered and combined with a csv file that had the longitude and latitude for the neighborhoods in SF for the purpose of visualizing the data in a geographical view. The neighborhoods with the no data in regards to sale price per sq/ft and gross rents were dropped, and the averages were calculated using the `.mean()` function.

The resulting geographical visualization was as follows:
![geoview-san-fran-plot](images/6-4-geoviews-plot.png)