#tech/python #lib/sklearn 
sklearnの学習器、変換器のベースクラス

set_params(),  get_params() の実装を提供

BaseEstimatorと、作成するクラスに応じたMixinを一緒に継承してクラスを作成
- ClasifierMixin / RegressorMixin / ClusterMixin .... (学習器)
- TransformerMixin  (変換器)

学習器は、scoreなどの実装
変換機は、fit_transformなどのデフォルト実装

```
class MyTransformer(BaseEstimator, TransformerMixin):
  def __init__(self):
```

fitメソッド : 戻りにselfを返す
get_feature_names_out() : 変換後の列名を配列で返す（列数が変わらなければ省略も可）
