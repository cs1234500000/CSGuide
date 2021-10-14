## Java基础

1. #### Java特点

   1. 面向对象（封装，继承，多态）

   2. 平台无关性（write once, run anywhere）

   3. 可靠，安全

   4. 支持多线程

   5. 支持网络编程

   6. 编译和解释并存

      

2. #### Java和C++区别

   1. 都是面向对象的语言（封装，继承，多台）

   2. C++支持指针，Java没有指针的概念

   3. C++支持多继承，Java不支持多重继承，但允许一个类实现多个接口

   4. 自动进行无用内存回收操作，不需要程序员主动删除；C++必须由程序员释放内存

   5. C++支持操作符重载，Java不支持

   6. Java取消了C++中的结构和联合

   7. C++不支持字符串变量，使用null表示字符串的终止。Java字符串是用类操作

   8. C++有goto语句，Java不支持

      

3. #### Java数据类型

   基本数据类型：byte(8), short(16), int(32), long(64), boolean(8), char(16), float(32), double(64)

   引用数据类型：class, interface, []

   

4. #### switch 是否能作用在 byte 上，是否能作用在 long ,String 上？

   switch(expr), expr可以是byte, short, char, int, enum, String

   long在目前所有版本都是不可以的

   

5. public, private, protected 及默认的区别？

   1. 默认：同一包内可见。使用对象：类，接口，变量，方法

   2. private：同一类可见。使用对象：变量，方法（不能修饰类）

   3. public：所有类可见。使用对象：类，接口，变量，方法

   4. protected：同一包内的类和所有子类可见。使用对象：变量，方法（不能修饰类）

      

6. #### final, finally, finalize的区别

   final用于修饰变量，方法和类

   1. final变量：被修饰的变量不可变，引用不可变，必须初始化，常量。
   2. final方法：被修饰的方法不允许任何子类重写，子类可以使用该方法
   3. final类：被修饰的类不能被继承，所有方法不能被重写

   finally作为异常处理的一部分，只能在try/catch中，并附带一个语句块表示这段语句最终一定被执行（无论是否抛出异常），经常被用在需要释放资源的情况下，System.exit(0)可以阻断finally执行

   finalize是java.lang.Object里定义的方法， 每个对象都有这个方法，在gc启动，回收时被调用。一个对象的finalize方法只会被调用一次，finalize被调用不一定会立即回收该对象 ，所以有可能调用 finalize 后，该对象又不需要被回收了，然后到了真正要被回收的时候，因为前面调用过一次，所以不会再次调用 finalize 了，进而产生问题，因此不推荐使用 finalize 方法。

   

7. #### static

   通常来说，用new创建类的对象时，数据存储空间才被分配，方法才供外界调用。但有时我们只想为特 定域分配单一存储空间，不考虑要创建多少对象或者说根本就不创建任何对象，再就是我们想在没有创 建对象的情况下也想调用方法。在这两种情况下，static关键字，满足了我们的需求。

   

8. #### Java中是否可以覆盖 (override)一个private或者是static的方法？

   Java中static方法不能被覆盖，因为方法覆盖是基于运行时动态绑定的，而static方法是编译时静态绑定 的。static方法跟类的任何实例都不相关，所以概念上不适用。

   

9. #### 是否可以在static环境中访问非static变量？ 

   static变量在Java中是属于类的，它在所有的实例中的值是一样的。当类被Java虚拟机载入的时候，会对 static变量进行初始化。如果你的代码尝试不用实例来访问非static的变量，编译器会报错，因为这些变 量还没有被创建出来，还没有跟任何实例关联上。

   

10. #### static静态方法能不能引用非静态资源？

    不能，new的时候才会产生的东西，对于初始化后就存在的静态资源来说，根本不认识它。

    

11. #### static静态方法里面能不能引用静态资源？

    可以，因为都是类初始化的时候加载的，大家相互都认识。 

    

12. #### 非静态方法里面能不能引用静态资源

    可以，非静态方法就是实例方法，那是new之后才产生的，那么属于类的内容它都认识。

    

13. #### Java静态变量、代码块、和静态方法的执行顺序是什么？

    静态变量 --> 静态方法 --> 代码块

    代码块执行顺序：静态代码块/静态变量（取决于编译顺序）--> 构造代码块 --> 构造器 -->普通代码块

    继承中：父类静态块—>子类静态块—>父类代码块—>父类构造器—>子类代码块—>子类构造器

    

14. #### Java如何实现多态？

    编译时多态（重载），运行时多态（继承，重写，向上转型）

    

15. #### 重载能否根据返回值进行区分？

    不能。float max(int a, int b), int max(int a, int b) 调用max(1,2)不知道是哪个方法

    

16. #### 构造器能否被重写？

    不能被重写，只能被重载

    

17. #### 抽象类和接口的区别是什么？

    语法层面上的区别： 

    1. 抽象类可以提供成员方法的实现细节，而接口中只能存在public abstract 方法； 
    2. 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是public static final类型的； 
    3. 接口中不能含有静态代码块以及静态方法，而抽象类可以有静态代码块和静态方法； 
    4. 一个类只能继承一个抽象类，而一个类却可以实现多个接口。 

    设计层面上的区别： 

    1. 抽象类是对一种事物的抽象即对类抽象（包括属性，行为），而接口是对行为（局部）的抽象。

    2. 抽象类是一种模板式设计。接口是一种行为规范，一种辐射式设计。

       

18. #### 抽象类能使用final修饰吗？

    不能，定义抽象类就是让其他类继承的，如果定义为 final 该类就不能被继承，这样彼此就会产生矛盾， 所以 final 不能修饰抽象类

    

19. #### Java 创建对象有哪几种方式？

    1. new创建新对象 

    2. 通过反射机制 

    3. 采用clone机制 （注意浅拷贝和深拷贝的区别）

    4. 通过序列化机制（Externalizable, Serializable）

       

20. #### 什么是不可变对象？

    对象一旦被创建，状态就不能再改变。任何修改都会创建一个新的对象比如String, Integer，等包装类，不可变对象最大的好处是线程安全

    

21. #### 能否创建一个包含可变对象的不可变对象？

    可以，比如`final Person[] persons = new person[]{}. `persons 是不可变对象的引用，但其数组中的Person实例却是可变的，这种情况下需要特别谨慎，不要共享可变对象的引用，这种情况下如果数据需要变化时，就返回原对象的一个拷贝。

    

22. #### 值传递和引用传递的区别是什么？为什么说Java中只有值传递？

    值传递：方法调用时，传递的参数是按值的拷贝传递，传递的是值得拷贝，也就是说传递后就互不相干了。

    引用传递：方法调用时，传递的参数是按引用传递，其中传递的是引用的地址，也就是变量所对应的内存空间的地址，传递的是值的引用。

    基本类型作为参数被传递时肯定是值传递；引用类型作为参数被传递时也是值传递，只不过“值”为对应的引用。

    

23. #### hashCode()，为什么要有hashcode？

    hashCode() 的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode()函数

    当你把对象加入 HashSet 时，HashSet 会先计算对象的 hashcode 值来判断对象加入的位置，同时也会 与其他已经加入的对象的 hashcode 值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。 但是如果发现有相同 hashcode 值的对象，这时会调用 equals()方法来检查 hashcode 相等的对象是否真的相同。如果两者相同，HashSet 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。这样我们就大大减少了 equals 的次数，相应就大大提高了执行速度。

    

24. #### 为什么重写equals必须重写hashcode？

    先根据hashcode进行的判断，相同的情况下再根据equals()方法进行判断。如果只重写了 equals方法，而不重写hashcode的方法，会造成hashcode的值不同，而equals()方法判断出来的结果为true。 在Java中的一些容器中，不允许有两个完全相同的对象，插入的时候，如果判断相同则会进行覆盖。这时候如果只重写了equals（）的方法，而不重写hashcode的方法，造成相同的对象散列到不同的位置而造成对象的不能覆盖的问题。

    

25. #### String 为什么设计成不可变的？

    1. 便于实现字符串池

    2. 使多线程安全

    3. 避免安全问题

       在网络连接和数据库连接中字符串常常作为参数，例如，网络连接地址URL，文件路径path，反射机制所需要的String参数。其不可变性可以保证连接的安全性。如果字符串是可变的，黑客就有可能改变字符串指向对象的值，那么会引起很严重的安全问题。

    4. 加快字符串处理速度

       由于String是不可变的，保证了hashcode的唯一性，于是在创建对象时其hashcode就可以放心的缓存了，不需要重新计算。这也就是Map喜欢将String作为Key的原因，处理速度要快过其它的键对象。所以 HashMap中的键往往都使用String。

       

26. #### 什么是字符串常量池？

    Java常量池：全局字符串常量池，class文件常量池，运行时常量池。

    jvm为了提升性能和减少内存开销，避免字符的重复创建，其维护了一块特殊的内存空间，即字符串 池，当需要使用字符串时，先去字符串池中查看该字符串是否已经存在，如果存在，则可以直接使用， 如果不存在，初始化，并将该字符串放入字符串常量池中。 

    字符串常量池的位置也是随着jdk版本的不同而位置不同。在jdk6中，常量池的位置在永久代（方法区） 中，此时常量池中存储的是对象。在jdk7中，常量池的位置在堆中，此时，常量池存储的就是引用了。 在jdk8中，永久代（方法区）被元空间取代了。

27. #### intern函数

    intern函数的作用是将对应的符号常量进入特殊处理，在JDK1.6以前 和 JDK1.7以后有不同的处理； 

    在JDK1.6中，intern的处理是 先判断字符串常量是否在字符串常量池中，如果存在直接返回该常 量，如果没有找到，则将该字符串常量加入到字符串常量区，也就是在字符串常量区建立该常量； 

    在JDK1.7中，intern的处理是 先判断字符串常量是否在字符串常量池中，如果存在直接返回该常 量，如果没有找到，说明该字符串常量在堆中，则处理是把堆区该对象的引用加入到字符串常量池中， 以后别人拿到的是该字符串常量的引用，实际存在堆中

    

28. #### 使用HashMap的时候，用String做key有什么好处？

    HashMap内部实现是通过Key的hashcode来确定value的存储位置，因为字符串是不可变的，所以创建字符串的时候，它的hashcode被缓存下来，不需要再次计算，相对于其他对象更快。

    

29. #### 包装类型和基本类型的区别

    原始类型：boolean, char, byte, short, int, long, float, double

    包装类型：Boolean, Character, Byte, Short, Integer, Long, Float, Double

    1. 包装类型可以为null，而基本类型不可以

    2. 包装类型可以用于泛型，基本类型不可以

    3. 基本类型比包装类型更有效。包装类型存储的是堆中的引用，占用更多的内存空间

       

30. #### 自动装箱和自动拆箱

    自动装箱：将基本类型转化为对象 `Integer num = 9;`

    自动拆箱：将对象重新转化为基本数据类型 `System.out.print(num--);`

    因为对象是不能直接进行运算的，需要转化为基本数据类型后才能加减乘除。

    

31. #### Integer变量和int变量的对比

    ```java
    int a = 10000;
    Integer b = new Integer(10000);
    Integer c = 10000;
    ```

    其中a=b, a=c 但是 b!=c 

    Integer和int变量比较时，会自动拆箱，只要两个变量的值相等，则结果为true。

    非new生成的Integer变量指向的事java常量池中的对象，new Integer()生成的变量是指向堆中新建的对象，两者在内存中的地址不同。

    

32. #### 两个非new生成的Integer对象的对比

    对于两个非new生成的Integer对象，进行比较时，如果两个变量的值在区间-128到127之间，则比较结 果为true，如果两个变量的值不在此区间，则比较结果为false.

    当值在 -128 ~ 127之间时，java会进行自动装箱，然后会对值进行缓存，如果下次再有相同的值，会直 接在缓存中取出使用。缓存是通过Integer的内部类IntegerCache来完成的。当值超出此范围，会在堆中 new出一个对象来存储。 给一个Integer对象赋一个int值的时候，会调用Integer类的静态方法valueOf，源码如下：

    ```java
    Integer i = 100;
    Integer j = 100;
    System.out.print(i == j); //true
    Integer i = 128;
    Integer j = 128;
    System.out.print(i == j); //false
    ```

    

33. #### 什么是反射？

    反射是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为 Java 语言的反射机制。

    

34. #### 反射机制的优缺点

    优点：能够运行时动态获取类的实例，提高灵活性；可与动态编译结合 Class.forName('com.mysql.jdbc.Driver.class'); ，加载MySQL的驱动类。

    缺点：使用反射性能较低，需要解析字节码，将内存中的对象进行解析。其解决方案是：通过 setAccessible(true)关闭JDK的安全检查来提升反射速度；多次创建一个类的实例时，有缓存会快很多； ReflflectASM工具类，通过字节码生成的方式加快反射速度。

    

35. 如何获取反射中的Class对象？

    1. Class.forName("类的路径")。当你知道该类的全路径名时，可以使用该方法获取Class类对象。

       ```java
       Class clz = Class.forNmae("java.lang.String");
       ```

    2. 类名.class。只适合在编译前就知道操作的Class

       ```java
       Class clz = String.class
       ```

    3. 对象名.getClass()。

       ```java
       String str = new String("Hello");
       Class clz = str.getClass();
       ```

    4. 如果是基本类型的包装类，可以调用包装类的Type属性来获得该包装类的Class对象。

       

36. #### Java反射API有几类？

    反射API 用来生成 JVM 中的类、接口或则对象的信息。 

    1. Class 类：反射的核心类，可以获取类的属性，方法等信息。 

    2. Field 类：Java.lang.reflec 包中的类，表示类的成员变量，用来获取和设置类之中的属性值。 

    3. Method 类：Java.lang.reflec 包中的类，类的方法，用来获取类中的方法信息或者执行方法。 

    4. Constructor 类：Java.lang.reflec 包中的类，表示类的构造方法。

       

37. #### 反射使用的步骤

    1. 获取想要操作的类的Class对象，这是反射的核心，通过Class对象我们可以任意调用类的方法
    2. 调用 Class 类中的方法，既就是反射的使用阶段。 
    3. 使用反射 API 来操作这些信息

    获取类的 Class 对象实例 

    ```java
    Class clz = Class.forName("com.zhenai.api.Apple");
    ```

    根据 Class 对象实例获取 Constructor 对象 

    ```java
    Constructor appleConstructor = clz.getConstructor();
    ```

    使用 Constructor 对象的 newInstance 方法获取反射类对象 

    ```java
    Object appleObj = appleConstructor.newInstance();
    ```

    

38. 为什么引入反射概念？反射机制的应用有哪些？ 

    从 Oracle 官方文档中可以看出，反射主要应用在以下几方面： 

    1. 反射让开发人员可以通过外部类的全路径名创建对象，并使用这些类，实现一些扩展的功能。 
    2. 反射让开发人员可以枚举出类的全部成员，包括构造函数、属性、方法。以帮助开发者写出正确的代码。 
    3. 测试时可以利用反射 API 访问类的私有成员，以保证测试代码覆盖率。 

    最常见的反射的例子：

    1. JDBC数据库的连接

       1. 通过Class.forName()加载数据库的驱动程序 （通过反射加载，前提是引入相关了Jar包）
       2. 通过 DriverManager 类进行数据库的连接，连接的时候要输入数据库的连接地址、用户名、密码； 
       3. 通过Connection 接口接收连接。

       ```java
       public static void main(String[] args) throws Exception {
           Connection con = null; //表示数据库的连接对象
           Class.forName(DBDRIVER); //1、使用CLASS 类加载驱动程序 ,反射机制的体现
           con = DriverManager.getConnection(DBURL,DBUSER,DBPASS); //2、连接数据库
           System.out.println(con);
           con.close(); // 3、关闭数据库
       }
       ```

    2. Spring框架的使用，最经典的xml配置模式

       Spring 通过 XML 配置模式装载 Bean 的过程： 

       1. 将程序内所有 XML 或 Properties 配置文件加载入内存中； 
       2. Java类里面解析xml或properties里面的内容，得到对应实体类的字节码字符串以及相关的属性信 息； 
       3. 使用反射机制，根据这个字符串获得某个类的Class实例； 
       4. 动态配置实例的属性。

       Spring这样做的好处是： 

       1. 不用每一次都要在代码里面去new或者做其他的事情； 

       2. 以后要改的话直接改配置文件，代码维护起来就很方便了； 

       3. 有时Java类里面不一定能直接调用另外的方法，可以通过反射机制来实现。

          

39. #### 反射机制的原理是什么？

    ```java
    Class actionClass=Class.forName(“MyClass”);
    Object action=actionClass.newInstance();
    Method method = actionClass.getMethod(“myMethod”,null);
    method.invoke(action,null);
    ```

    1. 类的装载，

    2. 链接和初始化

    3. 从class对象中获取到method对象

    4. 执行反射调用

       

40. #### Java中泛型是什么？

    将类型参数化，其在编译时才确定具体的参数。这种参数类型可以用在类，接口和方法的创建中，分别称为泛型类，泛型接口，泛型方法。

    

41. #### 使用泛型的好处是什么？

    不用泛型的话：

    1. 每次使用时都需要强行转化为想要的类型
    2. 在编译时编译器并不知道类型转化是否正常，运行时才知道，不安全

    泛型

    使用泛型的好处：

    1. 类型安全：

       编译时期就能检查出因Java类型不正确导致的ClassCastException

    2. 消除强制类型转换

    3. 潜在的性能收益

       不需要更改jvm或者类文件更改，所有的工作都在编译器完成，而不在运行阶段。

42. 

43. 

44. 

45. 

46. 

47. 

48. #### HashMap中key的存储索引是怎么计算出来的？

    首先根据key的值计算出hashcode的值，然后根据hashcode计算出hash值，最后通过hash&(length-1)计算出存储的位置。通过取模计算下标。(a%b=a&(b-1))

49. #### HashMap中put方法流程？

    1. 首先根据 key 的值计算 hash 值，找到该元素在数组中存储的下标； 

    2. 如果数组是空的，则调用 resize 进行初始化； 

    3. 如果没有哈希冲突直接放在对应的数组下标里； 

    4. 如果冲突了，且 key 已经存在，就覆盖掉 value； 

    5. 如果冲突后，发现该节点是红黑树，就将这个节点挂在树上； 

    6. 如果冲突后是链表，判断该链表是否大于 8 ，如果大于 8 并且数组容量小于 64，就进行扩容；如果链表节点大于 8 并且数组的容量大于 64，则将这个结构转换为红黑树；否则，链表插入键值 对，若 key 存在，就覆盖掉 value。

       

50. #### HashMap扩容机制

    HashMap 在容量超过负载因子所定义的容量之后，就会扩容。Java 里的数组是无法自动扩容的，方法 是将 HashMap 的大小扩大为原来数组的两倍，并将原来的对象放入新的数组中。

    JDK1.8做了两处优化 

    1. resize 之后，元素的位置在原来的位置，或者原来的位置 +oldCap (原来哈希表的长度）。不需要 像 JDK1.7 的实现那样重新计算hash ，只需要看看原来的 hash 值新增的那个bit是1还是0就好了， 是0的话索引没变，是1的话索引变成“原索引 + oldCap ”。这个设计非常的巧妙，省去了重新计算 hash 值的时间。
    2. JDK1.7 中 rehash 的时候，旧链表迁移新链表的时候，如果在新表的数组索引位置相同，则链表元 素会倒置（头插法）。JDK1.8 不会倒置，使用尾插法

    

51. #### 一般用什么作为HashMap的key？

    一般用Integer、String 这种不可变类当 HashMap 当 key，而且 String 最为常用。 

    1. 因为字符串是不可变的，所以在它创建的时候 hashcode 就被缓存了，不需要重新计算。这就是 HashMap中的键往往都使用字符串的原因。 

    2. 因为获取对象的时候要用到 equals() 和 hashCode() 方法，那么键对象正确的重写这两个方法是非常重要的,这些类已经很规范的重写了 hashCode() 以及 equals() 方法。

    

52. #### HashMap为什么线程不安全？

    1. 多线程下扩容死循环。JDK1.7中的 HashMap 使用头插法插入元素，在多线程的环境下，扩容的时候有可能导致环形链表的出现，形成死循环。因此，JDK1.8使用尾插法插入元素，在扩容时会保持链表元素原本的顺序，不会出现环形链表的问题。 

    2. 多线程的put可能导致元素的丢失。多线程同时执行 put 操作，如果计算出来的索引位置是相同 的，那会造成前一个 key 被后一个 key 覆盖，从而导致元素的丢失。此问题在JDK 1.7和 JDK 1.8 中都存在。 

    3. put和get并发时，可能导致get为null。线程1执行put时，因为元素个数超出threshold而导致 rehash，线程2此时执行get，有可能导致这个问题。此问题在JDK 1.7和 JDK 1.8 中都存在。

       

53. #### ConcurrentHashMap原理

    在数据结构上， JDK1.8 中的ConcurrentHashMap 选择了与 HashMap 相同的数组+链表+红黑树结 构；在锁的实现上，抛弃了原有的 <u>Segment 分段锁</u>，采用 <u>CAS + synchronized</u> 实现更加低粒度的 锁。 将锁的级别控制在了更细粒度的哈希桶元素级别，也就是说只需要锁住这个链表头结点（红黑树的根节 点），就不会影响其他的哈希桶元素的读写，大大提高了并发度。

    

54. #### ConcurrentHashMap的put方法执行逻辑？

    1. 根据 key 计算出 hash值。 

    2. 判断是否需要进行初始化。 

    3. 定位到 Node，拿到首节点 f，判断首节点 f： 

       1. 如果为 null ，则通过**CAS**的方式尝试添加。 
       2. 如果为 f.hash = MOVED = -1 ，说明其他线程在扩容，参与一起扩容。 
       3. 如果都不满足 ，**synchronized** 锁住 f 节点，判断是链表还是红黑树，遍历插入。

    4. 当在链表长度达到8的时候，数组扩容或者将链表转换为红黑树。

       

55. ####  ConcurrentHashMap是否需要加锁？

    get 方法不需要加锁，put需要加锁。因为 Node 的元素 val 和指针 next 是用 volatile 修饰的，在多线程环境下线程A修改结点的val或者新增节点的时候是对线程B可见的。 这也是它比其他并发集合比如 Hashtable、用 Collections.synchronizedMap()包装的 HashMap 安全效率高的原因之一。

    ```java
    static class Node<K,V> implements Map.Entry<K,V> {
    final int hash;
    final K key;
    //可以看到这些都用了volatile修饰
    volatile V val;
    volatile Node<K,V> next;
    }
    ```

    

56. #### get方法不需要加锁与volatile修饰的哈希桶有关吗？

    没有关系。哈希桶 table 用volatile修饰主要是保证在数组扩容的时候保证可见性。

    ```java
    static final class Segment<K,V> extends ReentrantLock implements Serializable {
    // 存放数据的桶
    transient volatile HashEntry<K,V>[] table;
    ```

    

57. #### ConcurrentHashMap 不支持 key 或者 value 为 null 的原因？

    value 为什么不能为 null ，因为 ConcurrentHashMap 是用于多线程的 ，如果 map.get(key) 得到了 null ，无法判断，是映射的value是 null ，还是没有找到对应的key而为 null ， 这就有了二义性。 

    而用于单线程状态的 HashMap 却可以用 containsKey(key) 去判断到底是否包含了这个 null 。 

    假设ConcurrentHashMap 允许存放值为 null 的value，这时有A、B两个线程，线程A调用 ConcurrentHashMap .get(key)方法，返回为 null ，我们不知道这个 null 是没有映射的 null ，还是存 的值就是 null 。 假设此时，返回为 null 的真实情况是没有找到对应的key。那么，我们可以用ConcurrentHashMap .containsKey(key)来验证我们的假设是否成立，我们期望的结果是返回false。 但是在我们调用ConcurrentHashMap .get(key)方法之后，containsKey方法之前，线程B执行了 ConcurrentHashMap.put(key, null )的操作。那么我们调用containsKey方法返回的就是true了，这就与我们的假设的真实情况不符合了，这就有了二义性。

    

58. #### ConcurrentHashMap的并发度是多少？

    并发度默认是16，可以在构造函数中设置。会使用大于等于该值的2^n。比如17，并发度是32

    

59. #### ConcurrentHashMap迭代器是强一致性还是弱一致性？

    HashMap是强一致性，ConcurrentHashMap是弱一致性。

    ConcurrentHashMap 的迭代器创建后，就会按照哈希表结构遍历每个元素，但在遍历过程中，内部元素可能会发生变化，如果变化发生在已遍历过的部分，迭代器就不会反映出来，而如果变化发生在未遍历过的部分，迭代器就会发现并反映出来，这就是弱一致性。 这样迭代器线程可以使用原来老的数据，而写线程也可以并发的完成改变，更重要的，这保证了多个线程并发执行的连续性和扩展性，是性能提升的关键。

    

60. #### JDK1.7与JDK1.8 中ConcurrentHashMap 的区别？

    数据结构：取消了Segment分段锁的数据结构，取而代之的是数组+链表+红黑树的结构。 

    保证线程安全机制：JDK1.7采用Segment的分段锁机制实现线程安全，其中segment继承自 ReentrantLock。JDK1.8 采用CAS+Synchronized保证线程安全。 

    锁的粒度：原来是对需要进行数据操作的Segment加锁，现调整为对每个数组元素加锁 （Node）。 

    链表转化为红黑树:定位结点的hash算法简化会带来弊端,Hash冲突加剧,因此在链表节点数量大于8 时，会将链表转化为红黑树进行存储。 

    查询时间复杂度：从原来的遍历链表O(n)，变成遍历红黑树O(logN)。

    

61. #### ConcurrentHashMap 和Hashtable的效率哪个更高？为什么？

    ConcurrentHashMap 的效率要高，因为Hashtable使用synchronized给整个哈希表加了一把大锁从而实现线程安全。而ConcurrentHashMap 的锁粒度更低，在JDK1.7中采用分段锁实现线程安全，在JDK1.8 中采 用 CAS+Synchronized 实现线程安全。

    

62. #### 多线程下安全的操作 map还有其他方法吗？

    如果传入的是 HashMap 对象，其实也是对 HashMap 做的方法做了一层包装，里面使用对象锁来保证多线程场景下，线程安全，本质也是对 HashMap 进行全表锁。在竞争激烈的多线程环境下性能依然也非常差，不推荐使用！

    我们在调用这个方法的时候就需要传入一个Map，可以看到有两个构造器，如果你传入了mutex参数，则将对象排斥锁赋值为传入的对象。

    如果没有，则将对象排斥锁赋值为this，即调用synchronizedMap的对象，就是上面的Map。

    创建出synchronizedMap之后，再操作map的时候，就会对方法上锁.

    ```java
    private static class SynchronizedMap<K,V> implements Map<K,V>, Serializable {
    	private static final long serialVersionUID = 1978198479659022715L;
    	private final Map<K,V> m; // Backing Map
    	final Object mutex; // Object on which to synchronize
    	SynchronizedMap(Map<K,V> m) {
    		this.m = Objects.requireNon null (m);
    		mutex = this;
    	}
    	SynchronizedMap(Map<K,V> m, Object mutex) {
    		this.m = m;
    		this.mutex = mutex;
    	}
    // 省略部分代码
    }
    ```

    

63. #### HashMap和HashSet的区别

    HashMap实现了Map接口，HashSet实现了set接口。利用hashcode判断对象是否相等。

    HashSet的实现：HashSet的底层其实就是HashMap，只不过我们HashSet是实现了Set接口并且把数据作为K值，而V值一直使用一个相同的虚值来保存。

    

64. #### Collection框架中实现比较要怎么做？

    1. 实现类实现Comparable接口，并实现compareTo(T t)方法，称为内部比较器。
    2. 创建一个外部比较器，要实现Comparator接口的compare(T t1, T t2)

    ```java
    class Student implements Comparable<Student> {
        String name;
        Integer age;
    
        Student(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        @Override
        public int compareTo(Student o2) {
            //降序
            return this.getAge().compareTo(o2.getAge());
        }
    }
    
    class ComparatorTest2 implements Comparator<Student> {
    
        public static void main(String[] args) {
            Student xiaoming = new Student("xiaoming", 20);
            Student xiaohong = new Student("xiaohong", 21);
            Student xiaogang = new Student("xiaogang", 19);
            List<Student> list = new ArrayList<>();
            list.add(xiaohong);
            list.add(xiaoming);
            list.add(xiaogang);
            System.out.println("已重写后的list --->>>" + list);
    
            ComparatorTest2 comparatorTest = new ComparatorTest2();
            System.out.println("自定义比较--->>>"+comparatorTest.compare(xiaoming, xiaohong));
        }
    
        //重写compare方法，用于单独比较
        @Override
        public int compare(Student o1, Student o2) {
            return o1.getAge().compareTo(o2.getAge());
        }
    }
    ```

    

65. #### Iterator 和 ListIterator 有什么区别？

    遍历。使用Iterator，可以遍历所有集合，如Map，List，Set；但只能在向前方向上遍历集合中的 元素。 

    使用ListIterator，只能遍历List，但可以向前和向后遍历集合中的元素。 

    1. 添加元素。Iterator无法向集合中添加元素；而ListIteror可以向集合添加元素。 

    2. 修改元素。Iterator无法修改集合中的元素；而ListIterator可以使用set()修改集合中的元素。 

    3. 索引。Iterator无法获取集合中元素的索引；而ListIterator，可以获取集合中元素的索引。

       

66. #### 快速失败和安全失败

    快速失败（fail—fast） 

    1. 在用迭代器遍历一个集合对象时，如果<u>遍历过程中对集合对象的内容进行了修改</u>（增加、删除、修 改），则会抛出Concurrent Modification Exception。 
    2. 原理：迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。 集合在被遍历期间如果内容发生变化，就会改变modCount的值。每当迭代器使用 hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值， 是的话就返回遍历；否则抛出异常，终止遍历。  
    3. 注意：这里异常的抛出条件是检测到 modCount！=expectedmodCount 这个条件。如果集合发生 变化时修改modCount值刚好又设置为了expectedmodCount值，则异常不会抛出。因此，不能依 赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的bug。 
    4. 场景：java.util包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修 改），比如HashMap、ArrayList 这些集合类。 

    安全失败（fail—safe)

    1. 采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是<u>先复制原有集合内 容，在拷贝的集合上进行遍历</u>。  

    2. 原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发Concurrent Modification Exception。  

    3. 缺点：基于拷贝内容的优点是避免了Concurrent Modification Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。  

    4. 场景：java.util.concurrent包下的容器都是安全失败，可以在多线程下并发使用，并发修改，比如：ConcurrentHashMap。

       

67. #### 如何提高ConcurrentHashMap的插入效率

    1. 扩容操作。主要还是要通过配置合理的容量大小和负载因子，尽可能减少扩容事件的发生。

    2. 锁资源的争夺，在 put 方法中会使用 synchonized 对首节点进行加锁，而锁本身也是分等级的，因此我们的主要思路就是尽可能的避免锁升级。我们可以将数据通过 ConcurrentHashMap 的 spread 方法进行预处理，这样我们可以将存在哈希冲突的数据放在一个桶里面，每个桶都使用单线程进行 put 操作，这样的话可以保证锁仅停留在偏向锁这个级别，不会升级，从而提升效率。

       

68. #### ConcurrentHashMap 是否存在线程不安全的情况？如果存在的话，在什么情况下会出现？如何解决？

    ![ConcurrentHashMap线程不安全](C:\Users\chens\OneDrive\桌面\面试题\CS Notes\ConcurrentHashMap线程不安全.jpg)

    原因就在于这三行在一起不是线程安全的，虽然 get 方法和 put 方法是线程安全的，但是中间的又对获取的值修改了，因此导致线程不安全。

    解决方法是使用 replace 方法

    `scores.replace(key:"Jogn",score, newScore);`

    

