#tech/python  #プログラミング

\_\_init\_\_() 関数内で 親クラスの \_\_init\_\_() を呼び出す必要があるが、
親クラスのクラス名を直接記述してしまうとダイアモンド継承が発生

         A
    　  /　　\
    B          C
        \ /
          D

```
class A:
    def __init__(self):
	    print('A')

class B(A):
	def __init__(self):
		print('B')
		A.__init__(self)

class C(A):
	def __init__(self):
		print('C')
		A.__init__(self)

class D(B, C):
	def __init__(self):
		print('D')
		B.__init__(self)
		C.__init__(self)

# 実行結果
# D
# B
# A
# C
# A  <- Aが重複して呼ばれてしまっている

```

  super() を使用して親クラスを参照すれば、mro に応じた順に重複なく呼ばれる。（チェーン）
```
class A:
	def __init__(self):
		print('A')

class B(A):
	def __init__(self):
		print('B')
		super().__init__(self)

class C(A):
	def __init__(self):
		print('C')
		super().__init__(self)

class D(A):
	def __init__(self):
		print('D')
		super().__init__(self)

# 実行結果
# D
# B
# C
# A
```
  
  クラス名.\_\_mro\_\_ で参照できる
```
In []  A.__mro__
Out[]  (__main__.D, __main__.B, __main__.C, __main__.A, object)
```

