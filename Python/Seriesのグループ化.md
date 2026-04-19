#tech/python #lib/pandas
### グループ名を値に取る配列を渡す
Seriesと同じ長さのグループ名を値に取る配列を渡す
```
ser = [1,2,3,4,5]
ser.groupby(['A', 'B', 'A', 'C', 'C']).count()
Out[]
A  2
B  1
C  2
```


自分自身でグループ化する例
ser.groupby(ser)


