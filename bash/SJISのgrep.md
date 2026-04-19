### 簡易的
LANG=ja_JP.SJIS grep "検索語" ファイル名

### 単一ファイル
	iconv -f SHIFT_JIS -t UTF-8 | grep "検索語"
### 複数ファイル
```sh
	find . -type f -name "*.txt" -print0 \
	  | xargs -0 -I{} sh -c 'iconv -f CP932 -t UTF-8 "{}" \
	  | grep "検索語 && echo {}" /dev/stdin'
```

##### find の -print0オプション: 
 NULL文字で終わるフルファイル名を表示。    xargs の-0オプションで使用

##### xargsの -0 オプション
 NULL区切りの入力受け付ける

##### xargsの -I オプション
-I の後ろの文字をプレイスホルダにする。　{} を使用するのが慣例
例）
```sh
echo file1.txt | xargs -I@ cat @
 # cat file1.txt と同等
```