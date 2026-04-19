#tech/python #lib/networkx #lib/matplotlib
maptlotlibでネットワーク図を書くライブラリ

### 読み込み
import networkx as nx
import matplotlib.pyplot as plt
### インスタンス生成
G = nx.Graph()
### node追加
nx.add_node('A')
nx.add_node('B')
nx.add_node('C')

### edge(辺)追加
nx.add_edge('A', 'B')
nx.add_edge('B', 'C')
nx.add_edge('A', 'C')

### 描画
nx.draw(G)

### よく使いそうなキーワード引数:
##### pos: Nodeの座標
drawの引数に、{ノード名: (x, y)} の辞書を指定
pos = {'A': (0, 0), 'B': '(0, 1), 'C': (1, 0)}
nx.draw(G, pos=pos)
##### width: 辺の幅の指定
nx.draw(G, ..., width=[1,2,3])
##### with_labels: ラベル表示
nx.draw(G, ..., with_labels=True)
##### node_size: ノードのサイズ
nx.draw(G, ..., node_size=1000)
##### font_size: フォントサイズ
ラベルのフォントサイズ