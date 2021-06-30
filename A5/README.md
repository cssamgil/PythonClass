# Carlos Sanchez COP4045 Assignment 5

In thin this assignment we were asked to create a simple program using dictionaries to store and process the contents of a very popular dataset, the Iris flower dataset.

I divided this program into 4:

- **read:** This part is in charge of reading the .csv file

```python
epa_file = open("iris.csv", "r",encoding="windows-1252")
reader = csv.reader(epa_file)
read = epa_file.readline().rstrip('\n') #skips first row 
for row in reader:
  rows.append(row)
```

- **Pretty print:** This part will print a pretty outcome to the user. I used examples to get closer to the outcome posted on the assignment.

```python
def prettyPrint(d:dict):
  print("This program computes summary statistics for the Iris Dataset")
  print("-----------------------------------------------------------------------")
  word_list = d.keys()
  print("{:27s}".format("Species:"), end="")
  for w in word_list:
      print("{:15s}".format(w), end="")
  print()
  print("-----------------------------------------------------------------------")
  print("Attributes (cm): ")
  
  fields = ["Avg Petal length:","Avg Petal width:","Avg Sepal length:","Avg Sepal width:"]
    #Prints
  for i in range(4):
      print("{:18s}".format(fields[i]),end="")
      print("{:15.2f}".format(d["Setosa"][i]),end="")
      print("{:15.2f}".format(d["Versicolor"][i]),end="")
      print("{:15.2f}".format(d["Virginica"][i]),end="")
      print()
```

- **Lists and Dictionary:** we were asked to Create a dictionary with the key as the species name and the values as(placeholders for)the averages of eachof the four attributes/features of each data point: petal length, petal width, sepal length, and sepal width.

```python
#Lists
setosa_list = []
versicolor_list = []
virginica_list = []
#fill the list 
for row in rows:
    temp_lista = row
    if "setosa" in temp_lista:
        setosa_list.append([float(i) for i in temp_lista[:-1]])
    elif "versicolor" in temp_lista:
        versicolor_list.append([float(i) for i in temp_lista[:-1]])
    else:
        virginica_list.append([float(i) for i in temp_lista[:-1]])
      
#Create dictionary 
iris = {}
iris["Setosa"] = average(setosa_list)
iris["Versicolor"] = average(versicolor_list)
iris["Virginica"] = average(virginica_list)
#Prints
prettyPrint(iris)

```
- **Find Average: **  this part will calculate and return the averages of the columns 

```python
def average(l:list):
  sepalLength = []
  sepalwidth = []
  petalLength = []
  petalwidth = []
  for lista in l:
      sepalLength.append(float(lista[0]))
      sepalwidth.append(float(lista[1]))
      petalLength.append(float(lista[2]))
      petalwidth.append(float(lista[3]))
  
  return [sum(petalLength)/len(petalLength), sum(petalwidth)/len(petalwidth), sum(sepalLength)/len(sepalLength), sum(sepalwidth)/len(sepalwidth)]
```
