# .py / .pyc / .pyo
- 在一般情况下，我们所使用的python文件是py。这个格式是python的基础文件具有修改代码的能力。
- 但为了将这个解释性的文件转换成编译性文件，python官方也推出了`.pyc`和`.pyo`两种格式的文件。
- 这两种格式都是将python转换成二进制文件，让用户无法修改代码。
- 区别在于`.pyo`是`.pyc`的优化版，拥有更高的效率。

# .pyc的生成
```py
import py_compile

py_compile.compile("123.py")
```

# .pyc的生成
```terminal
python -0 -m py+compile 123.py
```

# 总结
- `.py`, `.pyc`, `.pyo`本质并没有区别，效果也一样，但是`.pyc`和`.pyo`的隐蔽性更好尤其当我们并不想开源代码时。
- 而当我们想要生成编译文件时，`.pyc`会是一个更优的选择，因为是优化版的`.pyo`。

# 参考文献
- [python .pyc .pyd .pyo文件的区别](https://zhuanlan.zhihu.com/p/429356020)
- [Python 文件类型（*.py/*.pyc/*.pyo](https://blog.csdn.net/liang19890820/article/details/68063946#:~:text=%2A.py%20%EF%BC%9A%E6%BA%90%E7%A0%81%E6%96%87%E4%BB%B6%EF%BC%8C%E7%94%B1%20Python%20%E7%A8%8B%E5%BA%8F%E8%A7%A3%E9%87%8A%E3%80%82,%2A.pyc%20%EF%BC%9A%E6%BA%90%E7%A0%81%E7%BB%8F%E7%BC%96%E8%AF%91%E5%90%8E%E7%94%9F%E6%88%90%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%88%B6%E5%AD%97%E8%8A%82%E7%A0%81%EF%BC%88Bytecode%EF%BC%89%E6%96%87%E4%BB%B6%E3%80%82%20%2A.pyo%20%EF%BC%9A%E4%BC%98%E5%8C%96%E7%BC%96%E8%AF%91%E5%90%8E%E7%9A%84%E7%A8%8B%E5%BA%8F%EF%BC%8C%E4%B9%9F%E6%98%AF%E4%BA%8C%E8%BF%9B%E5%88%B6%E5%AD%97%E8%8A%82%E7%A0%81%E6%96%87%E4%BB%B6%E3%80%82)
