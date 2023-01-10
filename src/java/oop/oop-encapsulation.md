---
title: Java 面向对象 - 封装
author: 橘涂拾捌
date: 2023-01-09
category: 
 - java
 - oop
tag: 
 - java
 - oop
copyright: false
---

搞编程的人，只要提到面向对象（OO），肯定就会想到面向对象的三大特征。**”封装、继承、多态“**几乎成了面试中必须要提到的问题，连朗沃的小卖部大妈都知道这三个东东了😊。
可是知道是一回事情，但真要让我们把这三个东西说的清清楚楚、明明白白就又是另一回事情了😖。因为这三个概念实在是太抽象了😡，既涉及到编程语法，又上升到设计思想；既好像在代码中随处可见，又似乎隐藏在设计的思维中；让人好不头疼！所以，本博准备开一个专题，来聊聊这让人又爱又恨的“三大特征”。
今天，我们就先来看看第一个特征**“封装”**。

## 前言

**“封装、继承、多态”**，我们念成了口头禅，这个顺序还真不是可以随便改的。**“封装”**是整个面向对象的基础，没有封装性的话，后面两个特性也就白搭。对，封装就是这么🐂13！
但是，很多人只要一提到封装就想到信息隐藏，一提到信息隐藏脑子里就只有一个private修饰符了，这也实在是太片面化和简单化了。那么，

## 什么是封装

作为普通人，一想到“封装”这个词，脑子里面浮现的是什么？
[![img](http://img.mgd2008.com/1.jpg)](https://hyktech.gitee.io/javatech/img/20170816/1.jpg)
没错！就是这样！一个封装包裹的过程。
在这样的一个过程中，我们能够明确感受到：封装，封装。“封”是形容“装”的，这是两个动作，先装再封。“装”的目的是为了把散的东西统一在一起，是为了方便处理和使用；而“封”的目的才是为了信息隐藏，但信息隐藏也绝对不是说藏的严严实实，也可以是分各种级别的。比如说：上图中的箱子，如果换成一个透明的玻璃箱，可以不？还不是一样的叫“封装”呀。

接下来，我们就结合一下编程思想和语法，来讲讲面向对象编程中的这两个动作“装”和“封”，帮助大家再次理解一下。

## 如何理解“装”

### 面向对象中“类”的定义就是“装”

其实在计算机语言的发展过程，很多内容都是一步一步发展到今天这个程度的。

早期的计算机，由于主要处理的问题域的限制（当时主要是科研用途🔬），导致当时处理的数据主要都是数字呀，字符呀这些，所以在编程语言中都会有现成的整数类型、实数类型、字符类型。使用这些基本的数据类型，我们就足够在计算机中保存和处理科学计算问题所需要的数据了。

后来随着发展，计算机开始进入我们的生活了，那么编程人员要写软件满足大家在生活中的需求。那么他们所遇到的问题域也越来越复杂了，比如：大家要玩游戏🎮，里面有一种数据叫：“武器🔪”。可是用什么数据类型来表示武器呢？武器有名字，有等级，有攻击力等等一大堆内容组成。而以前的数据类型（基本数据类型）只能表示”武器”的某一个方面呀，不能表示“武器”这种东西的整体。更何况，类似于这样的情况在各个问题环境中比比皆是，银行系统需要“用户”类型、酒店系统需要“房间”类型、空管系统需要“航班”类型，太多太多了……咋办呢？干脆让编程语言提供一种可以让程序员“自定义”的复杂类型吧。你们（程序员们）可以根据自己的需要来定义这种复杂类型，把各种需要的数据都装入到这种类型中，然后自己起一个名字来表示就行了呗。C语言就提供了大名鼎鼎的“结构体”语法来干这件事情：

```java
struct weapon{
    char weaponName[20];  //武器名称
    int weaponLevel;      //武器等级
    int weaponATK;        //攻击力
}
```



再后来，编程人员发现很多这种复杂类型其实除了装“数据”以外，还提供了很多功能呢。比如刚才说的“武器”，它还有攻击功能，发大招功能，升级功能等等，所以单一的仅仅只能装入数据的类型设计语法已经不能满足我们了（傲娇～～～）。因此，到了面向对象的编程语言，就提供了“类”这个新东东。即让“武器类”这个类型可以装入武器的所有数据，又能装入“武器类”的所有功能，把所有属于“武器”的内容都装入到里面。

```java
class Weapon{
    String weaponName;
    int weaponLevel;
    int weaponATK;
    
    void attack(){
        //攻击的实现
    }
    
    void specialAttack(){
        //特效攻击的实现
    }
    
    void levelUp(){
        //升级的实现
    }
}
```

这样一个武器的变量，既可以保存武器的全部属性数据，又可以操作到它的行为。你说，“类”的定义是不是就是一种“装”？！😤

### 语法中出现{…}就是“装”

如果我们再把眼光放开一点，我们会发现“装”这个动作，在编程当中其实是很多的，绝不仅仅是类的设计定义上。
比如：循环语句块。这个语法中不就是把一堆代码作为一个整体（“装“在一起），每次循环就执行一次吗？

```java
for(int i = 0; i < 100; i++){
    //循环语句块
」
```



再比如：方法块；不也是把一系列的语句作为一个整体，每次调用方法就把这些语句块执行一次吗？

```java
void method(int param){
    //方法实现的语句块
}
```



甚至不仅仅是语句块，下面这个语法不也是把一堆int数据”装”到一个数组集合中统一处理吗？

```java
new int[]{13,24,56,-12,7};
```



所以，我们说编程语言中**{…}**这个语法的设计目的，就是把它里面的内容当成一个整体，以便于进行统一的操作使用。这不是“装”是什么？！这是在模块化编程中就已经出现的、自然的、普遍的概念，到了面向对象编程阶段仍然还在延用而已。
**只是说，在面向对象编程以前没有“封”的语法，所有“装”好的内容，都可以被随意访问到而已。**

## 如何理解“封”

### 为什么要“封”

总有很多刚开始接触编程的同学，对为什么要进行“封”这个动作很不理解。他们在写代码的时候，总觉得**不方便**。比如JavaBean的规范设计，明明就可以直接用“.”操作符操作到的属性，却偏偏要求写成private（私有）的。然后再添一对get／set（访问器／修改器）方法，简直是“脱了裤子放屁—多此一举”😏。难道真是如此吗？

是的，就是如此😂😂😂！！！**“封”就是为了对外部访问进行有效的控制！**生活中，把已经”装”好的东西“封”起来，不就是为了限制里面的内容不被外面的人随意看到或获取到吗？难道你会因为怕麻烦，就让快递不把你在某宝上买的那些不可见人的东西封箱？因为怕麻烦就把家里的贵重物品到处放，而不是装到柜子抽屉里，甚至锁上？（少年，你要么太年轻；要么你是真.傻X）。

**“封”当然不是为了方便，它是为了数据的安全性、有效性，为了维护设计者的意图，保证程序的正确性。**

### “封”体现在哪里

在本文一开始的时候，我提到很多面试者被问到“封装”就回答“信息隐藏”，针对这种说法我举双手同意🙆！但如果你认为信息隐藏仅仅只是private或者仅仅是访问修饰符，那我坚决举五肢反对🙅！！“封装”是一种思想，在使用上的体现可以是非常灵活，把它仅仅绑定为某一种语法法或是几个关键字，确实太简单化了。

#### 访问修饰符肯定是“封装”的体现

这点毋庸置疑！它们就是为了“封装”而生的，这点从“访问修饰符”这个名字也能看出来。“封装”绝不是“封死”，它也是有范围和级别的呀。所以才有各种访问修饰符来针对不同的情况。

| 访问修饰符 | 封装范围 | 容易理解的场景                             |
| :--------- | :------- | :----------------------------------------- |
| private    | 私有     | 你的私房钱，只能你用。                     |
| 默认       | 同包     | 你的家门钥匙，只要住在你家的人都可以使用。 |
| protected  | 受保护   | 你的遗产，只能分配给你的家里人或子女。     |
| public     | 公共     | 除了卫生纸，你能有多大方？                 |

#### get/set方法也是“封装”的体现

1.比如我们针对某个属性只提供get方法，那么这个属性对外部来说就是只读属性。

```java
public class User{
    private int age = 18;
    
    public int getAge(){
        return this.age;
    }
}
```

2.我们也可以在set方法中添加限制，让外部的调用者不能把垃圾数据放入对象当中。

```java
public class User{
    private int age = 18;
    
    public int getAge(){
        return this.age;
    }
    
    public void setAge(int age){
        if(age >= 18 && age <= 80){
            this.age = age;
        }
    }
}
```

3.让外部使用者无法知道类内部保存数据的方式和格式。

```java
public class User{
    private int year;
    private int month;
    private int day;
    
    public String getBirthday(){
        return year + "-" + month + "-" + day;
    }
    
    public void setBirthday(String birthday){
        String[] values = birthday.split("[-]");
        this.year = Integer.parseInt(values[0]);
        this.month = Integer.parseInt(values[1]);
        this.day = Integer.parseInt(values[2]);
    }
}
```

#### 我们调用的API或使用的框架同样是“封装”

```java
ArrayList<Integer> lst = new ArrayList<>();
lst.add(15);
```

当我们使用ArrayList装数据的时候，我们完全不需要去考虑它的具体实现细节（数据结构是咋样的，增加元素空间怎么相应变大变小的），也看不到它内部的实现。这是为什么？“先人”给我们写好了呀，把所有的细节都封装在了ArrayList当中，你只管用就OK了。

框架也是如此呀。Hibernate框架不就是把大家写起来很烦的ORM映射给封装了吗？在用这个框架前，我们要自己去循环数据查询结果集，自己去匹配哪个表对应哪个Bean类，哪个字段对应哪个属性，大家的时间精力都花在上面了。用了Hibernate以后呢？这些细节，你不用考虑了，只要配置一下对应关系，其它的都由Hibernate自己去做了，它把实现的细节给你封装好了。😊😊😊

## 总结

综上，“封装”是面向对象思想中基本的一个特征。在之前的编程思维中，更多的考虑是“装”，是为了能够让计算机有更好的表现数据的方式，以及更好的代码复用效果。现在到了面向对象，有了“封”的思想和语法，就能更好的保障数据的安全性、有效性、准确性，并能够在此基础上进一步维护设计人员的意图，从而达到设计层面在代码级别对实现层面进行管理控制，降低整个开发风险和成本。
