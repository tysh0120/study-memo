#tech/python #lib/sklearn

カテゴリ値を持つ属性のすべての値に対応する列を追加して、値に該当する列のみが１、他は０をとるように値を設定する。
カテゴリ値を持つ属性を、単純に数値でラベル付けすると、数値の大小関係や値同士の距離が学習に影響をしてしまう可能性があるため項目をばらしてワンホットエンコーディングする

## 例
```
df = pd.DataFrame({
	'sex': ['M', 'F', 'F', 'M', 'F'],
	'blood': ['A', 'O', 'B', 'AB', 'O'],
	'age': [30, 43,21,54,14]
})

df_encoded = pd.DataFrame({
	sex_M:  [1, 0, 0, 1, 0],
	sex_F:  [0, 1, 1, 0, 1],  # 不要
	blood_A: [1, 0, 0, 0, 0],
	blood_B: [0, 0, 1, 0, 0],
	blood_AB:[0, 0, 0, 1, 0],
	blood_O: [0, 1, 0, 0, 1]  # 不要
	'age': [30, 43,21,54,14]
})

# 各カテゴリに属する値の数だけ列を作成。
# ただし各カテゴリの列のうち１列は、他のすべての列が０となる行で表現できるため、情報として不要なため削除する（Python実践データ分析 P.121 ノック４６)
```

## pd.get_dummys()

DataFrameを引数に渡すと、自動でカテゴリ値の列を判別して列追加してくれる。
使い方が簡単だが下記注意点
1. すべてのカテゴリ値が含まれないデータフレームを処理するとすべての列が追加されず、異なるShapeとなってしまう
2. 
```
encoded = pd.get_dummys(df)
encoded
--->
   age  sex_F  sex_M  blood_A  blood_AB  blood_B  blood_O
0   30  False   True     True     False    False    False
1   43   True  False    False     False    False     True
2   21   True  False    False     False     True    False
3   54  False   True    False      True    False    False
4   14   True  False    False     False    False     True

```

## OneHotEncoder
skelern.preprocessing.OneHotEncoeder
これはすべての列を含まないDataFrameでも、fitで学習した列をすべて含む形で出力してくれる
```
In [7]: from sklearn.preprocessing import OneHotEncoder

In [8]: encoder = OneHotEncoder()

In [9]: encoded_vals = encoder.fit_transform(df)
```
戻りはscipy.sparse._csr.csr_matrix 型のオブジェクト
```
In [10]: encoded_vals
Out[10]:
<Compressed Sparse Row sparse matrix of dtype 'float64'
        with 15 stored elements and shape (5, 11)>

```
toarray()で配列化できる
```
In [20]: encoded_vals.toarray()
Out[20]:
array([[0., 1., 1., 0., 0., 0., 0., 0., 1., 0., 0.],
       [1., 0., 0., 0., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 0., 0., 1., 0., 0., 1., 0., 0., 0.],
       [0., 1., 0., 1., 0., 0., 0., 0., 0., 0., 1.],
       [1., 0., 0., 0., 0., 1., 1., 0., 0., 0., 0.]])

```
categories_ でカテゴリ値一覧
```
In [13]: encoder.categories_
Out[13]:
[array(['F', 'M'], dtype=object),
 array(['A', 'AB', 'B', 'O'], dtype=object),
 array([14, 21, 30, 43, 54])]

# number型の　age もカテゴリ値になっている

In [14]: encoder.feature_names_in_
Out[14]: array(['sex', 'blood', 'age'], dtype=object)

In [15]: encoder.get_feature_names_out()
Out[15]:
array(['sex_F', 'sex_M', 'blood_A', 'blood_AB', 'blood_B', 'blood_O',
       'age_14', 'age_21', 'age_30', 'age_43', 'age_54'], dtype=object)

```
