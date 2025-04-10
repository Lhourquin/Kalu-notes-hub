# SQL

## Flat-File Database

* As you have liekely seen beofre, data can often be described in patterns of columns and rows.
* Spreadsheets like those created in Microsoft Excel and Google Sheets can be outputted to a `csv` or *comma-separated values* file.
* If you look at a `csv` file, you'll notice that the file is flat in that all of our data is stored in a signle table represented by  a text file. We call this form of data a *flat-file database*
* With a file `favotrites.csv`, we write a python script to read line of the file of tat file as follows:

```python
# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.reader(file)

    # File header row
    next(reader)

    # Iterate over CSV file, printing each favorite
    for row in reader:
        print(row[1])

```

Notice that the `csv` library is imported. Further, we created a `reader` that will hold the result of `csv.reader(file)` The `csv.reader` function reads each row from the file, and in our code we store the results in `reader`. `print(row[1])`, therefore, will print the language form the `favorites.csv`.

* You can improve your code as follows:

```python
# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.reader(file)

    # File header row
    next(reader)

    # Iterate over CSV file, printing each favorite
    for row in reader:
        favorite = row[1]
        print(favorite)
```

Notice that `favorite` is stored and then printed. Also notice that we use the `next` function to skip to the next line of our reader.

* One of the disadvantages of the above approach is that we are trusting that `row[1]` is always the favorite. However, what would happen if the colums have been moved around?
* We can fix this potential issue. Python aslo allows you to inedx by keys of a list. Modify your code as follows:

```python
# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.DictReader(file)

    # Iterate over CSV file, printing each favorite
    for row in reader:
        favorite = row["language"]
        print(favorite)
```

Notice that this example directly utilizes the `language` key in the print statement.

* This could be further simplified to:

```python
# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.DictReader(file)

    # Iterate over CSV file, printing each favorite
    for row in reader:
        print(row["language"])
```

* To count the number of favorite languages expressed in the `csv` file, we can do the following:

```python
# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.DictReader(file)

    # Iterate over CSV file, printing each favorite
    for row in reader:
        print(row["language"])
```

Notice that each language is counted using `if` statements. Further notice the double equal `==` signs in those `if` statements.

* Python allows us to use a dictionary to count the `counts` of each language. Consider the following improvement upon our code:

```python
# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.DictReader(file)

    # Counts
    counts = {}
    
    # Iterate over CSV file, printing each favorite
    for row in reader:
        favorite = row["language"]
        if favorite in counts:
            counts[favorite] += 1
        else:
            counts[favorite] = 1

# Print counts
for favorite in counts:
    print(f"{favorite}: {counts[favorite]}")
```

Notice that the value in `counts` with the key `favorite` is incremented when it exists already. If it does not exist, we define `counts[favorite]` and set it to 1. Further, the formatted string has been improved to present the `counts[favorite]`.

* Python also allows sorting `counts`. Improve your code as follows:

```Python

# Prints all favorites in CSV using csv.reader

import csv

# Open CSV file
with open("favorites.csv", "r") as file:

    # Create reader
    reader = csv.DictReader(file)

    # Counts
    counts = {}
    
    # Iterate over CSV file, printing each favorite
    for row in reader:
        favorite = row["language"]
        if favorite in counts:
            counts[favorite] += 1
        else:
            counts[favorite] = 1

# Print counts
for favorite in sorted(counts):
    print(f"{favorite}: {counts[favorite]}")

```

Notice the `sorted(counts)` at the botoom of code. It sorted by alphabet.

* If you look at the parameters for the `sorted` function in the Python documenttation, you will find it has many built-in parameters. You can leverage some of these built-in parameters as follows:

```python
# Prints all favorites in CSV using csv.reader

import csv

# open csv file
with open("favorites.csv", "r") as file:

    # create reader
    reader = csv.DictReader(file)

    # counts
    counts = {}
    
    # iterate over csv file, printing each favorite
    for row in reader:
        favorite = row["language"]
        if favorite in counts:
            counts[favorite] += 1
        else:
            counts[favorite] = 1

# print counts
for favorite in sorted(counts, key=counts.get, reverse=true):
    print(f"{favorite}: {counts[favorite]}")
```

Notice the arguments passed to `sorted`. The `key` argument allows you to tell Python the method you wish to use to sort items. In this case `counts.get` is used to sort by the values. `reverse=True` tells `sorted` to sort from largest to smallest.

* Python has numerous libraries that we can utilize in our code. One of these libraries is `collections`, from which we can import `Counter`. `Counter` will allow you to access the counts of each language without the headaches of all the `if` statements seen in our previous code. You can implement as follows:

```Python
# Prints all favorites in CSV using csv.reader

import csv

from collections import Counter

# open csv file
with open("favorites.csv", "r") as file:

    # create reader
    reader = csv.DictReader(file)

    # counts
    counts = Counter()
    
    # iterate over csv file, printing each favorite
    for row in reader:
        favorite = row["language"]
        counts[favorite] += 1

# print counts
for favorite in counts.most_common():
    print(f"{favorite}: {counts[favorite]}")
```

Notice how `counts = Counter()` enables the use of this imported `Counter` class from `Collections`.

* We can change the column we are examining, focusing on our favorite problem instead:

```Python
# Prints all favorites in CSV using csv.reader

import csv

from collections import Counter

# open csv file
with open("favorites.csv", "r") as file:

    # create reader
    reader = csv.DictReader(file)

    # counts
    counts = Counter()
    
    # iterate over csv file, printing each favorite
    for row in reader:
        favorite = row["problem"]
        counts[favorite] += 1

# print counts
for favorite in counts.most_common():
    print(f"{favorite}: {counts[favorite]}")
```

Notice that `problem` replaced `language`.

* We can also get the count of the popularity of a specific problem in the course:

```Python
# Prints all favorites in CSV using csv.reader

import csv

from collections import Counter

# open csv file
with open("favorites.csv", "r") as file:

    # create reader
    reader = csv.DictReader(file)

    # counts
    counts = Counter()
    
    # iterate over csv file, printing each favorite
    for row in reader:
        favorite = row["problem"]
        counts[favorite] += 1

# print counts
favorite = input("Favorite: ")
print(f"{favorite}: {counts[favorite]}")
```

Notice how compact our code is compared to our experience in C.

## Relational Databases

* Google, Twitter, and Meta all use relational databses to store their information at scale.
* Relational databases store data in rows and columns in structures called *tables*
* SQL allows for four types of commands:

```
Create 
Read 
Update 
Delete 
```

* These four operationare affectionately called *CRUD*
* We can create a SQL database at the terminal by typing `sqlite3 favorites.db`. Upon being prompted, we will agree that we want to create `favorites.db` by pressing `y`.
* You will notice a different prompt as we are now inside a program called `sqlite3`.
* We can put `sqlite3` into `csv` mode by typing `.mode csv`. Then, we can import our data from our `csv` file by typing `.import favorites.csv`. It seems that nothing has happened!
* We can type `.schema` to see the structure of these database.
* you can read items form a table using the syntax `SELECT columns FROM table`.
* For example, you can type `SELECT * FROM favorites;` which will iterate every row in `favorites`.
* You can get a subset of the data using the command `SELECT language FROM favorites;`.
* SQL supports many commands to access data, including:

```
AVG
COUNT 
DISTINCT 
LOWER 
MAX 
MIN 
UPPER
```

* For example, you can type `SELECT COUNT(language) FROM favorites;`. Further, you can type `SELECT DISTINCT(language) FROM favorites;` to get a list of the individual languages within the database. You could even type `SELECT COUNT(DISTINCT(languages)) FROM favorites;` to get a count of those.
* SQL offers additional commands we can utilize in our queries:

```
WHERE -- adding a Boolean expression to filter our data
LIKE -- filtering responses more loosely
ORDER BY --ordering responses
LIMIT -- limiting the number of responses
GROUP BY -- grouping responses together
```

Notice that `--` to write a comment in SQL.

* For example, we can execute `SELECT COUNT(*) FROM favorites WHERE language = 'C'`. A count is presented.
* Further, we could type `SELECT language COUNT(*) FROM favorites WHERE language = 'C' AND problem = 'Hello, World';`. Notice how the `AND` is utilized to narrow our results.
* Similarly, we could execute `SELECT language, COUNT(*) FROM favorites GROUP BY language;`. This would offer a temporary table that would show the language and count.
* We could improve this by typing `SELECT language, COUNT(*) FROM favorites GROUP BY language ORDER BY COUNT(*)`. This will order the resuilting table by the `count`.
* We can also INSERT into a SQL database utilizing the form INSERT INTO table (column...) VALUES(value, ...);.
* We can execute INSERT INTO favorites (language, problem) VALUES ('SQL', 'Fiftyville');.
* DELETE allows you to delete parts of your data. For example, you could DELETE FROM favorites WHERE Timestamp IS NULL;.
* We can also utilize the UPDATE command to update your data.
* For example, you can execute UPDATE favorites SET language = 'SQL', problem = 'Fiftyville';. This will result in overwriting all previous statements where C was the favorite programming language.
* Notice that these queries have immense power. Accordingly, in the real-world setting, you should consider who has permissions to execute certain commands.

## Shows

* We can imagine a database that we might want to create to catalog various TV shows. We could create a spreadsheet with columns like `title`, `star`,`star`,`star`,`star`, and more stars. A problem with this approach is this approach has a lot of wasted space. Some shows may have one star. Others may have dozens.
* We could separate our database into multiple sheets. We could have a `shows` sheet and a `people` sheet. On the `people` sheet, each person could have a unique `id`. On the `shows` sheet and a `people` sheet. On `id`, too. On a third sheet called `stars` we could relate how each show has people for each show by having a `show_id` and `person_id`. while this is an improvement, this is not an ideal database.
* IMDb offers a databases of people, shows, writers, stars, genres, and ratings. Each of these tables is related to one another as follows:

![diagram](img/diagram-db.png )
