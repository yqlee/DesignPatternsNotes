## UML六种关系 ##
1. UML：  
   Unified Modeling Language（UML)又称统一建模语言或标准建模语言，是始于1997年一个OMG标准，它是一个支持模型化和软件系统开发的图形化语言，为软件开发的所有阶段提供模型化和可视化支持，包括由需求分析到规格，到构造和配置。  
   在UML类图中，常见的有以下几种关系：泛化（Generalization）、实现（Realization）、依赖（Dependency）、关联（Association）、聚合（Aggregation）、组合（Composition）
2. 泛化（Generalization）  
   泛化：泛化是一种一般与特殊、一般与具体之间关系的描述，具体描述建立在一般描述的基础之上，并对其进行了扩展。在程序中是通过继承类实现的。比如狗是对动物的具体描述，在面向对象设计的时候一般把狗设计为动物的子类。  
   表示方法：空心三角形箭头的实线，子类指向父类。  
   ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F/UML/uml_1_Generalization.png)  
3. 实现（Realization）  
   实现是一种类与接口的关系，表示类是接口所有特征和行为的实现，在程序中一般通过类实现接口来描述。  
   表示方法：空心三角形箭头的虚线，实现类指向接口。  
  ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F/UML/uml_2_Realization.png)  
4. 依赖（Dependency）  
   是一种使用的关系，即一个类的实现需要另一个类的协助，所以要尽量不使用双向的互相依赖，在程序中一般表现为类A中的方法需要类B的实例作为其参数或者变量，而类A本身并不需要引用类B的实例作为其成员变量。  
   表示方法：虚线箭头，类A指向类B。  
   ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/设计模式/UML/uml_3_Dependency.png)  
5. 关联（Association）  
   表示类与类之间的联接,它使一个类知道另一个类的属性和方法，这种关系比依赖更强、不存在依赖关系的偶然性、关系也不是临时性的，一般是长期性的，在程序中被关联类B以类属性的形式出现在关联类A中，也可能是关联类A引用了一个类型为被关联类B的全局变量。  
   表示方法：实线箭头，类A指向类B。  
  ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/设计模式/UML/uml_4_Association.png)  
6. 聚合（Aggregation）  
   概念：聚合关联关系的一种特例，是强的关联关系。聚合是整体和个体之间的关系，即has-a的关系，整体与个体可以具有各自的生命周期，部分可以属于多个整体对象，也可以为多个整体对象共享。程序中聚合和关联关系是一致的，只能从语义级别来区分；  
   表示方法：尾部为空心菱形的实线箭头（也可以没箭头），类A指向类B  
   ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/设计模式/UML/uml_5_Association.png)  
7. 组合（Composition）  
   组合也是关联关系的一种特例。组合是一种整体与部分的关系，即contains-a的关系，比聚合更强。部分与整体的生命周期一致，整体的生命周期结束也就意味着部分的生命周期结束，组合关系不能共享。程序中组合和关联关系是一致的，只能从语义级别来区分。  
   表示方法：尾部为实心菱形的实现箭头（也可以没箭头），类A指向类B  
  ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F/UML/uml_6_Composition.png)  
8. 总结：  
   ①、泛化（Generalization）：类的继承关系，实线+三角形；  
   ②、实现（Realization）：接口实现关系，虚线+三角形；  
   ③、依赖（Dependency）：使用关系，虚线+箭头；  
   ④、关联（Association）：联接关系，类属性形式，实线+箭头；  
   ⑤、聚合（Aggregation）：has--a，实线+虚心菱形；  
   ⑥、组合（Composition）：contains--a,实线+实心菱形。  
   画图工具：startUML、Rose