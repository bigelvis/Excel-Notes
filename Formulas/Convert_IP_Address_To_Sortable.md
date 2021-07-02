# Sort IP Addresses in Excel

I often have to sort IP Addresses in a spreadsheet, but Excel (somehow) doesn't natively support this.  Why this isn't a number type, I have no idea.

So, with this in mind, I have to use the formula below to take values in one cell, and convert it.  Then I sort this column and hide it.

|  |  A | B | C | 
| ----------- | ----------- | ---- | ----| 
|1| | | | 
|2| |  Sortable IP Address    |   IP Address |
|3| |192.168.001.001  |  192.168.1.1 |

In Cell B3, enter the following formula:
```
=TEXT(LEFT(C3,FIND(".",C3,1)-1),"000") & "." & TEXT(MID(C3,FIND( ".",C3,1)+1,FIND(".",C3,FIND(".",C3,1)+1)-FIND(".",C3,1)-1),"000") & "." & TEXT(MID(C3,FIND(".",C3,FIND(".",C3,1)+1)+1,FIND(".",C3, FIND(".",C3,FIND(".",C3,1)+1)+1)-FIND(".",C3,FIND(".",C3,1)+1)-1), "000") & "." & TEXT(RIGHT(C3,LEN(C3)-FIND(".",C3,FIND(".",C3,FIND( ".",C3,1)+1)+1)),"000")
```

Next, sort column B (make sure to select only numbers starting at B3 and down, and select "expand selection" when prompted).  
Next, hide Column B to clean up the visuals.

Typically, I'll have this column off to row AA or something way to the right, so it doesn't mess with the column order I'm working in.
