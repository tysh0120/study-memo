#lib/matplotlib #tech/python #可視化

plt.scatter(x, y, s=sizes, c=colors)

##### c (colors)の説明
scatterの戻りscを第1引数に colorbarを呼ぶ
plt.colorbar(sc, '色の説明')

##### s (sizes) のlegend
手動で作成　
(**scatterに空のx, yを渡して凡例を作成するテクニック**)
plt.plot([], [], s=10, label='size:10')

```python
import matplotlib.pyplot as plt
import numpy as np
sizes = np.random.randint(0, 50, 100)
colors = np.random.randint(0, 20, 100)
x = np.random.randint(0, 100, 100)
y = np.random.randint(0, 100, 100)

# 散布図描画
sc = plt.scatter(x, y, s=sizes, c=colors)

# 色の説明
plt.colorbar(sc, label='color legend')

# サイズのlegend
for s in [10, 20, 30, 40, 50]:
  plt.scatter([], [], s=s, label=f'size:{s}', color='blue')

plt.legend()

```