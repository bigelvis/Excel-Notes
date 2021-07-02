# Sort IP Addresses in Excel

I often have to sort IP Addresses in a spreadsheet, but Excel (somehow) doesn't natively support this.  Why this isn't a number type, I have no idea.

So, with this in mind, I have to use the formula below to take values in one cell, and convert it.  Then I sort this column and hide it.

|  |  A | B | C | 
| ----------- | ----------- | ---- | ----| 
|1| | | | 
|2| |  Sortable IP Address    |   IP Address |
|3| |192.168.001.001  |  192.168.1.1 |

```
=TEXT(LEFT(C3,FIND(".",C3,1)-1),"000") & "." & TEXT(MID(C3,FIND( ".",C3,1)+1,FIND(".",C3,FIND(".",C3,1)+1)-FIND(".",C3,1)-1),"000") & "." & TEXT(MID(C3,FIND(".",C3,FIND(".",C3,1)+1)+1,FIND(".",C3, FIND(".",C3,FIND(".",C3,1)+1)+1)-FIND(".",C3,FIND(".",C3,1)+1)-1), "000") & "." & TEXT(RIGHT(C3,LEN(C3)-FIND(".",C3,FIND(".",C3,FIND( ".",C3,1)+1)+1)),"000")
```
