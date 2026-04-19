#tech/python #lib/sklearn 
[[ColumnTransformer]]
verbose_feature_names_out=Falseを指定する

```python
ColumnTransformer([
		('name1', transformer1, ['col1', 'col2']),
		('name2', transformer2, ['col3']),
	],
		remainder='passthrough',
		verbosee_feature_names_out=False   # POINT
)

## feature_names_outが
## 指定しない場合, ['name1__col1', 'name1__col2' 'name2__col3']
## 指定した場合    ['col1', 'col2', 'col3']
```
