# php_weighted_random
A PHP7 class to generate weighted random results. This may also be called "biased random", "reservoir sampling", or "lootbox results" by some folks. It can return a single weighted random item, an array of weighted random items, or print a results table for you.

Weights or bias can be:

Even - such as with a coin where the odds are 50/50

Loaded - like a cheaters dice where one side has slightly higher odds of being rolled

Mixed - like a loot box would be in a videogame or a presidential election


Calculations and results can be performed multiple times on the same object. 

Items to roll on can be provided at run time as an array or default objects are available for selection such as: coin, cheaters dice, colors, and lootbox.
To use custom items pass an array with item names and weights to the object when it is instantiated.

Class documented both inline and using phpdocumentor for reference.
 
## Getting Started
Be running PHP 7 on your web server.

Download weightedrandom.php to the appropriate directory.

Create a $wrandom object.

Call functions as needed.


## Available Functions
$wrandom->return_single_random_item() - Returns a single weighted random item name as a string.

$wrandom->return_array_random_results($num = 50000) - Returns an array with each item and the number of times it was selected. If a number is provided this is the number of items selected.

$wrandom->calculate_multiple_results($num = 50000) - Executes the number of picks requested but nothing is returned.

$wrandom->print_results_table() - Prints an HTML table with information about the items and results.


## Examples
### Example 1
Using default item bag of lootbox.
```
<?
//add weightedrandom file

require_once("weightedrandom.php");

//create $wrandom object

$wrandom = new weightedrandom();



//return a single random item

echo $wrandom->return_single_random_item();




//return array after 50,000 picks
print_r($wrandom->return_array_random_results(50000));



?>
```

The above would result in:

Single item:
```
Polearm
```

Array result:
```
Array
(
    [Axe] => 7202
    [Mace] => 4368
    [Sword] => 4147
    [Crossbow] => 3191
    [Scepter] => 4982
    [Polearm] => 5166
    [Javelin] => 6836
    [Stave] => 6327
    [Bow] => 4321
    [Wand] => 1620
    [Dagger] => 1384
    [Spear] => 456
)
```
### Example 2
Using a custom item bag with bias.
```
<?
//add weightedrandom file

require_once("weightedrandom.php");

//create $wrandom object with custom objects for the bag

$wrandom = new weightedrandom(array("Whiskey" => 20,"Beer" => 10,"Gin" => 5,"Vodka" => 8));



//return a single random item

echo $wrandom->return_single_random_item();

//calculate 10 picks and print a results table
$wrandom->calculate_multiple_results(10);
$wrandom->print_results_table();

//calculate 1,000,000 picks and print results table
$wrandom->calculate_multiple_results(1000000);
$wrandom->print_results_table();


//return array after 50,000 picks
print_r($wrandom->return_array_random_results(50000));



?>
```
The above would result in:

Single item:
```
Whiskey
```

Table results:
```
Total items: 4
Total weight: 43
Total rolls: 10

Item	   Weight	 % Weight	 Result Count	 Result %	 Difference
Whiskey   20	     46.512	   3	            30	       -16.512
Beer      10	     23.256	   3	            30	       6.744
Gin       5	      11.628	   2	            20	       8.372
Vodka     8	      18.605	   2	            20	       1.395



Total items: 4
Total weight: 43
Total rolls: 1000000

Item	   Weight	 % Weight	 Result Count	 Result %	 Difference
Whiskey   20	     46.512	   465642	       46.564	   0.052
Beer      10	     23.256	   232190	       23.219	   -0.037
Gin       5	      11.628	   116088	       11.609	   -0.019
Vodka     8	      18.605	   186080	       18.608	   0.003
```

Array result:
```
Array
(
    [Whiskey] => 23291
    [Gin] => 5820
    [Vodka] => 9124
    [Beer] => 11765
)
```
## Acknowledgments
The method of calculating the weighted random / biased random as used in this program is from:

https://stackoverflow.com/questions/1761626/weighted-random-numbers

https://blogs.msdn.microsoft.com/spt/2008/02/05/reservoir-sampling/

https://xlinux.nist.gov/dads//HTML/reservoirSampling.html

## Misc
I did not do spell check.

## License
```
##############################LICENSE################################
#Copyright (c) 2019 Eric Wamsley.                                   #
#All rights reserved.                                               #
#                                                                   #
#Redistribution and use in source and binary forms are permitted    #
#provided that the above copyright notice and this paragraph are    #
#duplicated and viewable in all forms and that any documentation,   #
#advertising materials, and other materials related to such         #
#distribution and use acknowledge that the software was developed   #
#by ERIC WAMSLEY. THIS SOFTWARE IS PROVIDED "AS IS" AND WITHOUT     #
#ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, WITHOUT LIMITATION,  #
#THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A        #
#PARTICULAR PURPOSE.                                                #
##############################LICENSE################################
```
