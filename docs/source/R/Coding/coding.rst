Variables
===========

The first concept we will cover are **variables**. Variables are placeholders for a quantity that may change, or any mathematical object. In particular, a variable may represent a number, a vector, a matrix, a function, the list goes on.

To assign a variable in R, you can use the ``<-`` notation or ``=`` notation. 

In the code block below, we create the **string** ``"Hello World"`` and assign it to the variable ``greeting``. 

.. code-block:: r

    greeting <- "Hello World"

To print the contents of the variable ``greeting``, you can use the ``print`` function:

.. code-block:: r

    print(greeting)

.. code-block:: console

    [1] "Hello World"

Notice how the variable has been stored in our environment (the upper right box in RStudio) as a value.

As previously mentioned, variables are placholders and as such, can be overwritten and modified. 

Change the ``greeting`` variable to hold the string ``"Hello user"`` and print the contents:

.. code-block:: r

    greeting <- "Hello user"
    print(greeting)

Note the environment variable has been updated to reflect this change. 

Calculations
============

R is a statistical computing software and at it's core, an oversided calculator.

R performs addition, subtraction, multiplication, division, exponentiation and modulo with ``* - + / ^ %%``.

.. code-block:: r

    1 + 4
    10 - 1
    12 * 3
    1 / 6
    2 ^ 6
    3 %% 9

.. code-block:: console

    [1] 5
    [2] 9
    [3] 36
    [4] 0.16666666666666666
    [5] 64
    [6] 3

It is common practice to store the results of a calculation in a variable:

.. code-block:: r

    x <- 1 + 4
    print(x)

.. code-block:: console

    [1] 5

Vectors
=======

Vectors are a collection of the same data type. **Be careful not to mix data types in a vector!**.

.. attention::

    Data types help R interpret our code inputs. For example, anything surrounded in double quotes is interpreted as a **character string**. Integers and floats are interpeted as **numerics** which we can perform mathematical operations on. ``TRUE / FALSE`` statements are known as **Booleans**.

To initialise a vector, we use the ``c`` function - which stands for concatenate - with parentheses. 

Below we will create two vectors:

.. code-block:: r

    racing_number <- c(33, 44, 11, 4 , 3)
    driver_names <- c("Verstappen", "Hamilton", "Perez", "Norris", "Riccardo")

Named Vectors
-------------

We can use the ``driver_names`` vector variable to assign names to the ``racing_number`` vector using the ``names()`` function. Store the ``racing_number`` variable as ``drivers`` to avoid confusion!

.. code-block:: r

    names(racing_number) <- driver_names
    drivers <- racing_number
    print(drivers)

.. code-block:: console

    Verstappen   Hamilton      Perez     Norris   Riccardo 
        33         44         11          4          3 

Manipulating Vectors
--------------------

Let's update our previous vectors to include two new drivers and their racing numbers:

.. code-block:: r

    racing_number <- c(racing_number, 16, 24)
    driver_names <- c(drivers, "Leclerc", "Zhou")
    names(racing_number) <- driver_names
    drivers <- racing_number
    print(drivers)

.. code-block:: console

    Verstappen   Hamilton      Perez     Norris   Riccardo    Leclerc       Zhou 
        33          44          11         4         3           16          24 

Before showing you how to delete items from a vector, we need to cover vector **indexing**. Indexing allows us to access specific items in a vector.

In the example below, we will access the first, last and 2nd to 4th drivers in our vector:

.. code-block:: r

    drivers[1]
    drivers[7]
    drivers[2:4]

.. code-block:: R

    Verstappen 
        33 

    Zhou
     24

    Hamilton    Perez   Norris 
        44       11        4

.. note::

    Instead of ``drivers[7]`` we could use ``drivers(length(drivers))`` to access the last element in the vector. This saves you having to count the items manually and is programatically robust to future changes to the vector.

To delete an item from the vector, we place a minus infront of the corresponding index we want to drop.

Drop Lewis Hamilton from our ``drivers`` vector. Don't forget to assign the operation to the ``drivers`` variable if you want to save the changes. 

.. code-block:: r

    drivers[-2]

.. code-block:: console

    Verstappen      Perez     Norris   Riccardo    Leclerc       Zhou 
        33           11         4         3           16          24 

Lists
=====

Lists can be used to store mutliple vectors in a single data structure. We can name the vectors in the list, adding another element to this data structure.


To amuse myself, we will continue with the Formula 1 and create a **named list** attributing four driver pairings to their respective teams. 

.. code-block:: R

    F1_teams <- list(Scuderia_Ferrari=c("Charles Leclerc", "Carlos Sainz"),
                     Scuderia_Alpha_Tauri_Honda=c("Pierre Gasly", "Yuki Tsunoda"),
                     Alfa_Romeo_Racing_ORLEN=c("Valterri Bottas", "Guanyu Zhou"),
                     URALKALI_HASS_F1_Team=c("Mick Schumacher", "Nikita Mazepin"))

Constructing a list is simple - just assign multiple vectors (e.g ``Scuderia_Ferrari=c("Charles Leclerc", "Carlos Sainz")`` - each separated by a comma. 

The benefit of lists like these are that you can easily access items in the list using human readable names instead of numerical indexes (which still work!).

Below are a few examples of how to access the Ferrari drivers:

.. code-block:: R

    F1_teams$Scuderia_Ferrari
    F1_teams[1]
    F1_teams["Scuderia_Ferrari"]

These all achieve the same result. If you want to find out who the number 2 driver at HAAS is, apply the same logic used in vector indexing:

.. code-block:: R

    F1_teams$URALKALI_HASS_F1_Team[2]

.. code-block:: R

    "Nikita Mazepin"

Dataframes
==========

Dataframes are a superior method to lists for storing multiple vectors. Typically, each row in a dataframe corresponds to an observation (person, event, sample), whilst columns correspond to the variable being recorded (e.g height, age, eye color).

.. figure:: /_static/images/tidy-1.png
   :figwidth: 700px
   :target: /_static/images/tidy-1.png
   :align: center

|

Go to RStudio Cloud and open your session. Load in the ``Iris`` dataset:

.. code-block:: R

    iris <- datasets::iris

You can see a newly created 'Data' object in your environment called ``iris`` with ``150 obs of 5 variables``. That is to say we have 150 rows and 5 columns. 

Colnames & Rownames
-------------------

A simple rule applies to ``colnames`` and ``rownames``: **they must be unique**. This is because R uses both ``colnames`` and ``rownames`` to index each column and row respectively, duplicate entries are not allowed. 

Inspect the column names and row names of a dataframe:

.. code-block:: r

    colnames(iris)
    rownames(iris)

.. code-block:: console

      [1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"     

      [1] "1"   "2"   "3"   "4"   "5"   "6"   "7"   "8"   "9"   "10"  "11"  "12"  "13"  "14"  "15"  "16"  "17"  "18"  "19" 
     [20] "20"  "21"  "22"  "23"  "24"  "25"  "26"  "27"  "28"  "29"  "30"  "31"  "32"  "33"  "34"  "35"  "36"  "37"  "38" 
     [39] "39"  "40"  "41"  "42"  "43"  "44"  "45"  "46"  "47"  "48"  "49"  "50"  "51"  "52"  "53"  "54"  "55"  "56"  "57" 
     [58] "58"  "59"  "60"  "61"  "62"  "63"  "64"  "65"  "66"  "67"  "68"  "69"  "70"  "71"  "72"  "73"  "74"  "75"  "76" 
     [77] "77"  "78"  "79"  "80"  "81"  "82"  "83"  "84"  "85"  "86"  "87"  "88"  "89"  "90"  "91"  "92"  "93"  "94"  "95" 
     [96] "96"  "97"  "98"  "99"  "100" "101" "102" "103" "104" "105" "106" "107" "108" "109" "110" "111" "112" "113" "114"
    [115] "115" "116" "117" "118" "119" "120" "121" "122" "123" "124" "125" "126" "127" "128" "129" "130" "131" "132" "133"
    [134] "134" "135" "136" "137" "138" "139" "140" "141" "142" "143" "144" "145" "146" "147" "148" "149" "150"

Note that the rownames in this dataset are not important, they are just automatically incremented integers.

Dataframe Indexes
-----------------

There are situations where we will need to isolate columns or rows for an analysis. The same numerical indexing logic from vectors applies, but there are **two entries to the square brackets** - one for rows, and one for columns. 

.. figure:: /_static/images/slicingDataFrames.png
   :figwidth: 700px
   :target: /_static/images/slicingDataFrames.png
   :align: center

|

Like lists, we can provide human readable names to access a specific column: ``iris$Sepal.Width``.

Subsetting Dataframes
---------------------

Now that we know how to isolate specific cells of a dataframe, the next step is to apply these changes by 'slicing the dataframe'. Slicing a subsetting are interchangeable - I will nearly always call it subsetting. 

In our ``Iris`` dataset, make a new dataframe that contains only numerical measurements for ``Petals``:

.. code-block:: R

    petal_data <- iris[, 3:4]

Now make a dataframe that contains only the numerical observations (i.e drop the column ``species``):

.. code-block:: r

    numerical_data <- iris[,-5]
    
Personally, I prefer the use of the ``subset()`` function. The above operations are performed using ``subset`` below:

.. code-block:: R

    petal_data <- subset(iris, select = c(Petal.Width, Petal.Length))
    numerical_data <- subset(iris, select = -c(Species))

.. note::

    It is rare that you would select/drop observations from a dataset in this manner (do not cherry pick your data). This is why the examples are all done on columns.

Filtering Dataframes
--------------------

Filtering dataframes is an extension of dataframe subsetting, performed using ``logical operators``:

* ``<``: less than
* ``<=``: less than or equal to
* ``>``: greater than
* ``>=``: greater than or equal to
* ``==``: exactly equal to
* ``!=``: not equal to
* ``!x``: Not x
* ``x | y``: x OR y
* ``x & y``: x AND y

Using the ``Iris`` dataset as an example, subset the original dataframe to isolate data that belongs to the species ``Setosa``:

.. code-block:: R

    setosa_data <- subset(iris, iris$Species == "Setosa")

Updating Dataframes
-------------------

To create a new variable in our dataframe, we can use the ``$`` operator. 

In the example below, we will subtract ``Petal.Length`` from ``Sepal.Length`` and store it as a new column. 

.. code-block:: R

    iris$sepal_less_petal_len <- iris$Sepal.Length - iris$Petal.Length

IfElse
------

We can use ``ifelse()`` to create new variables based on conditional statements. 

In the example below we will use a vector, however this applies to dataframe columns too:

.. note::

    The ``ifelse()`` function is an example of a ternary operator which reads as follows: `` A ? B : C`` - If ``A`` is true choose ``B``, else choose ``C``.

.. code-block:: R

    vector <- c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

    test <- ifelse(vector > 5, "greater than 5", "less than 5")
    print(test)

.. code-block:: console

    [1] "less than 5"    "less than 5"    "less than 5"    "less than 5"    "less than 5"    "greater than 5" "greater than 5" "greater than 5" "greater than 5" "greater than 5"

But what about the 5th element? 5 is not less than 5. 

To add a second layer of conditionals we will re-use the ``ifelse()`` function:

.. code-block:: R

    test <- ifelse(vector == 5, "five", test)
    print(test)

.. code-block:: console

    [1] "less than 5"    "less than 5"    "less than 5"    "less than 5"    "five"           "greater than 5" "greater than 5" "greater than 5" "greater than 5" "greater than 5"


Worksheet
---------

Go to the following link to 