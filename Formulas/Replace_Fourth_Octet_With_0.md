# Replace the Fourth Octet In An IP Address With A 0

When exporting a lot of IPs, I sometimes need the subnet, and not the IP.  This happens when I'm trying to cross-reference an IP with an office assignment, for example.  This formula just simply puts a .0 at the end.


|  |  A | B | C | 
| ----------- | ----------- | ---- | ----| 
|1| | | | 
|2| |  IP Address    |   New Value |
|3| |192.168.1.1  |  192.168.1.0 |

This formula first checks to see if the value in B3 is empty or contains "192." first.
```
=IF(LEFT(B3,4)="192.",LEFT(B3,FIND("~",SUBSTITUTE(B3,".","~",3))-1)&".0","")
```

To search for a 10.x address, you would use the following:
```
=IF(LEFT(B3,3)="10.",LEFT(B3,FIND("~",SUBSTITUTE(B3,".","~",3))-1)&".0","")
```