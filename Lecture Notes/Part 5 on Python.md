# Part 5: Dictionaries, Loops, and Functions

## --- Dictionaries ---
We talked about this in part 1, this is a base python data type.
These are great ways to store arbitrary information. In our work it is usually used for dataframes, plots, or other odds and ends. 

__Making an empty dictionary__
<br />
dict = {} 

__Adding new information__
<br />
We use a similar method as with pandas dataframes.
<br />
key_name = 'initial_key'
<br />
dict[key_name] = df

The key_name refers to the key in the dictionary used to look up the information (the dataframe).
You do not need to save the string to a variable name I usually do for these things and I will go into why later.
So if we want to see the first 10 rows of the dataframe in this dictionary we could say
<br />
dict[key_name].head()


__Storing maps and plots__
<br />
Lets say we have a plot called cluster_map
<br />
map_name = 'cluster_map'
<br />
dict[map_name] = cluster_geo_plot

We can then see the map by simply calling
<br />
dict[map_name].show()

## --- Loops ---
We have gone through "for loops" and "while loops" and all of that but not incorporated them in data usage.
It is not uncommon to want to loop through a process and apply the same thing to multiple dataframes.


Remember in python we can loop through lists
<br />
for k in ['element_1', 'element_2']:
<br />
&emsp;	print(k)

that will evaluate to printing
<br />
'element_1'
<br />
'element_2'

Lets say we have a dictionary of dataframes, each with different levels of aggregation
<br />
keys = ['df1', 'df2']
<br />
dict['df1'] = df1
<br />
dict['df2'] = df2

We want to apply some steps to both of these
<br />
for k in keys:
<br />
&emsp;	dict[k] = dict[k].groupby(by = k).aggregate({'EU_sales': 'sum', 'NA_sales' : 'sum'})

This step will be applied to all of the dataframes in the dictionary

__Viewing Keys__
<br />
dict.keys()

__Removing an entry__ 
<br />
del dict['element_1']

__Clearing the dictionary__
<br />
dict.clear()

##--- Fucntions ---
We then often incorporate functions with these

def insert_ones(data_dict, key_list):
<br />
&emsp;	for k in key_list:
<br />
&emsp;		data_dict[k] = data_dict[k].insert(0, 'ones', 1)
<br />
&emsp;	return data_dict

Usually when complex operations are done I see people save each dataframe from the dictionary to a local name before operating on it but you dont have to.

The following function is similar to the previous but with one important difference, it allows you to input any keys that you want instead of only using the ones defined in the function.
<br />
def group_by_input_keys(data_frame, keys):
<br />
&emsp;  loop_dictionary = {}
<br />
 &emsp; for k in keys:
<br />
&emsp;&emsp;   loop_dictionary[k] =  df.groupby(by = k).aggregate({'NA_sales': 'sum', 'EU_sales' : 'sum'})
    
&emsp;  return loop_dictionary

key_names = ['Platform', 'Publisher', 'Genre']
<br />
final_grouped_dict = group_by_input_keys(df, key_names)

This next function uses a generic property of python functions. This is similar to the previous function but with one important difference. We have added a default to the keys. So if nothing is passed for the key names, we instead use the default. When we pass an argument for keys it superscedes the keys default values

def group_by_input_keys_with_default(data_frame, keys = ['Publisher', 'Platform']):
<br />
&emsp;  loop_dictionary = {}
<br />
&emsp;  for k in keys:
<br />
&emsp;&emsp;    loop_dictionary[k] =  df.groupby(by = k).aggregate({'NA_sales': 'sum', 'EU_sales' : 'sum'})
<br /> 
&emsp;  return loop_dictionary

key_names = ['Platform', 'Publisher', 'Genre']
<br /> 
default_function_dictionary = group_by_input_keys_with_default(df)