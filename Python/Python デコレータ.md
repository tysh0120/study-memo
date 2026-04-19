#tech/python #プログラミング
## 関数デコレータ、クラスデコレータ
関数定義、クラス定義の前に
@デコレータ名
をつける。

```
def trace(func):
	def _wrapper(*args, **kwargs):
		print('func start')
		ret = func(*args, **kwargs)
		print('func end')
		return ret
		
	return wrapper


@trace
def my_func():
	return True

# これは
# my_func = trace(my_func) を呼び出すのと同等

```