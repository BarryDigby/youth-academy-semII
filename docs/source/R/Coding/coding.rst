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

We can use the ``driver_names`` variable to assign names to the ``racing_number`` vector using the ``names()`` function. Store the ``racing_number`` variable as ``drivers`` to avoid confusion!

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

    print(drivers[1])
    print(drivers[7])
    print(drivers[2:4])

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

