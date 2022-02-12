# wa - Wordle Assistant 

wa builds a regular expression from a file containing the state of play
and uses that to filter a dictionary to find all the words that could
match.  It then looks at the frequency of letters in the remaining 
dictionary and tries to create suggestions in order of high possibility
by permutating the letters and then selecting any results that are 
* words
* match the filter

It's designed to run with default options from the repo root directory
but if you want it to work some other way you have to provide the -d
argument to tell it where its dictionary is.


You can run it initially to suggest a list of starting words like:

    ./wa 

Then you can pick one of the words, put it into wordle as a guess and
fill out your first game state file (e.g. guesses.json) in a format 
like this: 

    [
        ["sores", "gygrg"]
    ]

This file lists the guesses made with the results from the game:
* g - gray (meaning a non-match)
* y - yellow (meaning a match but wrong position)
* r - gReen ( meaning a match)

You can then run the program again to make new suggestions: 

    ./wa -g guesses.json

...and add the result back into your guesses.json so you can 
keep cycling on.

    [
        ["sores", "gygrg"],
        ["pores", "yygrg"]
    ]

