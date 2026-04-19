#tech/python #lib/sklearn #ColumnTransformer
[[ColumnTransformer]]
### Transformerが受け取るパラメタの型はndarray か DataFrame
ColumnTransformerの中のTransformerには基本ndarrayで渡ってくるが、DataFrameで渡ることがある。
具体的には以下の3条件を満たすとき 
1. 入力XがDataFrame
2. ColumnTrtansformerのtransformersを列名で指定
3. Transformerの戻りがDataFrame

Transformer作成時は、DataFrameの場合も考慮するのがベストプラクティス（Copilot談）
```python
def transform(self, X):
	# 👇 DataFrameの場合の考慮
	if hasattr(X, "iloc"):
		X = X.copy()
		X["ratio"] = X["a"] / X["b"]
		return X

	# ndarrayの場合
	ratio = (X[:,0]/X[:,1]).reshape(-1, 1)
	return np.hstack([X, ratio])
```

### Transrofmerの戻り値は2次元である必要がある
ColumnTransformerは各列を変換したものをhstackで結合するため、hstackの制約として２次元である必要がある

### sklearnの哲学：
- 特徴量Xは２次元
- yは１次元

TransformerはX→Xの写像なので、２次元→2次元
よってTransoformerの戻り値は２次元である必要がある

たとえ戻り値が１列しかなくても、(n,1)の２次元にするのが自然


