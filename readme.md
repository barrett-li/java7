jdk1.7新特性
1 对集合类的语言支持； 
2 自动资源管理； 
3 改进的通用实例创建类型推断； 
4 数字字面量下划线支持； 
5 switch中使用string； 
6 二进制字面量； 
7 简化可变参数方法调用。 

20170526：下面这点也很重要

NIO2的一些新特性
并发工具增强 
Networking增强

 //创建List接口对象
    List<String> list=new ArrayList<String>();
    list.add("item"); //用add()方法获取对象
    String Item=list.get(0); //用get()方法获取对象

 

    //创建Set接口对象
    Set<String> set=new HashSet<String>();
    set.add("item"); //用add()方法添加对象

 

    //创建Map接口对象
    Map<String,Integer> map=new HashMap<String,Integer>();
    map.put("key",1); //用put()方法添加对象
    int value=map.get("key");

 

在JDK1.7中，摒弃了Java集合接口的实现类，如：ArrayList、HashSet和HashMap。而是直接采用[]、{}的形式存入对象，采用[]的形式按照索引、键值来获取集合中的对象，如下：

 


      List<String> list=["item"]; //向List集合中添加元素
      String item=list[0]; //从List集合中获取元素

 

      Set<String> set={"item"}; //向Set集合对象中添加元素

 

      Map<String,Integer> map={"key":1}; //向Map集合中添加对象
      int value=map["key"]; //从Map集合中获取对象
	  

public static void main(String[] args) {
      // Pre-JDK 7
      List<String> lst1 = new ArrayList<String>();
      // JDK 7 supports limited type inference for generic instance creation
      List<String> lst2 = new ArrayList<>();
 
      lst1.add("Mon");
      lst1.add("Tue");
      lst2.add("Wed");
      lst2.add("Thu");
 
      for (String item: lst1) {
         System.out.println(item);
      }
 
      for (String item: lst2) {
         System.out.println(item);
      }
   }

//自动资源管理
public static void main(String[] args) {
      BufferedReader in = null;
      BufferedWriter out = null;
      try {
         in  = new BufferedReader(new FileReader("in.txt"));
         out = new BufferedWriter(new FileWriter("out.txt"));
         int charRead;
         while ((charRead = in.read()) != -1) {
            System.out.printf("%c ", (char)charRead);
            out.write(charRead);
         }
      } catch (IOException ex) {
         ex.printStackTrace();
      } finally {            // always close the streams
         try {
            if (in != null) in.close();
            if (out != null) out.close();
         } catch (IOException ex) {
            ex.printStackTrace();
         }
      }
 
      try {
         in.read();   // Trigger IOException: Stream closed
      } catch (IOException ex) {
         ex.printStackTrace();
      }
   }

public static void main(String[] args) {
      try (BufferedReader in  = new BufferedReader(new FileReader("in.txt"));
           BufferedWriter out = new BufferedWriter(new FileWriter("out.txt"))) {
         int charRead;
         while ((charRead = in.read()) != -1) {
            System.out.printf("%c ", (char)charRead);
            out.write(charRead);
         }
      } catch (IOException ex) {
         ex.printStackTrace();
      }
   }   
   
   

长数字可以加下划线，支持2进制写法   
int one_million = 1_000_000;

int binary = 0b1001_1001;



String s = "test";
switch (s) {
 case "test" :
   System.out.println("test");
case "test1" :
   System.out.println("test1");
break ;
default :
  System.out.println("break");
break ;
}



