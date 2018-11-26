### 一 Java程序的初始化顺序：

- 静态成员优先于非静态成员，且变量优先于代码块和方法。

- 静态成员只初始化一次，非静态成员可以初始化多次。

- 父类优先于子类初始化。

- 构造方法最后进行初始化，普通代码块按照顺序进行初始化。

### 二 反射：

- 反射 (Reflection) 是 Java 程序开发语言的特征之一，它允许运行中的 Java 程序获取自身的信息，并且可以操作类或对象的内部属性。通过 Class 类获取 class 信息称之为反射（Reflection）

- 反射的重点在于，是在运行时解决问题而不是编译时。

- 获取 Class 对象的三种方式：

  * 方式一：通过类本身获取
  
    > Class clazz = Person.class;
    
    > System.out.println(clazz.getName());
    
  * 方式二：通过类的对象获取
  
    > Person p = new Person();
    
    > Class clazz = p.getClass();
    
    > System.out.println(clazz.getName());
  
  * 方式三：使用 Class 类的 forName 静态方法
  
    > Class.forName("com.cdnu.tyx.Person");

### 三 泛型：

- 定义
  
  * 泛型通俗来讲就是一个类型的占位符，相当于一个类型的参数，多个参数之间用逗号隔开。
  * 泛型能解决类型固定的问题。 
  
- 泛型方法

  * 使用泛型的方法，表明该方法可以接受任何类型的参数。
  * 泛型方法的定义规则：
  
    - 所有泛型方法声明都有一个类型参数声明部分（由尖括号分隔），该类型参数声明部分在方法返回类型之前。
    - 每一个类型参数声明部分包含一个或多个类型参数，参数间用逗号隔开。一个泛型参数，也被称为一个类型变量，是用于指定一个泛型类型名称的标识符。
    - 类型参数能被用来声明返回值类型，并且能作为泛型方法得到的实际参数类型的占位符。
    - 泛型方法体的声明和其他方法一样。注意类型参数 只能代表引用型类型，不能是原始类型 （像 int,double,char 的等）。
  
  * 实例：
    
    ```
       public static < E > void printArray( E[] inputArray ){
        // 输出数组元素            
         for ( E element : inputArray ){        
            System.out.printf( "%s ", element );
         }
         System.out.println();
       }
       public static void main( String args[] ){
        // 创建不同类型数组： Integer, Double 和 Character
        Integer[] intArray = { 1, 2, 3, 4, 5 };
        Double[] doubleArray = { 1.1, 2.2, 3.3, 4.4 };
        Character[] charArray = { 'H', 'E', 'L', 'L', 'O' };
 
        System.out.println( "整型数组元素为:" );
        printArray( intArray  ); // 传递一个整型数组
 
        System.out.println( "\n双精度型数组元素为:" );
        printArray( doubleArray ); // 传递一个双精度型数组
 
        System.out.println( "\n字符型数组元素为:" );
        printArray( charArray ); // 传递一个字符型数组
      } 
    ```
    
- 泛型类
  
  * 和泛型方法一样，泛型类的类型参数声明部分也包含一个或多个类型参数，参数间用逗号隔开。一个泛型参数，也被称为一个类型变量，是用于指定一个泛型类型名称的标识符。因为他们接受一个或多个参数，这些类被称为参数化的类或参数化的类型。
  
  * 实例：
  
    ```
    public class Box<T> {
      private T t;
      public void add(T t) {
          this.t = t;
      }

      public T get() {
          return t;
      }

      public static void main(String[] args) {
          Box<Integer> integerBox = new Box<Integer>();
          Box<String> stringBox = new Box<String>();

          integerBox.add(new Integer(10));
          stringBox.add(new String("菜鸟教程"));

          System.out.printf("整型值为 :%d\n\n", integerBox.get());
          System.out.printf("字符串为 :%s\n", stringBox.get());
      }
    }
    
    ```
    
- 类型通配符
  
  * 类型通配符一般是使用 ? 代替具体的类型参数。例如 List<?> 在逻辑上是 List<String>，List<Integer> 等所有 List<具体类型实参> 的父类。

  * 类型通配符上限通过形如 List<? extend Number>来定义，如此定义就是通配符泛型值接受 Number 及其下层子类类型。

  * 类型通配符下限通过形如 List<? super Number> 来定义，表示类型只能接受 Number 及其三层父类类型，如 Objec 类型的实例。
  
### 四 权限修饰符

- 四个权限修饰符的关系
  
  ![](http://s15.sinaimg.cn/large/bfe6b00ctx6BrFwd03Yae&690)
  
- protected 修饰的成员对于其子类（不管是否是同一个包）都是可见的， default 修饰的成员对于其他包是私有的。

### 五 
    
  
  
  
