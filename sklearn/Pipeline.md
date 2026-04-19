#tech/python #lib/sklearn 
前処理と学習の流れを定義して一気通貫で実行する

### Pipelineの作り方
##### Pipelineコンストラクタ
各推定器の名称を自分で決められる
～ 引数に (名称 - インスタンス)のタプルのリストを指定）
```
from sklearn.pipeline import Pipeline

# Impute(補完)と標準化のパイプライン定義例
pipeline = Pipeline([
	('impute', SimpleImputer(strategy='median')),
	('standardize', StandardScaler())
])

pipeline.fit(pd.DataFrame({'values': [1,2,3,4,np.nan, 6]}))
```

##### make_pipeline()
各推定器の名称は自動で決まる
```
from sklearn.pipeline import make_pipeline
pipeline = make_pipeline(
	SimpleImputer(strategy='median'),
	StandardScaler()
)
```
### Pipelineのメソッド
最後の推定器と同じメソッドを呼び出せるようにする。
##### 最後の推定器が変換器(Transformer)の場合
fit()が呼び出し可能
パイプラインの推定器に対して
→
　前処理（最後のもの以外）：　fit_transform() が呼ばれる
　最後の推定器                    ：　fit() が呼ばれる

##### 最後の推定器が予測器の場合
predict()が呼び出し可能
パイプラインの推定器に対して
→
  前処理（最後のもの以外）： transform()が呼ばれる
  最後の予測器                    ：　predict() が呼ばれる
  
### 推定器の参照
配列のように [n] でn番目の推定器を参照できる。
また、名前指定で参照も可能
```
pipeline = Pipeline([
	('imputer', SimpleImputer(strategy='mean')),
	('scaler', StandardScaler())
])

# インデックスで参照
pipeline[0]
# SimpleImputer()

# 名前で参照
pipeline['scaler']
# StandardScaler
```
