## 循环结构

### 应用场景

在Python中构造结构有两种做法，一种是`for-in`循环，一种是`while`循环。

#### for-in循环

如果明确的知道循环执行的次数或者要对一个容器进行迭代，那么应该使用`for-in`循环。

```python
sum = 0
for x in range(101):
    sum += x
print(sum)
```

`range`可以用来产生一个不变的数值序列，而且这个序列通常都是用在循环中的，例如：

- `range(101)`可以产生一个0到100的整数序列。
- `range(1, 100)`可以产生一个1到99的整数序列。
- `range(1, 100, 2)`可以产生一个1到99的奇数序列，其中的2是步长，即数值序列的增量。

实现1~100之间的偶数求和。

```python
sum = 0
for x in range(2, 101, 2):
    sum += x
print(sum)
```

也可以通过在循环中使用分支结构的方式来实现相同的功能，代码如下。

```python
sum = 0
for x in range(1, 101):
    if x % 2 == 0:
        sum += x
print(sum)
```

#### while循环

如果要构造不知道具体循环次数的循环结构，推荐使用`while`循环。`while`循环通过一个能够产生或转换出`bool`值得表达式来控制循环，表达式的值为`True`循环继续，表达式的值为`False`循环结束。

```python
import random

answer = random.randint(1, 100)
counter = 0
while True:
    counter += 1
    number = int(input('请输入: '))
    if number < answer:
        print('大一点')
    elif number > answer:
        print('小一点')
    else:
        print('恭喜你猜对了!')
        break
print('你总共猜了%d次' % counter)
if counter > 7:
    print('你的智商余额明显不足')
```

通过嵌套的循环来输出一个九九乘法表。

```python
"""
输出乘法口诀表(九九表)
"""

for i in range(1, 10):
    for j in range(1, i + 1):
        print('%d*%d=%d' % (i, j, i * j), end='\t')
    print()
```

```python
1*1=1
2*1=2   2*2=4
3*1=3   3*2=6   3*3=9
4*1=4   4*2=8   4*3=12  4*4=16
5*1=5   5*2=10  5*3=15  5*4=20  5*5=25
6*1=6   6*2=12  6*3=18  6*4=24  6*5=30  6*6=36
7*1=7   7*2=14  7*3=21  7*4=28  7*5=35  7*6=42  7*7=49
8*1=8   8*2=16  8*3=24  8*4=32  8*5=40  8*6=48  8*7=56  8*8=64
9*1=9   9*2=18  9*3=27  9*4=36  9*5=45  9*6=54  9*7=63  9*8=72  9*9=81
```

打印三角形图案。

```python
"""
打印各种三角形图案

*
**
***
****
*****

    *
   **
  ***
 ****
*****

    *
   ***
  *****
 *******
*********
"""

row = int(input('请输入行数: '))
for i in range(row):
    for _ in range(i + 1):
        print('*', end='')
    print()


for i in range(row):
    for j in range(row):
        if j < row - i - 1:
            print(' ', end='')
        else:
            print('*', end='')
    print()

for i in range(row):
    for _ in range(row - i - 1):
        print(' ', end='')
    for _ in range(2 * i + 1):
        print('*', end='')
    print()
```

```python
*
**
***
****
*****
******
     *
    **
   ***
  ****
 *****
******
     *
    ***
   *****
  *******
 *********
***********
```

