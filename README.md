# Finite-Field-Operation

---

### 概述

实现F_{2^N}有限域上的加法、求模、乘法、平方和求逆五种基本运算。N由method.hpp中的宏定义的```#define RANGE```决定，代码中设置的是131。
表示这是一个2^131的有限域。<br>

### 有限域的构建

这里推荐使用```GF2(unsigned int N,vector<int> f);```这个构造函数，第一个传的是一个10进制数，
表示在此有限域中的多项式；第二个参数表示传一个数组，该数组表示的是一个不可约多项式。比如一个[131,13,2,1,0]
的数组，表示这是一个 x^131 + x^13 + x^2 + x + 1 的不可约多项式，这里要求该多项式的最大度必须是N，
而且是一个不可约的多项式。若传入一个可约多项式，那么上诉五种运算就有可能出错。这样一个有限域F_{2^N}
中的多项式就构造完成了，能进行接下来的运算。

### 运算介绍

```
GF2<R> operator+(const GF2<R> &a);
GF2<R> multipy(const GF2<R> a);
GF2<R> square();
GF2<R> reduction(GF2<R> b);
GF2<R> inverse();
```

这五个函数分别表示实现了加法、乘法、平方、求模和求逆五种运算，一般调用也就只使用这五个函数。还有一个
``` void print_bit()```函数表示使用二进制串的形式输出当前的多项式。

---

这个有限域还有许多地方能够改进，而且运算功能比较少，不过还是能凑合着使用的。
