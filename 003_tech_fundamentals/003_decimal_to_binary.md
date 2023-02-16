# Decimal to Binary

A sample decimal number: 133.33.33.7     
Each number between the dots has a value between 0-255.

## The Rules
1. Move from left to right.
2. If the decimal is smaller than the binary, write ```0``` in the table
3. If the decimal is equal to or larger, write ```1``` in the table

| position               | 1  |  2 |  3 |  4 |  5 |  6 |  7 |  8 |  
| ------                 | -- | -- | -- | -- | -- | -- | -- | -- |    
| binary position value | 128  |  64 |  32 |  16 |  8 |  4 |  2 |  1 | 
| binary value           |  1 | 0  |  0 |  0  |  0  |   |   |   |


A walk through.     
The first decimal is 133.  It is larger than 128, so we put a ```1``` in the first position.       
Now we subtract 128 from 133 which gives us our ```new decimal of 5```.   

Now we go to position 2.  We ask, "is 5 less than 64?"  It is, so we put a ```0``` in the binary value and move to the right.    

