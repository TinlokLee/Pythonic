# Pythonic

# 列表推导式
lst = [i for i in "daadaijifaf"]


# 字典推导式
dic = {"a":1,"b":2,"c":3,"d":4}
double_dic = {k:v*2 for (k,v) in dic.items()}


# 集合推导式
se = {1,2,3,4}
double_se = {i*2 for i in se}


# 合并字典
x = {"a":1, "b":2}
y = {"c":3, "d":4}
x_y = {**x, **y}


# 复制列表
l = [1,2,3]
l[::]
copy_l = l[::]


# 反转列表
reverse_l = l[::-1]


# 变量交换
a, b = b, a


# 拆包
a, *b, c= 1,2,3,4
a # 1
b # [2,3]
c # 4


# 函数返回多个值
def foo():
    return 1,2,3

a,b,c = foo()
print(a,b,c)


# 列表合并成字符串
str_l = ''.join(['nihao','china'])


# 链式比较
if a > 2 and a < 5:
    pass

def dup(n):
    for i in range(n):
        yield i
        # yield from[i,i]


# 字典代替多个if else
def foo(x):
    if x == 'a':
        return 1
    elif x == 'b':
        return 2
    else:
        return None

def foo(x):
    return {"a":1, "b":2}.get(x)


# 有下标索引的枚举
for (i, e) in enumerate(["a","b","c"]):
    print(i, e)


# zip()函数应用
m = [[1,2,3], [4,5,6], [7,8,9]]
n = [[2,2,2], [3,3,3], [5,6,6]]
# 矩阵相加减
print([x+y for a, b in zip(m, n) for x, y in zip(a, b)])
print('-*'*10 + '矩阵相加减' + '-*'*10)

# 矩阵点乘
print([x*y for a, b in zip(m, n) for x, y in zip(a, b)])


# .format
name = "lee"
age = 22
born_in = "xx, china"
string = "Hello my name is {0} and I'm {1} years old. I was born in {2}."\
            .format(name, age, born_in) 
print(string)


# 返回元祖（多个元素）
def binary(): 
    return 0, 1
# 要是你需要所有的元素被返回，用个下划线_
zero, one, _ = binary()



# 访问字典
countr = {} 
bag = [2, 3, 1, 2, 5, 6, 7, 9, 2, 7] 
for i in bag: 
    countr[i] = countr.get(i, 0) + 1
for i in range(10): 
    print("Count of {}: {}".format(i, countr.get(i, 0)))

bag = [2, 3, 1, 2, 5, 6, 7, 9, 2, 7] 
countr = dict([(num, bag.count(num)) for num in bag])
for i in range(10): 
    print("Count of {}: {}".format(i, countr.get(i, 0)))


# 列表切片
bag = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 
for elem in bag[::2]: 
    print(elem)
# 或者用 range()
bag = list(range(0,10,2)) 
print(bag)



# 注意区分列表推导式，生成器效率更高
g = (i**2 for i in range(10))
for i in g:
    print(i)


# 列表中出现次数最多的元素
l = [1,1,2,3,4,4,4,5]
max_l_count = max(set(l), key=l.count)

from collections import Counter 
Counter(l).most_common()[0][0]


# 文件读写
with open("test.txt", "w") as f:
      f.writelines("hello")


# 断对象类型，可指定多个类型
isinstance(a, (int, str))

# 类似的还有字符串的 startswith，endswith
"http://foofish.net".startswith(('http','https'))



# __str__ 与 __repr__ 区别
str(datetime.now())
#'2018-11-20 00:22:54.839605'
repr(datetime.now())
'datetime.datetime(2018, 11, 20, 0, 22, 0, 579521)'
# 前者对人友好，可读性更强，后者对计算机友好，支持 obj == eval(repr(obj))



# 装饰器
def makebold(f):
    return lambda: "<b>" + f() + "</b>"
def makeitalic(f):
    return lambda: "<i>" + f() + "</i>"

@makebold
@makeitalic
def say():
    return "Hello"
print(say())
