# Part 3: Dates and Strings


## --- Dates and Times ---
import datetime as dt
import pandas as pd

The datetime package is used to deal with well... dates and times
This is useful for individual values, if you have to loop over a list of  
values, or build your own function. 
Although, pandas has a way to parse them without needing the datetime package.

df['date'] = pd.to_datetime(df['date'], format = "%Y-%m-%d)
<br />
The formats are %y = year, %m = month, %d = day, %H = hour, %M = minute, %S = second

We can also infer the date formats. This command is usually pretty good, but its like autocorrect,
accurate enough you want to use it, but not accurate to really trust it. So I would not use this
in production, set the times yourself to be sure.
<br />
pd.to_datetime(df['date'], infer_datetime_format = True)


Now lets say you have dates but want the year, month, and day as columns
<br />
df['year'] = df['date'].dt.year
<br />
df['month'] = df['month'].dt.month
<br />
df['day'] = df['day'].dt.day


Maybe we care more about the week of the year so we can do timeseries modeling.
<br />
df['week'] = df['date'].dt.week


There are a variety of other functions than just looking at the times of course, looking up the datetime package
can show you options, or a better way might be to go over practice questions and things you are curious about
and just seeing what can be done with them.

## --- Strings ---

Lets cast to lower case, upper case, and get the length of each string
<br />
df['lower'] = df['string_col'].str.lower()
<br />
df['upper'] = df['string_col'].str.upper()
<br />
df['str_len'] = df['string_col'].str.len()  

Now we will strip strings. I have found this to be very important. This
function removes leading and trailing whitespace (only leading and trailing). Often times
the extra white space can cause encoding errors or a variery of other issues.
<br />
df['no_extra_white_space'] = df['string_col'].str.strip()


Lets say there is a character we dont want in our string, we can remove it with a replace of nothing.
<br />
df['removed_char'] = df['string_col'].str.repalce("@", "")

we have replaced the @ symbol with nothing, but we can replace it with anything. For example,
some dates are using a '/' and some are using a '-' and we want them to use a single format so we can make them a datetime
df['no_slash'] = df['string_col'].str.replace("/", "-")


We can link these commands together like
<br />
df['no_slash'] = df['string_col'].str.strip().str.replace("/", "-")

There are a lot of things you can do with stings, like looping over the characters
<br />
for i in "Hello":
<br />
print(i)

Will return
<br />
H
<br />
e<br />
l<br />
l<br />
o
<br />

Sometimes we need very specific string commands and these are provided with the re package. I am not going to 
go over regular expressions here in depth, if you know them then the package should be intuitive, it you do not we can 
cover it at another time. To access the package you can just
<br />
import re