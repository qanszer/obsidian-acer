
2025-09-16  15:45

Tags: [[Python]] [[Coding]] 

# Python Cheat Sheet


METHODS

.title()
output: "Sample Output"

.upper()
ouput: "SAMPLE OUTPUT"

.lower()
output: "sample output"

.strip()
output: "sampleoutput"

.rstrip or .lstrip
- right of left whitespace removed

"https://sample"
.removeprefix('https://')
output: "sample"


```python
input = 5  # single value

list = [] # list - ordered, mutable, allows duplicates, allows all data types
list(0) # select element
list(0) = 3 # modify selected element
list.append(6) # insert at the end
list.extend([8,9]) # insert multiple values at the end
list.insert(0,0) # insert at the front; (0=value, 0=index)
list.remove(5) # removes element by value; only removes 1st occurence if there are duplicates
del list[0] # removes element by index
list.clear() # removes all elements
x = list.pop() # gets last index
y = len(list) # gets total number of char
nested_list = [[1,2,3], ["a","b"],[True,False]]
exponent = [x**2 for x in range(1,6)] # populates list using loop
print(exponent) # [1,4,9,16,25]

add_list = [11,12]
indeces_list = [4,5]
for index,value in enumerate(add_list):
	list.insert(value, indeces_list[index])


tuple = () # tuple - ordered, immutable, allows duplicates
set = {} # set - unordered, mutable, no duplicates
```


![[Pasted image 20251014171317.png]]

![[Pasted image 20251014171345.png]]

![[Pasted image 20251014171415.png]]

![[Pasted image 20251014174446.png]]





# References