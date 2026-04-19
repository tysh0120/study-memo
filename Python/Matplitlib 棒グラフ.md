#tech/python #lib/matplotlib 
plt.bar(pos, height, width, bottom, \*, align, data, **kwargs)

- pos: x座標 配列
- height: 高さの配列
- bottom: 高さの始点 積み上げグラフ作成時などに便利
- align: posで指定した各tickに対する配置位置 
   ("center" 中心 / "edge" 左端合わせ) 
   widthに負の値を指定すると右端合わせにできる
- data: {キーワード: 値} オブジェクトを指定。各パラメタをキーワードで指定できる。使い道がよくわからん。
- kwargs: rectのキーワード引数

### 簡単な例
pos = [1,2,3]
plt.bar(pos, [2,4,1])

### 積み上げグラフ
plt.bar(pos, [2,3,1])
plt.bar(pos, [2,1,3], bottom=[2,3,1])  # bottomに前回の高さを入れると積み重なる

### 2系列グラフ
align="edge"とwidthに正と負を指定して簡単に書ける
```python
plt.bar(pos, [2,3,1], align="edge", width=-0.3)  # widthに負を指定するとtickの左に配置
plt.bar(pos, [2,1,3], align="edge", wdith=0.3]) # widthがせいなのでtickの右に配置
```

### 多系列
posをずらしながら各系列を描いていく
```python
# データ数5, 系列数3とする
x = range(5)
d=1/6
plt.bar(x, [3,2,5,4,3], width=1/4)
plt.bar(x+1*d, [2,4,3,4,1], width=1/4)
plt.bar(x+2*d, [3,4,2,1,4], width=1/4)
```