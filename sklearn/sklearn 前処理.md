#tech/python #lib/sklearn
scikit-learn, Keras, TensorFlowによる実践機械学習　読書メモ
##### カスタム変換器
FunctionTransformer
```python
from sklearn.preprocessing import FunctionTransformer
log_transformer = FunctionTransformer(np.log, inverse_func=np.exp)
```

##### 欠損値補完
SimpleImputer
```python
from skelarn.impute import SimpleImputer
```
##### 標準化

StandardScaler
```python
from sklearn.preprocessing import StandardScaler
```

##### カテゴリ列の数値化
2通りの方針
###### 数字に変換
シンプルだが単なるシンボルの場合、大小関係や順位が学習に影響する恐れがあり
OrdinalEncoder
```python
from sklearn.preprocessing import OrdinalEncoder
```

###### 取りうる値を列で持つ
pandasの get_dunmmy
```python
In [40]: pd.get_dummies(pd.DataFrame({'sex': ['F', 'M', 'F']}))
Out[40]:
   sex_F  sex_M
0   True  False
1  False   True
2   True  False
```
OneHotEncoder
```python
In [42]: from sklearn.preprocessing import OneHotEncoder

In [43]: encoder = OneHotEncoder()


In [47]: encoder.fit_transform(
			pd.DataFrame({'sex': ['F', 'M', 'F']})
		 ).toarray()
Out[47]:
array([[1., 0.],
       [0., 1.],
       [1., 0.]])

In [48]: encoder.categories_
Out[48]: [array(['F', 'M'], dtype=object)]
```
##### パイプライン
[[Pipeline]]
推定器を連鎖的に適用させるパイプライン作成
``` python
from sklearn.pipeline import Pipeline

num_pipeline = Pipeline([
	('log', log_transformer),
	('std', StandardScaler())
])

# make_pipeline() を使用すれば自動で名称をつけてくれる
cat_pipeline = make_pipeline(
	OneHotEncoder(),
	StandardScaler()
)
```

##### ColumnTransformer
カラム毎に変換器を適用
```python
from skleran.compose import ColumnTransformer
```
