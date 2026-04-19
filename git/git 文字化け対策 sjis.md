#文字コード #git
## 現象:
git diffが文字化けする
### 対策
.gitattributes ファイルを作成して以下を記述
```
*.asp diff=sjis
```

## 現象:
gitbashの git diff で以下のエラーがでて差分出力が中断してしまう。 
iconv: C:\Users\tuyosi\AppData\Local\Temp\git-blob-a19284/mdlxxx.ASP fatal: unable to read files to diff
### 対策
ターミナルで以下を実行
$ git config diff.sjis.textconv "iconv -f CP932 -t UTF-8"
