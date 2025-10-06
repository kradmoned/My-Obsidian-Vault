# Days in a month formula
For a particular month the days in it is given by this formula 
```
function f(x) { return 28 + (x + Math.floor(x/8)) % 2 + 2 % x + 2 * Math.floor(1/x); }
```
This formula does not account for leap years.

# The main loop
## Year
Year is the simplest just add them
## Month
For Month , we will need a loop that will do as follow
First get all the months for exaMPLE 23
Do a while loop `while(month>12)`
	in that while loop we will subtract 12 from the month , and add one to year.
This will take care of month
## Date
Then we will need to work for days, we will use the current month input into the formula get the days to be subtracted , subtract them from our *days* and get new date while incrementing month we will do this process as long as the *days* is less greater than the days in the particular *month*