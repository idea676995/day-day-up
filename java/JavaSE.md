# JavaSE

##  jvm  jre jdk



### jvm

 java的虚拟机。可以运行.class文件

### jre 

 java的运行环境，其中包括了jvm 和java核心类库和支持文件

### jdk

JDK是 [Java](https://baike.baidu.com/item/Java/85979) 语言的[软件开发工具包](https://baike.baidu.com/item/%E8%BD%AF%E4%BB%B6%E5%BC%80%E5%8F%91%E5%B7%A5%E5%85%B7%E5%8C%85/10418833)，主要用于[移动设备](https://baike.baidu.com/item/%E7%A7%BB%E5%8A%A8%E8%AE%BE%E5%A4%87/9157757)、[嵌入式设备](https://baike.baidu.com/item/%E5%B5%8C%E5%85%A5%E5%BC%8F%E8%AE%BE%E5%A4%87/10055189)上的java应用程序。JDK是整个java开发的核心，它包含了JAVA的运行环境（JVM+Java系统类库）和JAVA工具

## java运行流程

​	首先是源文件 .java  通过编译器产生 .class 文件，classloader类加载器把文件从本体加载到内存方法区中，再通过解释器进行执行。

​	java跨平台的是编译后的.class文件，而不是java文件 

​	编译期间的异常是受查异常 Exception 

​        解释执行期间的异常是非受查异常 RuntimeException

## Java数据类型

### Java基本类型

|                 数据类型                 | 所占字节（byte） |                   取值范围byte                    |
| :--------------------------------------: | :--------------: | :-----------------------------------------------: |
|              byte(字节类型)              |        1         |                     -128~127                      |
|            boolean(布尔类型)             |     1（1/8）     |                    true/false                     |
|              short(短整型)               |        2         |                   -32768~32767                    |
|              char(字符类型)              |        2         | 统一采用unicode编码 0='48' a='97' A='65' '\u0000' |
|       int(整型)(java整数默认类型)        |        4         |              -2147483648~2147483647               |
|       float(单精度浮点数类型) F/f        |        4         |                 范围比long类型大                  |
|              long(长整型) L              |        8         |                   -2^63~2^63-1                    |
| double(双精度浮点型)(java浮点数默认类型) |        8         |                                                   |

### 注意

*  八大基本类型值的比较只能使用  ==  [ 栈空间存储]
* 变量本质 ：  栈内存地址别名

## String 类型

 字符序列   '1'+'2'+'3'='123'

## Java引用类型

  数组 枚举enum  自定义类  

### 枚举类型enum

```java
/**
 * 枚举类
 * 	优点 ： 构造方法天生私有
 *  作用 ： 管理一组相关的常量
 *  命名规范 ： 所有字母都大写
 枚举里面可以写静态方法什么的  也可以进行方法的重写  可以直接变成策略模式
 *
 */
//RED，GREEN，YELLOW都是类Color的一个实例对象
//枚举也可以实现单例，但是可以别很多替代
public enum Color {
	RED("红灯"),GREEN("绿灯"),YELLOW("黄灯");
	
	private String msg; // 存放常量对应的信息
	private Color(String msg) {
		this.msg = msg;
	}
	
	public String getVal() {
		return msg;
	}
}
```





### 注意

* 包装类型与基本类型的区别为   包装类型可以存放null值  null相当于一个占位符  其在数据库中的语义可以代表不同的意思

* 任何类型+字符串类型都会变为字符串类型 

* Java中类型可以自动转换  小转大 自动转    大转小需要强制转换（类型）变量 

* 进行类型转换的时候要注意取值范围 不要内存泄漏

  

## Java运算符

### 基本运算符

* `+`  加法运算

* `-`  减法运算

* `*` 乘法运算

* `/` 除法运算  5/2=2 

* `%` 取余运算  5%2=1

* ^ 异或运算 

* <<  或者 >> 移位运算    左移1位等于乘2  右移一位等于除以2    2<<1=4     2>>1=1

  

### 逻辑运算符

* `||` 逻辑或运算  短路或  当第一个条件为真时 第二个条件跳过   非短路或运算 |

* &&  逻辑与运算   短路与  当第一个条件为假时  第二个条件跳过  非短路与运算 &

* ! 逻辑非运算 

* ？ 三目运算符 条件成立执行第一个结果 不成立执行第二个结果   row>1? "第一个条件":"第二个条件"

  

## Java条件判断语句

*  if (条件){代码}   其中{} 可以省略
*  if(条件){代码}else{代码}
*  f(条件){代码}else if(条件){代码}else{代码}
*  switch （变量）其中变量只能放 byte short int enum String 五种类型

## Java循环语句

循环条件  循环体  循环次数

* for 循环 死循环 for(;;)   

* while 循环 死循环  while(1>0)

* do while 循环 至少先执行一次循环体

  

  

  

  ```java
  //continue与break  
  //break是立即跳出当前循环体
  //continue 是跳过本次循环，立即执行下次
  // 可以指定跳出和 需要再循环千加标记
  a:for(int i=0;i<10;i++){
      b:for(int j=0;j<10;j++){
          continue b;
          break a;
          
      }
  }
  ```

  ### 递归与循环优缺点

  

  ```java
  //优缺点分析
  //递归
  /*虽然有代码简洁的优点，但是时间和空间消耗比较大。每一次函数调用都需要在内存栈中分配空间以保存参数，返回地址以及临时变量，而且往栈里面压入数据和弹出都需要时间。 
  另外递归会有重复的计算。递归本质是把一个问题分解为多个问题，如果这多个问题存在重复计算，有时候会随着n成指数增长。斐波那契的递归就是一个例子。 
  递归还有栈溢出的问题，每个进程的栈容量是有限的。
  
  循环
  代码可读性不如递归 
  但是效率更高*/
  ```

  堆收gc管理，栈随方法作用域释放

  

  

 ## Java 集合 

### 线程安全容器

```java
       //线程安全的容器
        CopyOnWriteArrayList<Object> list = new CopyOnWriteArrayList<>();
        CopyOnWriteArraySet<Object> set = new CopyOnWriteArraySet<>();
        ConcurrentHashMap<Object, Object> map = new ConcurrentHashMap<>();
        ConcurrentSkipListMap<Object, Object> listma = new ConcurrentSkipListMap<>();
        //使用了跳表 并发越多比concurrtHashMAP越有优势
        //其key是有序的
        HashMap<Object, Object> hash = new HashMap<>();
		vector等
```



LinkedList 是双端队列链表结构  可以直接在头和尾添加

```java
//集合的遍历
   ArrayList<Integer> arr = new ArrayList<>();
        arr.add(1);
        arr.add(4);
        arr.add(4);
        arr.add(8);
        arr.add(8);
        arr.add(11);
        arr.add(100);
        for (int i = 0; i < arr.size(); i++) {
            if (4==arr.get(i)){
                arr.remove(i);
            }

        }
        for (Integer i : arr) {
               System.out.println(i);
           }
        }
//指针删除的时候集合索引缩进了一位，所以如果连着的话会跳过下一个
//倒着删除
        for (int i =arr.size(); i <= 0; i++) {
           if (4==arr.get(i)){
               arr.remove(i);
            }

        }
//使用迭代器删除
  Iterator<Integer> iterator = arr.iterator();
        while (iterator.hasNext()){
            if (iterator.next()==4){
                iterator.remove();
            }
        }
//listiterator 迭代器比iterator更加强大
ListIterator<Integer> iter = arr.listIterator();
//可以向前或者向后，也可以返回相应的索引
//使用增强for循环的时候不能同时进行删除等操作，在迭代前就确定了集合的长度，进行删除操作后，长度变了，不一致了就会报错 但是如果是删除倒数第二个元素就不会报错
//正着删
        for (int i =arr.size(); i <= 0; i++) {
            if (4==arr.get(i)){
                arr.remove(i);
                i--;
           }

        }

```



### 集合框架

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固1\图解\集合框架.png)

 

### 数组结构

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固1\图解\数组.png)

### Hash结构

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固1\图解\Hash结构.png)

### 链表

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固1\图解\链表.png)

### 二叉树

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固1\图解\二叉树.png)

### 红黑树

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固1\图解\红黑树.png)

## 匿名内部类

```java
//匿名内部类实现了接口或者继承了父类
```



## 冒泡排序与选择排序

```java
int [] arr={1,2,3,4,5,6,7,8,9,10};
		//冒泡排序
		for (int i=1;i<=arr.length;i++){ //控制循环的轮数
			for (int j=0;j<arr.length-i;j++){ //控制循环的次数，最后位置被确定
				if(arr[j]<arr[j+1]){
					int temp=arr[j];
					arr[j]=arr[j+1];
					arr[j+1]=temp;
				}
			}
		}
		System.out.println(Arrays.toString(arr));
		System.out.println("---------------------------------------");
		int [] brr={1,2,3,4,5,6,7,8,9,10};
		//选择排序
		//从第一个开始排序，与它之后的所有进行比较，比较之后，位置被确定
		for (int i=0;i<brr.length;i++){
			for (int j=i+1;j<brr.length;j++){
				if (brr[j]>brr[i]){
					int temp=brr[i];
					brr[i]=brr[j];
					brr[j]=temp;
			}
			}
		}
		System.out.println(Arrays.toString(brr));
	}
```

## 快速排序

快速排序其本质是分而治之的思想

选一个数作为基准数  一般为第一个数 起始位基准位

 排一次顺序  把比基准数小的都放在左边  把比基准数大的都放在右边

通过循环 控制   从右侧测游标检查  检查到比基准数小的  就与基准位调换位置  左侧游标向右移动一位  然后轮到左侧游标开始检查

左侧游标检查到比基准数大的  就与上一步调过去的基准位也就是右侧游标 互换位置  右侧游标向左移动一位 

反复这个过程  知道左侧游标大于右侧游标

其中有可能有极端情况  就是基准数已经是最大的了  右侧检查后 右侧游标等于了左侧游标  此时就不用排序了  跳出循环

左侧检查相同

排好顺序后 通过基准数 把数组分为两组 然后两组 重复排序的过程  调用方法本身  递归

递归调用的时候判断下  是否符合继续递归调用的条件  左游标-1是否小于等于最右侧游标    右游标是否大于等于最右侧游标

  最后当左右开始的游标相等时，就意味着 其只剩一个数了  就不用排序了 直接返回就可以了  

```java
//方法
 public static void quickSort(int[] array,int low,int heigh){
        //记录起始的左右游标
        int left=low;
        int right=heigh;
      int key=array[low];
      //开始排序
       while (low<heigh){
           //开始从右侧往左侧 检索  当检测到有小于 基准的退出循环
           while(array[heigh]>key){
               heigh--;
           }
           //如果两边的游标相等 说明key已经是最小的了 不用排序了
           if (low==heigh){
               break;
           }
           //交换基准与右侧检索到的小于key的位置
           int temp=array[low];  //也就是基准
           array[low]=array[heigh];
           array[heigh]=temp;
           low++;
           //判断 如果此时low大于heigh 说明一轮就结束了
           if(low==heigh){
               break;
           }
           //开始从左侧往右侧检索 当检测到有大于基准的 退出循环
           while (array[low]<key){
               low++;
           }
           //如果左侧游标等于右侧游标 说明第一次交换后就是最大的了 不用交换了
           if (low==heigh){
               break;
           }
           //交换 基准与 左侧检索到大于基准的值的位置
           int temp1=array[low];
           array[low]=array[heigh];
           array[heigh]=temp1;
           heigh--;
       }
        System.out.println(left);
        System.out.println(heigh);
        System.out.println(low);
        System.out.println(right);
       //递归调用
        //判断终止条件 如果左右游标相等 说明只有一个值 不需要排序了
        if (!(heigh-1<=0) ){
            quickSort(array,left,heigh-1);
        }
        if (!(heigh+1>=right)){
            quickSort(array,heigh+1,right);
        }
    }
//调用
  public static void main(String[] args) throws ClassNotFoundException {
  /*     String str="StudentController\\class";
        String[] split = str.split("\\\\");

        for (String s : split) {
            System.out.println(s);
        }*/
      int[] ints={30,9,22,55,33,56,34,36,100,1200,3123,23,434,666};
      /*int[] ints1={22,9};
      int[] ints2={55,33,56,34,36};*/
      quickSort(ints,0,ints.length-1);
        System.out.println(Arrays.toString(ints));
    }
//结果
[9, 22, 23, 30, 33, 34, 36, 55, 56, 100, 434, 666, 1200, 3123]
// 上面是自己写的实验版本
//下面是写的一个简洁的版本
  public  static void sort(Integer[] array,int min,int max){
        if (min>max){
            return;
        }
        int middle = middle(array, min,max);
        sort(array,0,middle-1);
        sort(array,middle+1,max);

    }
    public  static int middle(Integer[] array,int min,int max){
        int p=array[min];
        while (max>min){
            while(max>min && array[max]>=p){
                max--;
            }
            array[min]=array[max];
            while (max>min && array[min]<=p){
                min++;
            }
            array[max]=array[min];
        }
        array[min]=p;
       return min;

    }
```



## 输入流与输出流

```java
Scanner sc = new Scanner(System.in);
		int i = sc.nextInt();
		System.out.println(i);
```

## 自比较与类比较   comparable            comparator

```java
public class Fruit implements Comparable<Fruit> {
    private String name;
    private Integer weight;

    public Fruit(){}

    public Fruit(String name, Integer weight){
        this.name = name;
        this.weight = weight;
    }

    @Override
    public int compareTo(Fruit o) {
        if(this.name.equalsIgnoreCase(o.getName())){
            // 相同名称则按照重量降序排列，如果重量也相同则保持添加时的顺序不变
            return this.weight <= o.getWeight() ? 1 : -1;
        }
        return this.name.compareToIgnoreCase(o.getName());
    }

    // setters and getters...
}
    public static void main(String[] args) {
        Fruit apple1 = new Fruit("apple",12);
        Fruit apple2 = new Fruit("aPple",15);
        Fruit apple3 = new Fruit("Apple",9);
        Fruit apple4 = new Fruit("appLe",9);
        Fruit banana1 = new Fruit("baNana",7);
        Fruit banana2 = new Fruit("banAna",7);
        Fruit banana3 = new Fruit("Banana",14);

        List<Fruit> fruitList = new ArrayList<>();
        fruitList.add(banana3);
        fruitList.add(apple4);
        fruitList.add(apple3);
        fruitList.add(banana1);
        fruitList.add(apple2);
        fruitList.add(banana2);
        fruitList.add(apple1);

        // 按照水果名称升序排列，如果名称一致则按照重量降序排列
        Collections.sort(fruitList);

        for(Fruit fruit : fruitList){
            System.out.println(fruit.getName() + "-" + fruit.getWeight());
        }
    }
按照如上代码示例运行结果如下：


aPple-15
apple-12
appLe-9
Apple-9
Banana-14
baNana-7
banAna-7

public class Fruit {
    private String name;
    private Integer weight;

    public Fruit(){}

    public Fruit(String name, Integer weight){
        this.name = name;
        this.weight = weight;
    }

   // setters and getters...
}
public class FruitComparator implements Comparator<Fruit> {

    @Override
    public int compare(Fruit o1, Fruit o2) {
        if(o1.getName().equalsIgnoreCase(o2.getName())){
            // 相同名称则按照重量降序排列，如果重量也相同则保持添加时的顺序不变
            return o1.getWeight() <= o2.getWeight() ? 1 : -1;
        }
        return o1.getName().compareToIgnoreCase(o2.getName());
    }

}
    public static void main(String[] args) {
        Fruit apple1 = new Fruit("apple",12);
        Fruit apple2 = new Fruit("aPple",15);
        Fruit apple3 = new Fruit("Apple",9);
        Fruit apple4 = new Fruit("appLe",9);
        Fruit banana1 = new Fruit("baNana",7);
        Fruit banana2 = new Fruit("banAna",7);
        Fruit banana3 = new Fruit("Banana",14);

        List<Fruit> fruitList = new ArrayList<>();
        fruitList.add(banana3);
        fruitList.add(apple4);
        fruitList.add(apple3);
        fruitList.add(banana1);
        fruitList.add(apple2);
        fruitList.add(banana2);
        fruitList.add(apple1);

        // 按照水果名称升序排列，如果名称一致则按照重量降序排列
        fruitList.sort(new FruitComparator());
        // Collections.sort(fruitList, new FruitComparator());

        for(Fruit fruit : fruitList){
            System.out.println(fruit.getName() + "-" + fruit.getWeight());
        }
    }
按照如上代码示例运行结果如下：

aPple-15
apple-12
appLe-9
Apple-9
Banana-14
baNana-7
banAna-7
三、关于Comparable和Comparator的异同
相同点

在功能上两者能实现完全一样的排序需求；
在两者都可使用的情况下，随意使用一个即可；
不同点

Comparable需要主体自己实现接口并重写compareTo方法；
Comparable只能使用Collections.sort方法进行排序；
Comparator需要单独创建一种排序策略，在排序的时候指定使用；
Comparator既可以使用Collections.sort也可以使用list.sort方法；
四、使用总结
当排序主体本身实现了Comparable接口，且其重写的排序策略符合需求的时候，直接使用Comparable的排序方案即可；
当排序主体虽然实现了Comparable接口，但是其本身重写的排序策略不能满足需求，则需要使用Comparator，新建一种排序策略；
当排序主体没有实现Comparable接口的时候，可以考虑让其实现Comparable接口并重写排序策略，也可以使用Comparator单独新建一种排序策略；
Comparable需要对排序主体进行修改，侵入性较高，而Comparator无需更改任何排序主体的代码，体现了策略模式的思想，在排序场景较多的情况下较为推荐。


```

## 适配器模式 Adapter

一个接口定义了许多方法，然而当我们继承接口重写方法的时候只需要重写其中的几个时，就用放到了适配器模式，

新建一个类继承接口，对我们不需要重写的方法进行空实现，然后继承进行空实现的类

但是在jdk1.8之后接口可以实现默认方法，接口中可以下方法体，所以适配器模式可以被接口替代

## 关键字

```java
1.public/private/protect/default
-protect在父子类时可以跨包调用 其他时候不可以
-default在任何时候不能跨包调用

2.static/final/super/this...
-static代表所有对象共享，与对象无关，只与类有关。
-final修饰类/方法/常量
    final 关键字表示对象是最终形态的，对象是不可改变的意思。final 应用于类、方法和变量时意义是不同的，但本质是一样的：final 表示不可改变。

final 用在变量的前面表示变量的值不可以改变，此时该变量可以被称为常量；final 用在方法的前面表示方法不可以被重写；final 用在类的前面表示类不可以被继承，即该类是最终形态，如常见的 java.lang.String 类。

final 修饰符使用在如下方面：
1. final 修饰类中的属性
表示该属性一旦被初始化便不可改变，这里不可改变的意思对基本类型来说是其值不可变，而对对象属性来说其引用不可再变。其初始化可以在两个地方：一是其定义处，也就是说在 final 属性定义时直接给其赋值；二是在构造函数中。这两个地方只能选其一，要么在定义时给值，要么在构造函数中给值，不能同时既在定义时赋值，又在构造函数中赋予另外的值。
2. final 修饰类中的方法
说明这种方法提供的功能已经满足当前要求，不需要进行扩展，并且也不允许任何从此类继承的类来重写这种方法，但是继承仍然可以继承这个方法，也就是说可以直接使用。在声明类中，一个 final 方法只被实现一次。
3. final 修饰类
表示该类是无法被任何其他类继承的，意味着此类在一个继承树中是一个叶子类，并且此类的设计已被认为很完美而不需要进行修改或扩展。

对于 final 类中的成员，可以定义其为 final，也可以不是 final。而对于方法，由于所属类为 final 的关系，自然也就成了 final 型。也可以明确地给 final 类中的方法加上一个 final，这显然没有意义

```

## 泛型

泛型将运行期间的错误检查提前到了编译期间

* 泛型类
* 泛型接口
* 泛型方法

```java
ArrayList<Integer> li = new ArrayList();
		li.add(1);
//		li.add(true); // 泛型产生的强制编译期类型检查
		// 泛型的作用 ： 【将类型的检查从运行期提前到了编译期】
		// 泛型的范围: 只在编译期有效，到运行期就无效了
		// li.add(true); //true能否添加进去到集合中呢？ 【可以】
		// 反射的目的 ： 解析一个类的内部结构 【反射是框架的基础】
		// 反射的基础 ： 字节码（Class.forName("")  类型.class  对象.getClass()  ）
		//  现在需要使用反射来动态添加元素
		Class<? extends ArrayList> clazz = li.getClass(); // 泛型的上限判断   ? super 类
		Method add = clazz.getMethod("add", Object.class);
		add.invoke(li, true);
		
		System.out.println(li);
		
		/**
		 * 反射 
		 * 	字节码获取  Class.forName("");  类名.class  对象.getClass()
		 *  对象的创建 clazz.newInstance();
		 *  调用方法  clazz.getMethod(方法名，形参类型)    method.invoke(对象，实参)
		 *  
		 *  如何动态修改属性【给属性赋值】
		 *  如何动态的获取类上的注解
		 */
		/**
		 * 注释 ： 功能性的描述，程序员查错，为了生成api帮助文档
		 * 注解（主流开发形式） ：
		 * 	 功能性简化代码
		 * 自定义注解   @interface
		 */
 		/**
 * 越底层的通用接口就是这样写的 ： 泛型
 * @param <T>
 */
public interface BaseDao<T> {

	int add(T obj);
	
	int delete(int id);
	
	/**
	 * 根据id查询单个对象
	 * @param id  主键
	 * @return 对象
	 */
	T findById(int id);
	
	Map<Integer, T> findById2(int id);    
	
	List<T> findByIds(int...id);  
	
	List<T> findAll();
}

```

## Java单例模式

```java
//饿汉式 线程安全
public class Person {
	private Person person=new Person();
	//构造方法私有化
	private Person(){
	}
	public Person getInstance(){
		return person;
	}
}
//懒汉式 非线程安全
public class Person {
	private Person person=null;
	//构造方法私有化
	private Person(){
	}
	public Person getInstance(){
		if (person==null){
			person=new Person();
		}
		return person;
	}
}
//双检索懒汉式
ublic class Person {
    // volatile 防止指令重排
    // synchronized 加锁 同步
	private volatile Person person=null;
	//构造方法私有化
	private Person(){
	}
	public Person getInstance(){
		if (person==null){
			synchronized (Person.class){
				if (person==null){
					person=new Person();
					return person;
				}
			}
			
		}
		return person;
	}
}
//懒加载饿汉式 运用了JVM的类加载
public class Singleton3 {
    public static Singleton3 singleton4;
    private Singleton3(){
    }
    public static class Setup{
     private static Singleton3 singleton3=new Singleton3();
    }
    public static Singleton3 getInstance(){

        return Setup.singleton3;
    }
}
//静态内部类实现简单 性能优越 但只要一次getInstance()因异常为null，则每一次都是null
```



## 面向对象

* 封装

  使属性私有化，防止被随意修改，设置setter和getter方法 可以对数据进行检查

* 继承  

  可以继承父类非私有的的属性和方法，减少代码的冗余，提高复用性

  ```java
  //代码的执行顺序
  父类的静态属性，静态的代码块>父类的静态方法>子类的静态属性，静态代码块>子类的静态方法>父类的普通属性，代码块>父类的普通方法>子类的普通属性,代码块>子类的普通方法>父类的构造方法>子类的构造方法
  ```

  

* 多态

  通过指向父类类型而调用父类的不同实现类，向上转型可以自动转换

  向下转型不可以自动转换

  

### 方法重载

​	具有相同的方法名称，根本为其形参列表不同

  * 形参个数
  * 形参顺序
  * 形参类型

### 方法覆盖

具有相同的方法名称，返回类型，形参列表，子类的访问权限必须大于或等于父类

具有不同的方法体

## 元注解

```java
/**
 * 路由映射自定义注解
 * 修饰注解的注解叫 ： 元注解
 *	 @Target({ElementType.TYPE })  注解的使用范围
 * 	 @Retention   注解的可见范围
 * 		RetentionPolicy.SOURCE  只有源码可见
 * 	    RetentionPolicy.CLASS   源码和字节码可见
 * 		RetentionPolicy.RUNTIME 编译和运行期都可见
 */
@Documented  //添加API文档
@Target({ElementType.TYPE, ElementType.METHOD}) //作用在方法，属性，类
@Retention(RetentionPolicy.RUNTIME)//
public @interface RequestMapping {
	
	public String value();
	
	public String path()  default "";

}
```

## String  StringBuffer StringBuilder

```java
/**
	自动扩容 倍数递增，减少了创建次数，提高了效率
 *  字符串String【字符串常量，值不能被修改】
 *  对字符串的操作实质上就是在新建字符串
 *       空间内存占用效率极大提高，时间优化效率也提高
 *  StringBuffer  始终操作的都是同一个字符串，不会新建字符串 【线程安全的： 专用于多线程环境下的字符串拼接】
 *  StringBuilder 始终操作的都是同一个字符串，不会新建字符串 【非线程安全的：适用于单线环境】
 */
public class Test1 {
	public static void main(String[] args) {
		// 面试 ：String,StringBuilder,StringBuffer之间的异同
		long start = System.currentTimeMillis();
//		String s = "字符串";
		StringBuffer sb = new StringBuffer("字符串");  //代码共耗时:708ms
		StringBuilder sb2 = new StringBuilder("字符串"); //代码共耗时:479ms
		for (int i = 0; i < 10000000; i++) {
//			s += "dejuighjkijkhdfdh";	
			sb.append("dejuighjkijkhdfdh");
		}
		long end = System.currentTimeMillis();
		System.out.println("代码共耗时:"+(end-start)+"ms"); 
	}
}
```

## 自定义异常

```java
//创建一个类，继承异常
public class AgeException extends RuntimeException{
	private static final long serialVersionUID = 1L;

	public AgeException() {
		super();
	}

	public AgeException(String message, Throwable cause, boolean enableSuppression, boolean writableStackTrace) {
		super(message, cause, enableSuppression, writableStackTrace);
	}

	public AgeException(String message, Throwable cause) {
		super(message, cause);
	}

	public AgeException(String message) {
		super(message);
	}

	public AgeException(Throwable cause) {
		super(cause);
	}

}
```

## IO流

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固3\图解\IO流.png)

### 字节流

InputStream/OutputStream
-字节流可用于读写一切文件
-文件拷贝:定义输入输出流->遍历读取与写入->关闭流

Reader/Writer
-字符流只能用于读写文本文件

缓冲流/转换流
-*缓冲流最关键 切合敏感需求[分行读取] 只有缓冲流拥有readLine()方法

X.装饰者模式（类似于代理模式）
1.继承->单继承->包装(装饰者)
-继承位宝贵，所以需要一种替补机制。

```java
File file = new File("E:\\JavaSE\\src\\com\\woniu\\test\\test.txt");
		File file1 = new File("test1.txt");
		InputStream ins = new FileInputStream(file);
		FileOutputStream out = new FileOutputStream(file1);//后面加true参数变为追加写入
		byte[] b = new byte[1024];
		int len=0;//读取到的字节数 如果没读取为-1
		while ( (len= ins.read(b))!=-1){
			out.write(b,0,len); //从读到的开始写，写到读的结尾，防止覆盖
		}
		ins.close();
		out.close();

	}
//字节缓冲流可以实现readline 返回string类型
try {
			// 定义输入流/集合容器
			Reader source = new FileReader("C:/Temp/A1/1.txt");
			BufferedReader bufReader = new BufferedReader(source);
			List<String> list = new ArrayList<String>();
			// 遍历读取
			String tmp = "";
			while ((tmp = bufReader.readLine()) != null) {
				list.add(tmp);
			}
			// 关闭流
			source.close();
			// 输出结果
			for (String str : list) {
				System.out.println(str);
			}
			System.out.println("list-size=" + list.size());
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
```

## JDBC

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固4\图解\JDBC.png)

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固4\图解\释放资源.png)

```java
public class JdbcTest {
	public static void main(String[] args) {
		//1. 【验证驱动是否成功】
		try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			System.out.println("驱动加载失败");
		}
		//2. 连接数据库(DriverManager MySQL驱动管理器)
		String url = "jdbc:mysql://localhost:3306/woniu?useSSL=false";
		String user = "root";
		String password = "root";
		Connection conn = null;
		PreparedStatement ps = null;
		try {
			conn = DriverManager.getConnection(url, user, password);
			//3. 获取预编译对象并做占位符替换
			String sql = "delete from t_user where id=?";
			ps = conn.prepareStatement(sql);
			ps.setInt(1, 4);
			//4. 执行SQL
			int row = ps.executeUpdate();
			System.out.println(row>0?"删除成功":"删除失败");
		} catch (SQLException e) {
			System.out.println("数据库连接获取失败");
		}finally {
			if (ps != null) {
				try {
					ps.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
			if (conn != null) {
				try {
					conn.close();
				} catch (SQLException e) {
					e.printStackTrace();
				}
			}
		}
		
	}
}
```

## ORM

Object Relational Mapping   对象关系映射

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固4\图解\ORM核心思想.png)

## OCP

open -closed principle  开闭原则

意思是说,一个软件实体应当对扩展开放,对修改关闭.也就是说,我们在设计一个模块的时候,应当使这个模块可以在不被修改的前提下被扩展,换句话说就是,应当可以在不必修改[源代码](https://baike.baidu.com/item/%E6%BA%90%E4%BB%A3%E7%A0%81)的情况下改变这个模块的行为.

满足OCP的设计给系统带来两个无可比拟的优越性.

1.通过扩展已有的软件系统,可以提供新的行为,以满足对软件的新需求,使变化中的软件系统有一定的适应性和灵活性.

2.已有的软件模块,特别是最重要的抽象层模块不能再修改,这就使变化中的软件系统有一定的稳定性和延续性.

例如：

编程模式中的工厂模式的“工厂方法”支持OCP原则

## XML

XML有两种约束

* DTD 约束 可以约束参数的形式等

* SHEMA 约束 比DTD约束更加强大  可以约束标签出现的顺序等

  ![](C:\Users\idea\Desktop\笔记整合\框架基础巩固4\图解\xml约束.png)

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固3\图解\Xml.png)

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固3\图解\Xml解析.png)

![](C:\Users\idea\Desktop\笔记整合\框架基础巩固3\图解\Xpath.png)

## 线程

什么是线程安全问题？

必须在多线程环境下（单线程永远线程安全)

多个线程必须有对同时对同一资源进行操作的机会

怎样规避线程安全问题？

* 拆分为单线程（但是很多时候没法这样改，平台属性问题，业务需求问题，性能问题，等等。。。)
  (比如服务端项目永远需要面对多线程环境)

* 线程封闭 

  ```java
  public class UserController{
      @Autowired
      private UserService userService;
  
      public String login(String account,String password){
           方法级别 线程封闭 栈封闭
      }
  
      //
  }
  //ThreadLocal封闭
  ThreadLocal<Integer> i=new ThreadLocal<>();
          i.set(1);  
  
  ```

  

* -加锁---规避同时 进行排队
  (有些竞争性业务场景不适用线程封闭，他就需要多个线程操作同一个资源)

* 线程安全的集合的局限性



```java
//线程的三种创建方式
//第一种通过继承Thread类并实现run方法
public class Test extends Thread{ //主类 ： 类名与文件名保持一致，并且修饰符只能是public
	@Override
	public void run() {
		System.out.println("逻辑代码");
		super.run();
	}
	
	public static void main(String[] args) {
		//1. 使用类的方式来创建线程对象
		Test t1 = new Test();
		t1.start(); // 如何启动一个线程
  //实现runnable接口
        new Thread(new Runnable() {
			@Override
			public void run() {
				System.out.println(1);
			}
		}).start();
   //实现callable接口
        * Runnable重写run() , Callable<T> 重写call()
            SE se = new SE();//se实现了callable接口
		FutureTask<String> ft = new FutureTask<>(se);//callable的包装类
		new Thread(ft,"我是个线程").start();
		String s = ft.get();//接受线程的返回值
		System.out.println(s);
	}

	@Override
	public String call() throws Exception {
		return "111";
	}
 * run()没有返回值，不能抛出异常
 * call()有返回值，可以抛出异常
     多个线程执行一个runnable接口  数据不独立 共享
     继承Thread类的线程 各个数据之间互相独立
     runnable接口可以实现多继承 
  
```

### 三个线程轮流交替打印



```java

//通过计数控制
  final  int[] count={1};
        Object obj = new Object();
        Thread t1 = new Thread("线程-A"){
            @Override
            public void run() {
                   for (; ; ) {
                       synchronized (obj) {
                           if (count[0]==1) {
                               System.out.println(Thread.currentThread().getName());
                               count[0]++;
                               obj.notifyAll();
                           }
                           try {
                               obj.wait();
                           } catch (InterruptedException e) {
                               e.printStackTrace();
                           }
                       }
               }
            }
        };
        Thread t2 = new Thread("线程-B"){
            @Override
            public void run() {

                for (;;) {
                    synchronized (obj) {
                        if (count[0]==2) {
                            System.out.println(Thread.currentThread().getName());
                            count[0]++;
                            obj.notifyAll();
                        }
                        try {
                            obj.wait();
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        }
                    }
                }
            }
        };
        Thread t3 = new Thread("线程-C"){
            @Override
            public void run() {
                for (;;) {
                    synchronized (obj) {
                        if (count[0]==3) {
                            System.out.println(Thread.currentThread().getName());
                            count[0] = 1;
                            obj.notifyAll();
                        }
                        try {
                            obj.wait();
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        }
                    }
                }
            }
        };
        t1.start();
        t2.start();
        t3.start();
//总结加同步代码块保证了原子性，线程的等待和唤醒不加也可以，就是浪费性能
/* 结果
线程-A
线程-B
线程-C
线程-A
线程-B
线程-C
线程-A
线程-B
线程-C
线程-A
线程-B
线程-C
*/
int[] count={1};
        ReentrantLock lock = new ReentrantLock();
       Condition c1 = lock.newCondition();
        Condition c2 = lock.newCondition();
        Condition c3 = lock.newCondition();
        Thread t1 = new Thread("线程A"){
            @Override
            public void run() {

                for (;;) {
                    lock.lock();
                    if (count[0]==1) {
                        c2.signal();
                        System.out.println(Thread.currentThread().getName());
                        count[0]++;
                    }
                        try {
                            c1.await();
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        }

                    lock.unlock();
                }

            }
        };
        Thread t2 = new Thread("线程B"){
            @Override
            public void run() {
                for (; ; ) {
                    lock.lock();
                    if (count[0]==2) {
                        c3.signal();
                        System.out.println(Thread.currentThread().getName());
                        count[0]++;
                    }
                    try {
                        c2.await();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    lock.unlock();
                }
            }
        };
        Thread t3 = new Thread("线程C"){
            @Override
            public void run() {
                for (; ; ) {
                    lock.lock();
                    if (count[0]==3) {
                        c1.signal();
                        System.out.println(Thread.currentThread().getName());
                        count[0]=1;
                    }
                    try {
                        c3.await();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    lock.unlock();
                }
            }
        };
        t1.start();
        t2.start();
        t3.start();

```

### 守护线程



守护线程是随着非守护线程结束而自动结束的线程 多个非守护线程以最后结束的为准 守护线程一般是死循环  如后台自动跑得程序等

应用场景JVM的垃圾回收机制 当非守护线程运行程序的同时垃圾回收线程也运行 当非守护线程程序运行结束的同时，垃圾回收线程

```java
 Thread t1 = new Thread("主线程"){
            @Override
            public void run() {
                for (int i = 0; i < 11; i++) {
                    System.out.println(Thread.currentThread().getName()+"池塘开始进水");

                }
            }
        };
       Thread t2= new Thread("守护线程"){
            @Override
            public void run() {
                while (true){
                    System.out.println(Thread.currentThread().getName()+"进水的同时漏水");
                }
            }
        };
        Thread t3 = new Thread("辅助线程"){
            @Override
            public void run() {
                for (int i=1;i<101;i++){
                    System.out.println(Thread.currentThread().getName()+"辅助测试");
                }
            }
        };
        t2.setDaemon(true);
        t1.start();
        t2.start();
        t3.start();
/*
辅助线程辅助测试
守护线程进水的同时漏水
守护线程进水的同时漏水
守护线程进水的同时漏水
守护线程进水的同时漏水
守护线程进水的同时漏水
守护线程进水的同时漏水
*/
```

### 线程池



-数据库连接池/线程池/对象池...(池:预置一定数量的资源在池中 随取随用 随时返还)
-几种常见线程池:无界/固定数量/单线程池等

```java
       //ExecutorService pool = Executors.newCachedThreadPool(); //无界线程池  看机器性能
        ExecutorService fixpool = Executors.newFixedThreadPool(5);//固定线程池
        Runnable s=new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName());
            }
        };
        fixpool.execute(s);
        fixpool.execute(s);
        fixpool.execute(s);
        fixpool.execute(s);
        fixpool.execute(s);
        fixpool.execute(s);
//线程池执行完毕后程序并不会退出 因为线程还是存活状态 可以设置延时退出

    }
```

#### forkjoinpool线程池

```java
 Handler handler = new Handler(1, 101);
        ForkJoinPool forkJoinPool = new ForkJoinPool();
        Integer sum = forkJoinPool.submit(handler).get();
        System.out.println(sum);
//创建handler类继承 RecursiveTask<指定返回类型> 递归有返回值  RecursiveAction  递归无返回值
package com.woniu.thread;

import java.util.ArrayList;
import java.util.Collection;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.RecursiveTask;
import java.util.zip.CheckedOutputStream;

public class Handler extends RecursiveTask<Integer> {
    private Integer min;
    private Integer max;
    public Handler(Integer...nums){
       this.min=nums[0];
       this.max=nums[1];

    }
    @Override
    protected Integer compute() {
        int sum=0;
        int count=min;
        if(max-min<10){
            for (int i = min; i < max; i++) {
               sum+=i;
            }
            System.out.println(Thread.currentThread().getName()+"------"+sum);
            return sum;
        }else{
            ArrayList<Handler> list = new ArrayList<>();
            while (count+10 <max){
                int temp=count;
               count+=9;
                Handler handler = new Handler(temp, count);
                list.add(handler);
            }
           Collection<Handler> handlers = invokeAll(list);
            for (Handler handler : handlers) {
                try {
                   sum+= handler.get();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (ExecutionException e) {
                    e.printStackTrace();
                }
            }
            if (count!=max) {
                for (int i = count; i <= max; i++) {
                    sum += i;
                }
            }
            return sum;
        }
    }
}

```



### 锁



java的锁本质是对象，

#### 同步锁synchronized





```java
//同步方法  public synchronized void demo(){}
//同步代码块 synchronized(obj){代码块}
这个obj对象也可以是字符串或者字符串.intern()
    
public class StringTest {
	public static void main(String[] args) {
	String str1 = "todo";
        String str2 = "todo";
        String str3 = "to";
        String str4 = "do";
        String str5 = str3 + str4;
        String str6 = new String(str1);
 
        System.out.println("------普通String测试结果------");
        System.out.print("str1 == str2 ? ");
        System.out.println( str1 == str2);
        System.out.print("str1 == str5 ? ");
        System.out.println(str1 == str5);
        System.out.print("str1 == str6 ? ");
        System.out.print(str1 == str6);
        System.out.println();
 
        System.out.println("---------intern测试结果---------");
        System.out.print("str1.intern() == str2.intern() ? ");
        System.out.println(str1.intern() == str2.intern());
        System.out.print("str1.intern() == str5.intern() ? ");
        System.out.println(str1.intern() == str5.intern());
        System.out.print("str1.intern() == str6.intern() ? ");
        System.out.println(str1.intern() == str6.intern());
        System.out.print("str1 == str6.intern() ? ");
        System.out.println(str1 == str6.intern());
	}
}
      代码运行结果如下所示：

------普通String测试结果------
str1 == str2 ? true
str1 == str5 ? false
str1 == str6 ? false
---------intern测试结果---------
str1.intern() == str2.intern() ? true
str1.intern() == str5.intern() ? true
str1.intern() == str6.intern() ? true
str1 == str6.intern() ? true
//总结这个intern()方法只是常量值 无关对象地址 能确保字符串唯一

```

#### 轻量级锁 ReentrantLock





```java
ReentrantLock lock = new ReentrantLock();
		Condition con1 = lock.newCondition();  //条件1
		Condition con2 = lock.newCondition(); //条件2
		lock.lock(); //加锁
		con1.await();

		con1.signal();
		con2.await();
		con2.signal();
		lock.unlock();//释放锁
```

#### 如何优雅地停止一个线程

```java
    final boolean[] flag={true};

        Thread t1 = new Thread("线程A"){
            @Override
            public void run() {
                while (flag[0]){
                    System.out.println(1);
                }
            }
        };
        t1.start();
        Thread.sleep(5000);
        flag[0]=false;
//5秒后线程自动停止
```



### countDownLatch 计数器锁

多个线程可以共享这个锁，countDown使计数器减一，await使当前线程陷入阻塞，当计数器为0时，所有线程开始执行

```java
private static CountDownLatch cdl=new CountDownLatch(5);


    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(i+""){
                @Override
                public void run() {
                    System.out.println("当前线程名称->"+Thread.currentThread().getName());
                    try {
                        cdl.countDown();
                        cdl.await();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println("计数为0才能看见"+Thread.currentThread().getName());
                }
            };
            thread.start();

        }
```

## CyclicBarrier锁

起与countDownLatch锁相比较

countDownLatch是一次性的锁归零0结束

cyclicBarrier是可以循环执行的 等所有线程都执行完，再开始下一步的同步共享锁

```java
private static CyclicBarrier cb=new CyclicBarrier(5);
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            new Thread(()->{
                System.out.println("到达30米");
                try {
                    cb.await();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (BrokenBarrierException e) {
                    e.printStackTrace();
                }
                System.out.println("到达50米");
                try {
                    cb.await();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (BrokenBarrierException e) {
                    e.printStackTrace();
                }
                System.out.println("到达70米");
                try {
                    cb.await();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (BrokenBarrierException e) {
                    e.printStackTrace();
                }
                System.out.println("到达100米");

            }).start();
        }
    }
//结果
到达30米
到达30米
到达30米
到达30米
到达30米
到达50米
到达50米
到达50米
到达50米
到达50米
到达70米
到达70米
到达70米
到达70米
到达70米
到达100米
到达100米
到达100米
到达100米
到达100米

Process finished with exit code 0

```



## Semaphore 信号量

可以用来限流

同时只允许 一定数量的线程执行需要使用acquire获得锁，当有线程使用release释放了锁，别的线程才可以进来

```java
 public static void main(String[] args) {
        Semaphore sh = new Semaphore(2);
        for (int i = 0; i < 5; i++) {
          new Thread(){
              @Override
              public void run() {
                  try {
                      sh.acquire();
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  System.out.println("进入一辆车");
                  try {
                      TimeUnit.SECONDS.sleep(2);
                  } catch (InterruptedException e) {
                      e.printStackTrace();
                  }
                  System.out.println("出去一辆车");
                  sh.release();
              }
          }.start();

        }
```



### 线程通信

#### wait()/sleep()的区别

```java
synchronized(obj){
    obj.wait()
    Thread.sleep(1000)
}
Thread.sleep(1000);
//wait()是在synchronized代码块中使用，sleep()哪里都可以用
wait()是使当前线程进入当前线程池，等待状态  释放锁
sleep是当前线程休眠一段时间后继续执行    不释放锁
```



在线程同步的基础上，进行线程之间的调度

```java
synchronized(obj){
    代码
    obj.wait();
    obj.notify();
    
}
```

## 反射

即解析一个类的结构

-根据类名clazzStr，获取属性名列表/方法名列表/注解名列表

```java
//反射的三种方式
Class.forName("全限定类名")
 类名.class
 实例对象.getClass();
```

## 形参影响实参的问题-重点讨论对象型

当形参为基本类型时

形参的改变相当于副本形参的栈指向了新的对象，所以副本形参的改变不会使实参发生改变

当形参为引用类型时

形参副本的API改变相当于使他们的引用地址的对象内容发生了改变，实参的引用地址没变，但是地址对象的内容发生了改变，所以实参发生了改变。

形参副本是赋值操作时，改变了引用地址的对象，但是实参数的引用地址没有变，所以形参的改变对实参没有影响

## equals/==/hascode()

* 三者在默认情况下都是比较的是引用地址

* equals和hascode()可以根据条件进行重写  == 不可以

* 一个类，只要重写了equals()，就要同步重写hashcode()以保持契约。

* 以上契约与JDK现有的集合判重有关 只好遵守。如Set的内部判重。判重就是先判断hascode()粗判断  再用equals进行最终判断 

  

## LIST与SET区别

* List 可重复/SET不可重复 有去重判断

* List的存取有顺序/SET 的存取无顺序

* (少数特殊集合例外，不遵守以上两点。如有的变种Set遵循了放入顺序)CopyOnWriteArraySet

  

## bio/nio/aio

-bio-每个线程只能处理一个请求，多个客户端请求过来，只能多开更多线程。
-nio/aio-皆有多路复用机制，即每个线程可以同时处理多个请求。
(其中nio实现多路复用采用轮询器selector+管道channel的方式)
(aio也就是nio2实现多路复用 采用更好的epoll机制 类似事件监听机制)

## Stream流操作集合

Stream流是JDK8的新特性配合lambda表达式使用（函数式方程）

其是针对于集合的操作优化

把集合看成一条数据流，在stream（）的管道上流过，我们在管道上可以设置许多节点，对流进行筛选过滤，最后进行终端操作

优点

```undefined
（1）速度更快
（2）代码更少（增加了新的语法Lambda表达式）
（3）强大的Stream API
（4）便于并行
（5）最大化减少了空指针异常Optional
ps:工作窃取算法  当一个线程完成自己的任务时，其他线程没做完，自动去拿剩下的去做
```

``` java
//stream流分为 stream()流和parallelStream() 
//stream流为串行流 单个线程
//paralletstream流为并行流 多个线程同时执行
//stream流操作步骤
（1）创建Stream，一个数据源（如：集合、数组），获取一个流；
（2）中间操作，一个中间操作链，对数据源的数据进行处理；filte distinct sort 等
（3）终止操作，一个终止操作，执行中间操作链，并产生结果。foreach max min count anymatch allmatch collect等
Integer[] ints={1,5,6,4,45,465,889,855,123,65,4,489,65,98,49,6,4};
        ArrayList<Integer> arr = new ArrayList<Integer>(Arrays.asList(ints));
       //anymatch 是判断集合中任意一个元素是否包含指定条件，allmatch是判断集合中的所有元素是否符合指定条件
        boolean b = arr.stream().allMatch(i -> {
            return i==98;
        });
        System.out.println(b);
        arr.stream().filter(i -> i > 100 || i < 50).collect(Collectors.toSet());
        arr.parallelStream().forEach(o->{
            System.out.println(Thread.currentThread().getName()+o);
        });
```

## 异常处理

### try ...catch   finally

```java
//try ...catch   finally
 try {  //尝试执行可能会出错误的代码
            FileInputStream inss = new FileInputStream(new File("note"));
            int lens;
            while ((lens=inss.read())!=-1){
                System.out.println(lens);
            }
     return null；

        }catch (RuntimeException e){//当捕获到异常的时候 进行的处理
     							//如果包含父子类异常 要把子类异常放在前面  父类放后
            e.printStackTrace();
        }finally {  //无论try中是否抛出异常都会执行
     				//如果try中有return 也是finally执行之后再去return  一般用来处理资源
            System.out.println("结束");
        }
```

### throws/throw

```java
throws为声明可能会出现的异常
throw 为手动抛出异常  
throw new Exception("手动抛出异常");

```

### 自定义异常

```java
public class MyException extends RuntimeException {
    public MyException(String message){
        super(message);
    }
}
public static void main(String[] args){
    throw new MyException("自定义异常")
}
```

## 动态代理

java的动态代理只针对接口，因为创建出来的代理对象自动会继承Proxy这个类，又因为java是单继承的，如果代理的对象是没有是实现接口，就转化不了类型切记     切记！！！！

动态代理其实是创建一个对象继承法了proxy 然后把被代理对象的方法都变为代理对象中的一个方法类型的属性

代理对象中执行相应的方法都会调用对应属性的方法，然后调用invoke来执行

如果要代理没有实现接口的对象用CgLib来代理 他是通过继承来代理的

-只有接口，没有实现时。利用动态代理生成实现类对象。(多见于各种orm框架---mybatis的原理)
-已有实现时，利用动态代理优雅地植入逻辑(一般是监控性逻辑)。

```java
//invocationHandler
public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        // proxy为代理对象是生成的对象，method是调用的方法,args是方法中调用的参数
        System.out.println("开始代理，执行方法");
        System.out.println(method.getName()+"------"+"开始判断方法");
        System.out.println("代理执行完毕");
    //如果执行方法，invocationHandler中的构造方法中要传入代理的实例对象，method.invoke(实例对象,args)
    
        return null;
    }

```

## 设计模式

* 工厂  分支型工厂     反射性工厂   一般都结合多态和xml  核心是为了解耦和

* 单例模式  饿汉 和懒汉  双检索  和 静态内部类 （懒加载 利用了JVM加载，内部类第一次加载时不运行，第一次调用时加载）

* 装饰者模式

   BufferedReader bufReader=new BufferedReader(reader);

* 代理模式

  静态代理

  (装饰与代理在代码层面99%相同，只是意图不同。)
  (装饰是继承的替补方案，重在扩展其他方法)

  动态代理

  (静态代理只能代理有限的一个或多个类，并不万能)
  (动态代理就是一个可以代理任意类的万能代理)
  (JDK式动态代理: 需要接口/性能好)
  (CGLIB式动态代理: 不需要接口/性能稍低)
  (动态代理在有实现类时，可以优雅地植入逻辑。在只有接口没有实现时，可以生成实现对象。)

* 策略模式

  同样由装饰者演变而来
  -被装饰的类接口化 运用多态 可以执行不同策略  加上工厂可以获得不同的实现类

* 适配器模式

  缺省适配器
  -实现接口时，都需要强制实现接口内的所有抽象方法。
  -所以用一个适配器类放在中间。
  -适配器类

* 模板模式

  内部写好了逻辑骨架

  需要内部几个开放的步骤方法进行重写 类似于jdbc中的resultset；

  ```java
  abstract class 模板类{
     public void 骨架逻辑(){
        第一步();
        第二步();---允许子类重写
        第三步();---允许子类重写
     }
  } 
  ```

  

* 观察者模式

* 责任链模式

     

     

   ## 用两个栈模拟一个队列

   ```java
   package main.java;
   
   import com.sun.org.apache.bcel.internal.generic.INSTANCEOF;
   
   import java.util.ArrayList;
   import java.util.Iterator;
   import java.util.Stack;
   
   public class TTTTT {
       private static Stack<Integer> s1 = new Stack();
       private static Stack<Integer> s2 = new Stack();
   
       public static void main(String[] args) {
           //两个栈来模拟队列
           //栈是先进后出 队列是先进先出
           into(1);
           into(2);
           into(3);
           System.out.println(outer());
           into(4);
           System.out.println(outer());
           System.out.println(outer());
           into(5);
           System.out.println(outer());
           System.out.println(outer());
   
   
   
       }
   
       public static void into(Integer item) {
           if (s1.isEmpty()){
               while(s2.size()>0){
                   s1.push(s2.pop());
               }
               s1.push(item);
               return;
           }
          s1.push(item);
       }
   
       public static Integer outer() {
           if (s1.isEmpty() && s2.isEmpty())
               return -1;
          if (!s1.isEmpty()){
              while (s1.size()>0){
                  s2.push(s1.pop());
              }
              return s2.pop();
          }
          return s2.pop();
       }
   
   }
   
   ```

   

   ## 两个队列来模拟一个栈

   ```java
   public class TTTTT {
       private static LinkedList<Integer> q1=new LinkedList();
       private static LinkedList<Integer> q2=new LinkedList();
   
   
   
       public static void main(String[] args) {
           //两个栈来模拟队列
           //栈是先进后出 队列是先进先出
   
           into(1);
           into(2);
           into(3);
           into(4);
           into(5);
           System.out.println(outer());
           System.out.println(outer());
           into(7);
           System.out.println(outer());
           into(6);
           System.out.println(outer());
           System.out.println(outer());
           System.out.println(outer());
           System.out.println(outer());
       }
       public static void  into(Integer item){
           //可以判断q1是否装满  如果装满了就往s2里面放
           q1.add(item);
       }
       public static Integer outer(){
           if (q1.isEmpty() && q2.isEmpty()){
               return -1;
           }
           if (!q1.isEmpty()){
               while (q1.size()>0){
                       q2.addFirst(q1.pop());
               }
           }
           return q2.pop();
       }
   ```

   ## 两个栈模拟队列

   ```java
   private static Stack<Integer> s1 = new Stack();
       private static Stack<Integer> s2 = new Stack();
   
   
       public static void main(String[] args) throws IOException {
           add(1);
           add(2);
           add(3);
           System.out.println(pop());
           add(4);
           System.out.println(pop());
           add(5);
           System.out.println(pop());
   
           System.out.println(pop());
           System.out.println(pop());
          
   
   
       }
   
       public static void add(Integer item) {
           if (s1.isEmpty()) {
               while (s2.size() > 0) {
                   s1.push(s2.pop());
               }
               s1.push(item);
               return;
           }
           s1.push(item);
       }
   
       public static Integer pop() {
           if (s1.isEmpty() && s2.isEmpty()) {
               return -1;
           }
           if (s1.isEmpty() && !s2.isEmpty()) {
               return s2.pop();
           }
   
           while (s1.size() > 0) {
               s2.push(s1.pop());
           }
   
           return s2.pop();
       }
   ```

   ![1584285226907](C:\Users\idea\AppData\Roaming\Typora\typora-user-images\1584285226907.png)

   

## 两个队列模拟战

```java
    private static  LinkedList<Integer> q1=new LinkedList();
    private static LinkedList<Integer> q2=new LinkedList();


    public static void main(String[] args) throws IOException {
        System.out.println(pop());
        add(1);
        add(2);
        add(3);
        System.out.println(pop());
        add(4);
        System.out.println(pop());
        add(5);
        System.out.println(pop());

        System.out.println(pop());
        System.out.println(pop());





    }

    public static void add(Integer item) {
      q1.add(item);
    }

    public static Integer pop() {
        if (q2.isEmpty() && q1.isEmpty()){
            return -1;
        }
        if (!q1.isEmpty()){
            while(q1.size()>0){
                q2.addFirst(q1.pop());
            }
        }
        return q2.pop();
    }

```

![1584286893046](C:\Users\idea\AppData\Roaming\Typora\typora-user-images\1584286893046.png)