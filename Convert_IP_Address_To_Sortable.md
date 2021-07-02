# Sort IP Addresses in Excel

I often have to sort IP Addresses in a spreadsheet, but Excel (somehow) doesn't natively support this.  Why this isn't a number type, I have no idea.

So, with this in mind, I have to use the formula below to take values in one cell, and convert it.  Then I sort this column and hide it.

|  |  A | B | C | 
| ----------- | ----------- | ---- | ----| 
|1| | | | 
|2| |  IP Address    |  New Sortable IP |
|3| |192.168.1.1  |  192.168.001.001 |

```
=TEXT(LEFT(B3,FIND(".",B3,1)-1),"000") & "." & TEXT(MID(B3,FIND( ".",B3,1)+1,FIND(".",B3,FIND(".",B3,1)+1)-FIND(".",B3,1)-1),"000") & "." & TEXT(MID(B3,FIND(".",B3,FIND(".",B3,1)+1)+1,FIND(".",B3, FIND(".",B3,FIND(".",B3,1)+1)+1)-FIND(".",B3,FIND(".",B3,1)+1)-1), "000") & "." & TEXT(RIGHT(B3,LEN(B3)-FIND(".",B3,FIND(".",B3,FIND( ".",B3,1)+1)+1)),"000")
```


