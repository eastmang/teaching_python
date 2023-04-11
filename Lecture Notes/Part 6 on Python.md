# Part 6: plots

## --- Matplotlib ---
Advantage: Very customizeable but more complicated to implement

import matplotlib.pyplot as plt
<br /> 
df_data['Year'] = pd.qcut(df_data[NA_sales'],4)


We are going to make a histogram of north american sales. Since the data is extremely skewed we will take the log (sales are usually skewed).
Additionally since we have the option we will look at the density of observations. So instead of the counts
which are large we view the proportion. There is no correct way to do this, its more art than data science. 
 
plt.hist(new_dat['NA_sales'], density = True, log = True)
<br /> 
plt.ylabel('counts')
<br /> 
plt.xlabel('Year')
<br /> 
plt.show()


Now we will look at a simple scatter plot between NA_sales and EU_sales

plt.scatter(new_dat['NA_sales'], new_dat['EU_sales'])
<br /> 
plt.xlabel('NA_sales')
<br /> 
plt.ylabel('EU_sales')
<br /> 
plt.show()


Just as in the previous we specified the x and y labels, we could also do things for the
title, number of plots to show, size of the tick marks, rotation of the lettering, etc. These
are all documented in matplot lib. There are more than we can explore here. 

## --- Seaborn ---
import seaborn as sns

Advantage: It is simple to use and looks nice with its basic designs but is not as customizeable

__Histogram__ 
<br /> 
sns.histplot(data = new_dat, x = 'EU_sales', log_scale = True, color = 'darkred', bins = 10)


I think seaborn usually looks nicer and is simpler to run.
It is a little less customizeable. I think seaborn and matplotlib can actually work together,
although it has been a while since I have worked with both at once


__Scatter Plot__
<br /> 
sns.scatterplot(data = new_dat, x = 'EU_sales', y = 'NA_sales', color = 'darkred')




## --- Plotly ---
import plotly.express as px
<br /> 
import plotly.graph_objects as go


Advantage: you can see information on the data when you highlight the graphs and is pretty customizeable and easy to make

__Histogram__ 
<br />
fig = px.histogram(new_dat, x='NA_sales', labels = {'NA_sales' : 'NA_sales'}, title = """Number {} Histogram""".format(2), log_y = True, nbins = 14)
<br /> 
fig.show()

This makes a histogram with the labels and title. Plotly is fantastic because you can view details about the data in the plots. I
would highly suggest it. 

__Scatter Plot__
<br />
fig = px.scatter(new_dat, x='NA_sales', y = 'EU_sales', labels = {'NA_sales' : 'NA_sales'}, title = """Number {} Histogram""".format(2))
<br /> 
fig.show()