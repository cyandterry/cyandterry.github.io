昨天写N-Queens时候遇到了一个巨sb的bug然后始终懒得de最后就去玩儿了, 今天查了一下资料再来看这个感觉还是有些收获, 记下.

起因是因为如下一段代码:

'''
def totalQueens(self, n):
	ret = 0
	self.totalNQueens_helper(n, [], ret)
	return ret
'''

然后在主函数里每次发现可行解后把ret自增. 调试的时候发现ret始终没有增加, 后来才意识到这是个sb的问题.

在参考答案的C代码里他ret用的是&ret, 所以每次都会自增(C这个变态的指针...), 于是直接抓过来想在python里用, 可是失败了.

Google了一下, Python用的是 Pass by Assignment, 和其他的语言不一样, 当发生
'''
a = 1
a = 2
'''
的时候, 第一行是让a refer一个值是1的object, 第二行是让a refer一个值是2的object. 所以对于N-Queens题目肯定会不行, ret += 1是让 ret refer一个值比原来的object大1的新object, 但是原来的ret还是refer老的object, 自然不会自增.

网上查的办法是refer mutable, 例如 list, dictionary这些, 这也是为什么之前都没有暴露出这样的问题, 以前写代码的时候, 要不然是用了global varible, 要不然就是用了dict或者list, 恰好躲过了这个...

还有另外一种解决办法就是在class init的时候, 用self.ret类似的东西来做global, 这样又不会影响安全性, 而且还算是创建了global variable.