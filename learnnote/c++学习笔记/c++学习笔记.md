###冒号与双冒号的用法
####冒号
1. 表示机构内位域的定义（即该变量占几个bit空间）
   例： unsigned char a:4
2. 构造函数后面的冒号起分割作用，是类成员变量赋值的方法，初始化列表，更适用于成员变量的常量const型。
   例：某类():某成员变量(赋值){} //构造函数
3. public:和private:后面的冒号代表所有的成员都是共有的或者私有的。直到下一个public:或private：为止。private:为默认处理。
4. 类名后面的冒号是用来定义类的继承的。
   例： class 派生类名:继承方式 基类名{派生类成员} //继承方式:public,private,protected
####双冒号
1. 表示域操作符
   例：声明了一个类A，在类中声明了一个成员函数 void f()，但没有在类的声明给出定义，那么在类外定义时，要写成void A::f(),表示f()函数是类A的成员函数。
2. 直接用在全局函数前，表示是全局函数
   例： 调用API函数时，在API函数名前加::
3. 表示引用成员函数及变量，作用域成员运算符。
   例：System::Math::Sqrt() 相当于System.Math.Sqrt()