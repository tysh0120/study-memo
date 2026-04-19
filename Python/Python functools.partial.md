引数を部分的に適用して少ない変数の関数を作成する
カーリー化

def raw_func(a,b,c):
    print(f"{a!r}, {b!r}, {c!r}")

raw_func(1,2,3)      # 1, 2, 3

先頭の引数に適用する場合は位置引数で指定可能
func1 = functools.partial(raw_func, 1,2)

func1(3)   # 1, 2, 3

先頭以外もキーワード引数で残せる
new_func = functools.partial(raw_func, a=1, c=3)

new_func(2)    # 1, 2, 3

