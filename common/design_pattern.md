# 设计模式
设计模式代表了最佳实践，是软件开发人员在软件开发过程中面临的一般问题的解决方案  

## 一些有的没的
### GOF（四人帮 Gang of Four）
Erich Gamma、Richard Helm、Ralph Johnson、John Vlissides

### 设计模式的使用
1. 开发人员的共同平台：设计模式提供一个标准的术语系统，且具体到特定的情节  
2. 最佳的实践：有助于经验不足的开发人员通过一种简单快捷的方式来学习软件设计  

### 设计模式的类型
根据设计模式的参考书Design Patterns - Elements of Reusable Object-Oriented Software共有23种设计模式。  
这些模式可分为三大类：创建模式(Creational Patterns)、结构型模式(Structrual Patterns)、行为模式(Behavioral Patterns)  

模式&描述 | 包含
-------- | -------
创建型模式<br>这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式，<br>而不是使用新的运算符直接实例化对象。<br>这使得程序在判断针对某个给定实例需要创建哪些对象时更加灵活。 | 工厂模式(Factory Pattern)<br>抽象工厂模式(Abstrract Factory Pattern)<br>单例模式(Singleton Pattern)<br>建造者模式(Builder Pattern)<br>原型模式(Prototype Pattern)
结构型模式<br>这些实际模式关注类和对象的组合。<br>继承的概念被用来组合借口和定义组合对象获得新功能的方式 | 适配器模式(Adapter Pattern)<br>桥接模式(Bridge Pattern)<br>过滤器模式(Filter、Criteria Pattern)<br>组合模式(Composite Pattern)<br>装饰器模式(Decorator Pattern)<br>外观模式(Facade Pattern)<br>享元模式(Flyweight Pattern)<br>代理模式(Proxy Pattern)
行为模式<br>这些设计模式特别关注对象之间的通信 | 责任链模式(Chain of Responsibility Pattern)b<br>命令模式(Command Pattern)<br>解释器模式(Interpreter Pattern)b<br>迭代器模式(Iterator Pattern)<br>中介者模式(Mediator Pattern)<br>备忘录模式(Memento Pattern)b<br>观察者模式(Observer Pattern)<br>状态模式(state Pattern)<br>空对象模式(Null Object Pattern)b<br>策略模式(Strategy Pattern)b<br>模板模式(Template Pattern)b<br>访问者模式(Visitor Pattern)

![relation](http://www.runoob.com/wp-content/uploads/2014/08/the-relationship-between-design-patterns.jpg)

### 设计模式的六大原则
1. 开闭原则(Open Close Principle)  
对扩展开放，对修改关闭。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。为了程序的扩展性和易于维护和升级，需要使用接口和抽象类  
2. 里氏代换原则(Liskov Substitution Principle)  
任何基类可以出现的地方，子类一定可以出现。LSP是继承复用的基石，只有当派生类可以替换掉基类，且软件单位的功能不受影响时，基类才能真正被复用，而派生类也能够在基类的基础上增加新的行为。LSP是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以LSP是对象抽象化的具体步骤的规范  
3. 以来倒换原则(Dependence Inversion Principle)  
这个原则是开闭原则的基础，具体内容：针对借口编程，依赖于抽象而不依赖于具体  
4. 借口隔离原则(Interface Segregation Principle)  
使用多个隔离的接口，比使用单个接口要好。降低累之间的耦合度。由此可见，设计模式就是从大型软件架构出发，便于升级和维护的软件设计思想，强调降低依赖，降低耦合  
5. 迪米特法则，又名最少知道法则(Demeter Principle)  
一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立  
6. 合成复用原则(Composite Reuse Principle)  
尽量使用合成/聚合的方式，而不是使用继承   

## 工厂模式(Factory Pattern)
提供了一种创建对象的最佳方式，我们在创建对象时不会对客户端暴露创建逻辑，并且通过使用一个共同的接口来指向新创建的对象  
意图：定义一个创建对象的接口，让其子类决定实例化哪一个工厂类，工厂模式使其创建过程延迟到子类进行  
实例：Hihernate换数据库只需要换方言和驱动就可以  
优点：  
    1. 一个调用者想创建一个对象，只要知道其名称就可以了  
    2. 扩展性高，如果想增加一个产品，只要扩展一个工厂类就可以  
    3. 屏蔽产品的具体实现，调用者只关心产品的接口  
缺点：
    1. 每次增加一个产品时，都需要增加一个具体类和对象实现工厂  
> 看了例子我觉得，工厂模式就是一个类的实例的分发器

## 抽象工厂模式(Abstract Factory Pattern)
围绕一个超级工厂创建其他工厂，工厂的工厂，提供了一种创建对象的最佳方式  
抽象工厂模式中，接口是负责创建一个相关对象的工厂，不需要显示置顶它们的类。每个生成的工厂都能按照工厂模式提供对象  
意图：提供一个创建一系列相关或相互依赖对象的接口，而无需制定他们具体的类  
何时使用：系统的产品有多余一个的产品族，而消费者只消费其中某一族时  
如何解决：在产品族里面定义多个产品  
优点：当一个产品族中的多个对象被设计成一起工作时，它能保证客户端始终只使用同一个产品族中的形象  
缺点：产品组扩展非常困难，要增加某一个产品，既要在抽象的Creator里加代码，又要在具体的里面加代码  
场景：QQ换肤  

## 单例模式(Singleton Pattern)
这种模式涉及一个单一的类，该类负责创建自己的对象，同时确保只有单个对象被创建。这个类提供一种访问其唯一的对象的方式，可以直接访问，不需要实例化该类的对象  
注意：单例类只有一个实例，必须自己创建，必须提供给所有其他对象  
意图：保证一个类仅有一个实例，并提供一个访问它的全局访问点  
主要解决：当想控制实例数目，节省资源的时候  
如何解决：判断系统是否已经有这个实例，如果有则返回，否则创建  
关键代码：构造函数是私有的  
优点：在内存中只有一个实例，减少开销，避免对资源的多重占用(如写文件操作)  
缺点：没有接口，不能继承，与单一职责冲突，一个类应该只关心内部逻辑，而不关心外面如何来实例化  
场景：WEB中得计数器，不用每次刷新都在数据库里加一次，用单例先缓存起来  
注意：`getinstance()`方法需要使用同步锁，防止多线程同时进入造成instance多次被实例化  

## 建造者模式(Builder Pattern)
使用多个简单的对象一步一步构建成一个复杂的对象  
意图：将一个复杂的构建与其表示相分离，使得同样的构建过程可以构建不同的表示  
主要解决：主要解决在软件系统中，有时候棉铃一个复杂对象的构建工作，其通常由各个部分的子对象用一定的算法构成，由于需求的变化，这个复杂对象的各个部分经常棉铃剧烈的变化，但将他们组合在一起的算法却相对稳定  
何时使用：一些基本不见不会变，而其组合经常变化的时候  
如何解决：将变与不变分离开  
优点：建造者独立，易扩展；便于控制细节风险  
缺点：产品必须有共同点，范围有限制；需要生成的对象内部属性本身相互依赖  
注意：与工厂模式的区别：建造者模式更加关注与零件装配的顺序  

## 原型模式(Prototype Pattern)
用于创建重复的对象，同时又能保证性能  
这种模式实现了一个原型接口，该接口用于创建当前对象的克隆。当直接创建对象的代价比较大时，则采用这种模式。如一个高代价的数据库操作  
意图：用原型实例制定创建对象的种类，并且通过拷贝这些原型创建新的对象  
主要解决：在运行期建立和删除原型  
如何解决：利用已有的一个原型对象，快速生成和原型对象一样的实例  
应用实例：细胞分裂  
优点：性能提高，逃避构造函数的约束  
缺点：......  
注意事项：与通过对一个类进行实例化来构造新的对象不同的是，原型模式是通过拷贝一个现有对象生成新对象
> 预先将资源都加载出来，需要的时候直接在已加载的数据中取就行了  

## 适配器模型(Adapter Pattern)
两个不兼容的接口之间的桥梁  
意图：将一个类的接口转换成客户希望的另一个接口。  
主要解决：在软件系统中，常常要将一些现存的对象放到新的环境中，而新环境要求的接口是现对象不能满足的  
如何解决：继承或依赖  
关键代码：是配给继承或依赖已有的对象，实现想要的目标接口  
优点：可以让两个没有关联的类一起运行，提高了类的服用，增加了类的透明度，灵活性好  
缺点：过多的适配器使得系统零乱，如明明调用的是A接口，其实内部被适配成了B接口的实现  
使用场景：有动机的修改一个正常运行的系统的接口  
注意事项：不是在详细设计时添加的，而是解决正在服役的项目的问题  
