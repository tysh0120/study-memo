#tech/phthon #lib/sklearn

### 機能
カテゴリ変数を数値の連番に変換

### 使い方

```
from sklearn.preprocessing import LabelEncoder

# 1. 使用するカテゴリを渡して初期化
LabelEncoeder.fit(["cat1", "cat2"])

# 2. transformで変換
LabelEncoder.transofrm(df['categories'])

# インプット ["cat1", "cat2", "cat2", "cat1"]
# 戻り値 [0,1,1,0]
 ```

### 注意
複数のカテゴリからなる場合、値の大きさや並びに意味があると思ってしまう可能性あり