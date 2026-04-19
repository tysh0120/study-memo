#python 

importlib.reload(修復したいオブジェクト) で修復

```python
imoprt matplotlib.pyplot as plt

plt.x_ticks = [1,2,3]  # 正しくはplt.x_ticks([1,2,3])

pltが壊れてしまった

plt.x_ticks([1,2,3])
-> Attribute Error  no attribute x_ticks

# リカバリ
import importlib
importlib.reload(plt)  # これで修復
```
