#shell #文字コード
CRLFをCRにしてしまう
CRLFのファイルをsedで置換（sコマンド)すると、置換のかかった行の改行コードからCRが抜けてしまう。

やりかたとして、以下のように\rを補う方法がある
$ cat crlf.txt | sed 's/foo/bar/' | sed 's/$/\r/'
