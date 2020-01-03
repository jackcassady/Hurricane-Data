# Hurricane-Data
Project to analyze data on hurricanes from 1899 to 2018.

## Data

I used the data in `hurricanes.csv` in order to complete the analysis. `hurricanes.csv` is a CSV file that contains information on hurricanes from 1899 to 2018, including data points such as: Name, Formation Date, Dissipation Date, Wind Speed, Value of Damage, and Number of deaths. There are 132 hurricanes in the dataset.

## Functions Used

Get month from a full date:

```python
def get_month(date):
    '''Returns the month when the date is the in the 'mm/dd/yyyy' format'''
    return int(date[:2])
```

Get day from full date:

```python
def get_day(date):
    '''Returns the day when the date is the in the 'mm/dd/yyyy' format'''
    return int(date[3:5])
```

Get year from full date:

```python
def get_year(date):
    '''Returns the year when the date is the in the 'mm/dd/yyyy' format'''
    return int(date[-4:])
```

Converting damage string to number:

```python
def cost(damage):
    if damage[-1] == 'K':
        return int(float(damage[:-1]) * 1000)
    elif damage[-1] == 'M':
        return int(float(damage[:-1]) * 1000000)
    elif damage[-1] == 'B':
        return int(float(damage[:-1]) * 1000000000)
```

Find deadliest hurricane in range of years:

```python
def deadliest_in_range(year1, year2):
    worst_idx = None
    for i in range(project.count()):
        year_i = get_year(project.get_formed(i))
        if year1 <= year_i <= year2:
            if worst_idx == None or project.get_deaths(i) > project.get_deaths(worst_idx):
                worst_idx = i
    return worst_idx
```

Find the number of hurricanes in a month:

```python
def hurricanes_in_month(mm):
    num_of_hurricanes = 0
    for i in range(project.count()):
        date = get_month(project.get_formed(i))
        if date == mm:
            num_of_hurricanes += 1
    return num_of_hurricanes
```

Find the number of hurricanes in a year:

```python
def hurricanes_in_year(year):
    num_of_hurricanes = 0
    for i in range(project.count()):
        date = get_year(project.get_formed(i))
        if date == year:
            num_of_hurricanes += 1
    return num_of_hurricanes
```

## Data Analysis

First, I wanted to find the hurricane with the highest wind speeds, I did this by creating a list of all wind speeds in `hurricanes.csv` and then finding the max of that list which was 190. Next to find the name of the hurricane with the highest wind speeds, looped through the data and found where mph was equal to 190 and returned the index, then using this index I could find the name of the hurricane at this index. 


Next, I wanted to find the damage caused by hurricane Dolphin. This was done by looping through the data to find where name is equal to `Dolphin` and then getting the damage from this index and converting it to a monetary value using the `cost` function from above. Thus I was able to find that hurricane Dolphin caused $13,500,000 worth of damage.


I then wanted to find the number of deaths caused by all hurricanes in `hurricanes.csv`. To do this, I looped through the data, looking for the number of deaths for each hurricane and adding that value to the total for all the hurricanes before it. This gave me a total of 18,959.


Using the `deadliest_in_range` function from above, I found that hurricane Maria was the most deadly from 2010 to 2019, Hurricane Inez was the most deadly in the 20th century and the most deadly hurricane in the dataset was formed in 1899.


The value of the damage done by hurricane Inez was also found to be $226,500,000 and the total damage of all hurricanes in the dataset were found to be $864,230,464,997


Lastly, I wanted to analyze when hurricanes occurred. Thus, I was able to use the `hurricanes_in_month` and `hurricanes_in_year` functions to get the number of hurricanes that occur in certain months or years. In the month of July, there were 17 hurricanes formed. In December and January, there were 3 hurricanes. In May, there were 2. The month that had the most hurricanes was September. Using the data, I was also able to find that there were 10 years with at least 4 hurricanes formed.  
