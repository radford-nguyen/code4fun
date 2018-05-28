Excel :D

 
```
=SUM(IF(MID(ABS(J1302),ROW(INDIRECT("1:"&LEN(ABS(J1302)))),1)=MID(ABS(J1302),LEN(ABS(J1302))-ROW(INDIRECT(LEN(ABS(J1302))&":1"))+1,1),1, 0))
```

## Submitted by

Matthew Janiga, master troll
2013/04/24
