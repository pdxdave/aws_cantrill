# Decimal to Binary

A sample decimal number: 133.33.33.7     
Each number between the dots has a value between 0-255.

## The Rules
1. Move from left to right.
2. If the decimal is smaller than the binary, write ```0``` in the table
3. If the decimal is equal to or larger, write ```1``` in the table

| position               | 1    |  2  |  3  |  4  |  5  |  6  |  7 |  8 |  
| ------                 | --   | --  | --  | --  | --  | --  | -- | -- |    
| binary position value  | 128  |  64 |  32 |  16 |  8  |  4  |  2 |  1 | 
| binary value           |  1   |  0  |  0  |  0  |  0  |  1  |  0 |  1 |


A walk through.     
The first decimal is 133.  It is larger than 128, so we put a ```1``` in the first position.       
Now we subtract 128 from 133 which gives us our ```new decimal of 5```.   

Now we go to position 2.  We ask, "is 5 less than 64?"  It is, so we put a ```0``` in the binary value and move to the right.    
We know that 5 is less than 64, 32, 16 and 8, so we can put a ```0``` in those binary values.    
At binary position value 4, we know that our decimal value of 5 is larger, so we put a ```1``` there.  
Now we take our decimal value of 5 and subtract 4, giving us 1, our new decimal number.    
Next is binary position 2 greater than decimal 1?  It is, so we put a ```0``` in the binary value.  
And lastly, the decimal is equal to our binary position value, so the binary value gets a ```1```     
Add the binary values together (126, 4, 1) and you get 133. 

| results     | 1          |  2        |  3        |  4       | 
| ------      | --         | --        | --        | --       |
| decimal     | 133        |  33       |  33       |  7       |   
| binary      | 10000101   | 00100001  | 00100001  | 00000111 | 




# Binary to Decimal

Starting binary number: 10000101.0010001.00100001.00000111

| binary value           | 1    |  0  |  0  |  0  |  0  |  1  |  0 |  1 |  
| ------                 | --   | --  | --  | --  | --  | --  | -- | -- |    
| binary position value  | 128  |  64 |  32 |  16 |  8  |  4  |  2 |  1 | 
| decimal value          | 128  |  0  |  0  |  0  |  0  |  4  |  0 |  1 | 

Add the decimal values: 133