# Carlos Sanchez COP4045 Assignment 4
In this assignment we were asked to create a program were we will practice with lists, tuples, functions, and CSV file manipulationto perform basic queries and produce simple plots related to vehicle fuel consumption. we were asked to ask the user to pick between two options: 
1. ask the user for an interval of MPG to create a list from a CSV file.
2. ask the user for either (H)ighway MPG, (C)ity MPG or (O)verall MPG to display the graph or to save it as a .png file.

For this assigment I used examples from the book as a guide and changed them to get the desired output.

### For example 7.15 and option 1:
Instead of making two lists for Min() or Max() MPG, I created a single list that will take the data desired from the user interval and display it.
```python
    def find_max_min_mileage(mileage_list, max_mileage, min_mileage):
        max_min_mileage_list = []  # make a list of vehicles within interval
        # finds vehicles between interval
        for car_tuple in mileage_list:
            if max_mileage >= car_tuple[0] >= min_mileage:
                max_min_mileage_list.append(car_tuple)
        return max_min_mileage_list
```
### For example 7.18 and option 2:
in this part I used mostly the example showed in the lecture and modified it to being able to graph (H)ighway MPG, (C)ity MPG or (O)verall MPG, not just (H)ighway MPG as the class lecture.
```python
    if trend_option == "H":
        title = "Highway MPG"
        next(reader)
        for line_list in reader:
            try:
                year_list = int(line_list[0])
                x.append(year_list)
                highway_mpg_float = float(line_list[6])
                y.append(highway_mpg_float)
            except ValueError:
                break
    elif trend_option == "C":
        title = "City MPG"
        next(reader)
        for line_list in reader:
            try:
                year_list = int(line_list[0])
                x.append(year_list)
                highway_mpg_float = float(line_list[5])
                y.append(highway_mpg_float)
            except ValueError:
                break
    elif trend_option == "O":
        title = "OverallMPG"
        next(reader)
        for line_list in reader:
            try:
                year_list = int(line_list[0])
                x.append(year_list)
                highway_mpg_float = float(line_list[4])
                y.append(highway_mpg_float)
            except ValueError:
                break
```
"Title" helped me to change the name in the graph:
```python
    pylab.plot(x, y)
    pylab.ylabel(title)
    pylab.xlabel("Year")
    pylab.title("EPA annual average MPG data")
```
regarding the last line of years that we talked in lectured I used professor's recomendation:

```python
        for line_list in reader:
            try:
                year_list = int(line_list[0])
                x.append(year_list)
                highway_mpg_float = float(line_list[6])
                y.append(highway_mpg_float)
            except ValueError:
                break
```