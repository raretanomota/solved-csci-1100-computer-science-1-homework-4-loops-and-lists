Download Link: https://assignmentchef.com/product/solved-csci-1100-computer-science-1-homework-4-loops-and-lists
<br>
<h1>Part 1: Words with alternating vowels and consonants</h1>

Write a program that reads in a word entered by the user and checks whether:

the word has at least 8 characters, starts with a vowel, has alternating vowels and consonants, and the consonants are in increasing alphabetical order.

Note that you can check letters for alphabetical order using &lt;.

For example:

&gt;&gt;&gt; ’a’ &lt; ’b’

True

&gt;&gt;&gt; ’z’ &lt; ’b’

False

Your program should work for words entered upper or lower case, and must use a single function is_alternating(word) that returns True if the word has the above pattern, and False otherwise. (<strong>Hint. </strong>Remember to write a loop that goes through each letter and check for the necessary conditions. Using indexing is important here as you need to compare letters in different positions.

Here is an example run of this program:

Enter a word =&gt; eLimiNate eLimiNate

The word <sup>’</sup>eliminate<sup>’ </sup>is alternating

Enter a word =&gt; ageneses ageneses

The word <sup>’</sup>ageneses<sup>’ </sup>is not alternating

Enter a word =&gt; ADAGE

ADAGE

The word <sup>’</sup>adage<sup>’ </sup>is not alternating

The word eliminate has this alternating pattern since we have that: ‘l'&lt;‘m'&lt;‘n'&lt;‘t’.

The word adage is not long enough, ageneses has two consonants that are identical and as a result not in strictly increasing alphabetical ordering.

Here is a little hint that will help: Given a letter stored in the variable x, the boolean expression:

x in <sup>’</sup>aeiou<sup>’</sup>

is True if and only if x is a lower case vowel.

When you have tested your code, please submit it as hw4Part1.py. Be sure you use the correct filename, otherwise, Submitty will not be able to grade your submission.

<h1>Part 2: New York State Death Statistics</h1>

As part of an open government initiative, New York State releases a large number of health related statistics for researchers and developers to use. Among these are death statistics by region of the state at <a href="https://health.data.ny.gov/">https://health.data.ny.gov</a><a href="https://health.data.ny.gov/">.</a> For this assignment, we have simplified the statistics to provide just the total number of deaths per 100,000 people. Our goal is to come up with a simple visualization comparing death trends between two different counties over the last few years.

Write a program to read in the death statistics for two different areas of NYS for the 11 years from 2003 to 2013. Remember that these are deaths per 100,000 people. We will take the naive view that areas with lower deaths per 100,000 are automatically healthier places to live, ignoring all other population demographics such as age. Compute the difference between the death rates of the areas for each year, and encode this as a string visualization using the symbols =, +, and -, where = implies the two areas are within +/- 50 deaths per 100,000 for that year, + implies the first area has more than 50 fewer deaths for that year, and – implies that the first area has more than 50 more deaths for that year. Compare the number of + and – symbols in your string to determine the healthier area with + favoring the first area and – favoring the second. Print out the trend line including a header for the data labeling the start and end years – this should be in reverse order from 2013 to 2003 – along with your determination of the healthier area.

The utility module provided for this homework will give you some help. Given a string containing a county name, it provides a function read_deaths(county) that returns you a list of 11 numbers. Try the following:

import hw4_util cdata1 = hw4_util.read_deaths(<sup>’</sup>Erie<sup>’</sup>) cdata2 = hw4_util.read_deaths(<sup>’</sup>Cattaraugus<sup>’</sup>) print(<sup>’</sup>Erie:<sup>’</sup>, cdata1) print(<sup>’</sup>Cattaraugus:<sup>’</sup>, cdata2)

would give:

Erie: [1061.0, 1032.0, 1047.0, 1020.0, 1040.0, 1037.0, 1029.4, 1010.0, 1043.0, 1014.0, 1046.0]

Cattaraugus: [1005.0, 1089.0, 1061.0, 978.7, 972.7, 978.8, 1010.2, 1083.0, 1002.0, 977.9, 990.0]

The difference (rounded to one decimal) is:

[56.0, -57.0, -14.0, 41.3, 67.3, 58.2, 19.2, -73.0, 41.0, 36.1, 56.0]

Running the program with these values would give:

Enter the first area to check =&gt; Erie

Erie

Enter the second area to check =&gt; Cattaraugus Cattaraugus

2013       2003

Trend: -==+=–==+-

I would rather live in Cattaraugus than Erie

Note that 2013 and 2003 are printed to line up with the margins of the trend data.

Here is another example where the number of ”+” and ”-” symbols are the same:

Enter the first area to check =&gt; Bronx

Bronx

Enter the second area to check =&gt; Queens Queens

2013       2003

Trend: ===========

Bronx and Queens are the same

The function hw4_util.read_deaths will return an empty list whenever the county cannot be found. Your program must give an error and exit when it encounters an invalid name as shown below.

Enter the first area to check =&gt; Errie

Errie

Errie is an invalid name

or

Enter the first area to check =&gt; Erie

Erie

Enter the second area to check =&gt; Wesstchaester

Wesstchaester

Wesstchaester is an invalid name

You can ignore any warnings you get from using sys.exit() that may show up after your error message.

When you have tested your code, please submit it as hw4Part2.py. Be sure to use the correct filename or Submitty will not be able to grade your submission.

<h1>Part 3: Pokemon GO</h1>

This is a little variation on the turtle walk we did last homework. This time, we place a Pokemon trainer at the center of an 11×11 grid at position (5,5). As in the previous homework (0,0) is in the upper left corner and (10,10) is in the lower right corner. The grid is populated by Pokemon and your job is to guide the pokemon trainer around the grid gathering up any Pokemon they find.

You will need to read the list of Pokemon and their locations on the grid using the read_pokemon function from hw4_util. By now you should be experts at this. For example, the program:

import hw4_util pokemon, locations = hw4_util.read_pokemon() print(pokemon) print(locations)

Will produce:

[<sup>’</sup>Pikachu<sup>’</sup>, <sup>’</sup>Bulbasaur<sup>’</sup>, <sup>’</sup>Charizard<sup>’</sup>, <sup>’</sup>Squirtle<sup>’</sup>] [(2, 3), (4, 1), (6, 3), (2, 4)]

The first list is the pokemon that are available on this particular grid, while the second list is their locations. You may assume without checking that no locations are repeated in this list. The pokemon trainer collects pokemon by walking around the grid one step at a time. The trainer can move in one of 4 directions N (up), S (down), E (right) and W (left). When the trainer lands on the same space as a pokemon, the pokemon is considered captured. We won’t require you to animate the pokemon battles for this homework. This simulation has an indeterminate number of steps driven by user input.

<h2>The Program</h2>

This is a turn based simulation driven by user input. To set up the simulation, first use read_pokemon to load in the pokemon data. Immediately print out the list of Pokemon and their locations using a function print_pokemon that you will need to write. The function should only print out pokemon that have not been captured by the trainer. This will allow you to use it at additional places in the simulation.

Once you have the simulation set up you enter a loop. At the start of each iteration through the loop begin by asking the user for a command:

<ol>

 <li><strong>N </strong>moves up one step</li>

 <li><strong>S </strong>moves down one step</li>

 <li><strong>E </strong>moves right one step</li>

 <li><strong>W </strong>moves left one step</li>

 <li><strong>print </strong>print all active (uncaptured) pokemon and their locations</li>

 <li><strong>end </strong>stop the simulation and end the program</li>

</ol>

After each command other than end, print out the current location of the trainer and report if the trainer has captured a pokemon. A sample run is below:

Current pokemon:

Pikachu at (2, 3)

Bulbasaur at (4, 1)

Charizard at (6, 3)

Squirtle at (2, 4)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; N

N

Currently at (5, 4)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; n n

Currently at (5, 3)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (4, 3)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; W

W

Currently at (3, 3)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (2, 3)

You capture a Pikachu on turn 4

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; print print

Current pokemon:

Bulbasaur at (4, 1)

Charizard at (6, 3)

Squirtle at (2, 4)

Currently at (2, 3)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; end end

Or a second example:

Current pokemon:

Pikachu at (2, 3)

Bulbasaur at (4, 1)

Charizard at (6, 3) Squirtle at (2, 4) N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (4, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (3, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (2, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (1, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (0, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; w w

Currently at (0, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; prrrint prrrint

Currently at (0, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; print print

Current pokemon:

Pikachu at (2, 3)

Bulbasaur at (4, 1)

Charizard at (6, 3)

Squirtle at (2, 4)

Currently at (0, 5)

N,S,E,W to move, <sup>’</sup>print<sup>’ </sup>to list, or <sup>’</sup>end<sup>’ </sup>to stop ==&gt; end end

Some notes:

<ol>

 <li>Be careful not to let the trainer walk off the field</li>

 <li>Make sure that your commands are case insensitive</li>

 <li>We will use a different pokemon file when we test on Submitty, so make sure you test thoroughly</li>

 <li>If you get an invalid command (such as prrrint in the second example) just ignore it, print the current position, and start the next turn</li>

</ol>

When you have tested your code, please submit it as hw4Part3.py. You must use this filename, or Submitty will not be able to run and grade your code.