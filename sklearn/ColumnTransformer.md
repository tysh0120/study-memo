
#tech/python #lib/sklearn 
カラム毎に適用する前処理を定義

### 使い方
##### コンストラクタ
名称を設定
```
from sklearn.compose import ColumnTransformer

# 数値項目には、SimpleImputerとStandardScaleのパイプラインを、
# カテゴリ項目には、OneHotEncoderを適用する例
preproc = ColumnTransformer([
	('num', make_pipeline(
				SimpleImputer(strategy='mean'),
				StandardScale()
			), ['age', 'height', 'weight']),
	('cat', OneHotEncoder(), ['sex', 'bloodtype'])
])
```

 出力の列名には、\`名称__列名\`の形式をとる
 ```
 preproc.get_feature_names_out()
 # ['num__age', 'num__height', 'num__weight', 'cat__sex__f', 'cat__sex_m', 'cat__bloodtype_a] 
 ``` 
##### make_column_transformer()で型に応じた列を自動選択
```
preproc = make_column_transformer([
	(make_pipeline(
		SimpleImputer(strategy='mean'),
		StandardScale()
	), ['age', 'height', 'weight']),
	(OneHotEncoder(), ['sex', 'bloodtype'])
])
```

##### make_column_selector()による列の自動選択
make_column_selector()を使うと列を列挙せずに型に応じて自動選択できる
```
preproc = ColumnTransformer([
	('num', make_pipeline([
		SimpleImputer(strategy='mean'),
		StandardScale()
	]), make_column_selector(dtype_include=np.number)),
	('cat', OneHotEncoder(), make_column_selector(dtype_include=object))
])
```