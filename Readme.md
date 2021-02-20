# Coding Challenge

##iles:

- overbond_coding_challenge.py
- sample_input.csv
- tests.py

##Technologies Used


- Language: Python
- Libraries: NumPy, SciPy, csv, os, math

## Challenge #1

###Description

Calculates the yield spread (return) between a corporate bond and its government bond benchmark. 

###Execution Steps

Call yield_spread() with 2 parameters:
- Param 1: pathname - this parameter stores the location of the csv file that contains data about the bonds
- Param 2: bond_name - this parameter is the name of the corporate bond for which the yield spread is to be calculated

###Approach:

- Verify availability of file at given location
- Call store_bonds function with pathname as an input parameter to store government and corporate bond data in 2 different lists (iteration time will be reduced by storing the bond data in separate lists) with numeric values of the fields - ‘term’ and ‘yield’ (for ease of arithmetic operations). 
- Verify that at least one government bond exists for benchmarking
- Verify that the corporate bond given as an input exists in the csv file
- Find the benchmark government bond for this corporate bond by iterating through the list of government bonds to find the bond that has the minimum term difference with the corporate bond term. 

## Challenge #2

###Description

Calculate the spread to the government bond curve.

###Execution Steps:

Call calculate_spread() with 1 parameter:
- Param 1: pathname - this parameter stores the location of the csv file that contains data about the bonds

###Approach:

- Verify availability of file at given location
- Call store_bonds function with pathname as an input parameter to store government and corporate bond data in 2 different lists with numeric values of the fields - ‘term’ and ‘yield’. 
- Store the terms and yields of government bonds in 2 NumPy arrays to be given as x and y coordinates to the interp1d function in the SciPy library to build a linear interpolant function. 
- Iterate through the corporate bonds to calculate the spread to the government bond curve by evaluating the interpolant function at the term of the corporate bond. It is assumed that the term of every corporate bond lies between 2 given government bond terms, so the interpolant function can be evaluated at the corporate bond term. 


### Test Scenarios Covered

####Challenge 1:

- File at specified pathname does not exist
- The given corporate bond does not exist in the csv file
- No government bond exists in the csv file
- Only one government bond exists in the csv file
- Government bonds with the same term, but different yields in the csv file
- Only one corporate bond and one government bond exists
- Multiple corporate and government bonds exist
- No corporate bonds exist

####Challenge 2:

- File at specified pathname does not exist
- Multiple corporate and government bonds exist
- No corporate bonds exist

###Trade-offs

- Verify the format of the csv file
- Verify the term and yield data is valid
- For the second challenge, it is assumed that no two government bonds have the same term. If they were to have the same term, a different kind of interpolant function might be needed.


