## Builder模式 ##
1. Builder模式定义与使用场景  
  将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。
2. UML类图  
  ![](https://github.com/yqlee/DesignPatternsNotes/blob/master/设计模式/UML/2、Builder模式.png)  
  Product产品类：产品的抽象类  
  Builder：抽象的Builder类，规范产品的组建，一般由子类实现具体的组建过程  
  ConcreteBuilder：具体的Builder类  
  Director：统一组装过程  
  在开发实现过程中 ，Director角色经常会被省略。而直接使用一个Builder来进行对象的组装，这个Builder通常为链式调用，它的关键点是每个setter方法都返回自身this，这样使得setter方法可以链式调用。
3. Builder模式的源码实现  
  AlertDialog  
  AlertDialog的Builder模式并没有Director角色的出现。AlertDialog.Builder同时扮演着Builder、ConcreteBuilder、Director的角色。