Part 1:

Python is the default language but in practice the tools we use are largely from imported packages. 
Best practice is to import all packages at the top, instead of as you need them. 
You can also import specific parts of packages. 

IE. 
import numpy as np
from keras.layers import Layer

Now lets talk about the data we can store in python. 


Data Storage- 
	. Python uses dictionaries, they are unordered and elements are accessed via keys. The keys can be any type. 
	. Python uses lists, this is memory intensive but allows for storing multiple data types and the list can grow or shrink as needed.	
	. Python uses tuples, this is an ordered colelction of variables but it is immutable AKA the size is fixed. 
	. NumPy uses arrays, this is memory efficient but can only handle one data type and is not flexible since elements are explicitely ordered.
	. Pandas uses series, this is like a numpy array but it is explicitely indexed instead of implicitly. 
	. Pandas uses a dataframe, this is a set of series, each one being a column.This is probably what we will work with the most.
Not really covered in what we are doing but
	. PySpark uses its own dataframe which is like a columnar table in sql
	. PySpark also uses RDD's which does not format data in a column type. This is usually used for unstructured data or data engineers. 

Pyspark dataframes are actually built on top of RDDs so you can swap between them with simple calls. RDD manipulation is a good tool
for quickly manipulating lots of data, but doing so requires understanding of the underlying data and more advanced pyspark knowledge than 
we will look into. 



Small Python Quirks:
Python determines order and loops by indentation. Indents indicate something is within a loop. It does not use parentheses like in SAS
This helps the code look more readable, but also you need to be diligient that indents are correct. Also the \ character will allow you discontinue
a line and pick it up on the next line. There can be no characters, not even a space after the \ or the command will fail. 

Functions can take in any variable type. This is good because you dont have to specify int or double, but you need to make sure that you are not allowing
invalid types to be passed since there will not be an error if a string is passed to a function that should only work with integers. 

You can add strings and same types together. "Hello" + " " + "World" will become "Hello World"

You can loop through items in a list. So if I have a list called loop_arr = [1, 2, 4, 8] then

for loop in loop_arr:
	print(loop)
	print('\n')

We will get:
1
2
4
8



Syntax:

The # starts a line comment

"""comment here""" is how you do a blocked comment/string

You can insert variables into strings in 2 ways:
var = 'string'
f"""This is a format {var}.""" will become, This is a format string. Which it is.

Or

"""This is a format {}""".format(var) will become, This is a format string. Which it is.


This is how you define a function
If you do not specify a return it will return a None value
def function_name(input_value):
	# contents of the function
	return the_thing_to_return

You can loop over lists or a set of objects without having to define the loop yourself
for loop_variable in object_to_loop_over:
	loop contents

While loops are just normal while loops done with indentation
While item_1 conditional item_2:
	loop contents

Conditional order goes, if -> elif (which is else if) -> else
if conditional:
	if contents
elif conditional:
	else if contents	
else: 
	else contents

(lambda val: operations)
lambda functions are quick functions usually done for a one off purpose but that you dont want to go and define a whole new function, or that you can define for just within another function

accessing the index of an arrary arr is arr[index_value]
