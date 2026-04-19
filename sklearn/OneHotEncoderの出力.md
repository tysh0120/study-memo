#tech/python #lib/sklearn 
OneHotEncoderの出力をStandardScalerに掛けたら ValueError となった

##### 原因
OneHotEncoderの出力がsparse matrixのため、値のない所に対して平均を引く演算ができない。
→ エラーメッセージに出てくるように、StandardScalerのオプション with_mean=False にするとエラーは消えるが、、、

##### そもそもやってはいけない
OneHotEncoder の出力は0/1のフラグ値
StandardScalerに掛けると、プラスとマイナスの値をとり、頻度が高いと値も小さくなる。
大きさは意味を持たないため、不要な情報を与えてしまう

##### 結論
OneHotEncoderの出力は、StandardScalerに掛けずにそのまま使用する。
