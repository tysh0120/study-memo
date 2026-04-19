#tools/git

昔のバージョンのソースを見たいとき

```bash
git show コミットバージョン:path/to/file

```

ページャでなく標準出力に出したいとき  git の --no-pager オプションを指定すればよい。
例えば標準出力でiconvにパイプしたいときなど。

```
git --no-pager show xxxxx | iconv -f cp932 -t utf-8
```
