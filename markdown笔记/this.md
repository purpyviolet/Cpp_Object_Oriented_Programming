this简单来说就是指向正在使用某些类函数的对象本身

```c++
#include <iostream>
using namespace std;
class A {
public:
    A(int x) : a(x) {}//不是const,只是普通的构造函数

    A& largerOne(A& x) {
        if (x.a > a)
            return x;
        else
            return *this; // 返回当前对象的引用
        //看看main函数谁执行了这个函数，如果是a1，那就返回a1的引用
    }

private:
    int a;
};

//int main() {
//    A a1 = 1;
//    A a2 = 2;
//    a1.largerOne(a2);
//    a2.largerOne(a1);
//}

//这里哪个对象调用的含有*this返回值的函数，这个*this最终就代表了这个对象
```

