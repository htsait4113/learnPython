## 构造程序逻辑

### 1. 寻找“水仙花数”

```python
"""
找出100~999之间的所有水仙花数
水仙花数是各位立方和等于这个数本身的数
如: 153 = 1**3 + 5**3 + 3**3
"""
for num in range(100, 1000):
    low = num % 10
    mid = num // 10 % 10
    high = num // 100
    if num == low ** 3 + mid ** 3 + high ** 3:
        print(num)
```

```python
153
370
371
407
```

### 2. 寻找“完美数”

```python
"""
找出1~9999之间的所有完美数
完美数是除自身外其他所有因子的和正好等于这个数本身的数
例如: 6 = 1 + 2 + 3, 28 = 1 + 2 + 4 + 7 + 14
"""
import time
import math

for num in range(1, 10000):
    sum = 0
    for factor in range(1, int(math.sqrt(num)) + 1):
        if num % factor == 0:
            sum += factor
            if factor > 1 and num /factor != factor:
                sum += num / factor
    if sum == num:
        print(num)
```

```python
1
6
28
496
8128
```

### 3. “百钱百鸡”问题

```python
"""
求解《百钱百鸡》问题
1只公鸡5元 1只母鸡3元 3只小鸡1元 用100元买100只鸡
问公鸡 母鸡 小鸡各有多少只
"""
for x in range(0, 20):
    for y in range(0, 33):
        z = 100 - x - y
        if 5 * x + 3 * y + z / 3 == 100:
            print('公鸡: %d只, 母鸡: %d只, 小鸡: %d只' % (x, y, z))
```

```python
公鸡: 0只, 母鸡: 25只, 小鸡: 75只
公鸡: 4只, 母鸡: 18只, 小鸡: 78只
公鸡: 8只, 母鸡: 11只, 小鸡: 81只
公鸡: 12只, 母鸡: 4只, 小鸡: 84只
```

### 4. 生成“斐波拉切数列”

```python
"""
输出斐波那契数列的前20个数
1 1 2 3 5 8 13 21 ...
"""
a = 0
b = 1
for _ in range(20):
    a, b = b, a + b
    print(a, end=' ')
```

```python
1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765
```

### 5. Craps赌博游戏

```python
"""
Craps赌博游戏
玩家摇两颗色子 如果第一次摇出7点或11点 玩家胜
如果摇出2点 3点 12点 庄家胜 其他情况游戏继续
玩家再次要色子 如果摇出7点 庄家胜
如果摇出第一次摇的点数 玩家胜
否则游戏继续 玩家继续摇色子
玩家进入游戏时有1000元的赌注 全部输光游戏结束
"""
from random import randint

money = 1000
while money > 0:
    print('你的总资产为:', money)
    needs_go_on = False
    while True:
        debt = int(input('请下注: '))
        if debt > 0 and debt <= money:
            break
    first = randint(1, 6) + randint(1, 6)
    print('玩家摇出了%d点' % first)
    if first == 7 or first == 11:
        print('玩家胜!')
        money += debt
    elif first == 2 or first == 3 or first == 12:
        print('庄家胜!')
        money -= debt
    else:
        needs_go_on = True

    while needs_go_on:
        current = randint(1, 6) + randint(1, 6)
        print('玩家摇出了%d点' % current)
        if current == 7:
            print('庄家胜')
            money -= debt
            needs_go_on = False
        elif current == first:
            print('玩家胜')
            money += debt
            needs_go_on = False

print('你破产了, 游戏结束!')
```



