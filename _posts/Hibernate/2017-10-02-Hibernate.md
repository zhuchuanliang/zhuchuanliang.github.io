---
layout: post
title: Hibernate中的inverse和cascade属性的介绍
categories: Hibernate
description: Hibernate中的inverse和cascade属性的介绍
keywords: inverse,cascade
---
hibernate配置文件中有这么一个属性inverse，它是用来指定关联的控制方。inverse属性默认是false，若为false，则关联由自己控制，若为true，则关联由对方控制。（一对多关联一般都将控制方交给多端，即将一端的inverse属性设置为true）。  


Inverse和cascade是Hibernate映射中最难掌握的两个属性。两者都在对象的关联操作中发挥作用。  


 **1. 明确inverse和cascade的作用**  
 
inverse 决定是否把对对象中集合的改动反映到数据库中，所以inverse只对集合起作用，也就是只对one-to-many或many-to-many有效（因为只有这两种关联关系包含集合，而one-to-one和many-to-one只含有关系对方的一个引用）。cascade决定是否把对对象的改动反映到数据库中，所以cascade对所有的关联关系都起作用（因为关联关系就是指对象之间的关联关系）。  

 **2. inverse属性**  
 

inverse所描述的是对象之间关联关系的维护方式。 
inverse只存在于集合标记的元素中 。Hibernate提供的集合元素包括<set/> <map/> <list/> <array /> <bag /> 
Inverse属性的作用是：是否将对集合对象的修改反映到数据库中。 
inverse属性的默认值为false，表示对集合对象的修改会被反映到数据库中；inverse=false 的为主动方，由主动方负责维护关联关系。 
inverse=”true” 表示对集合对象的修改不会被反映到数据库中。  


 为了维持两个实体类（表）的关系，而添加的一些属性，该属性可能在两个实体类（表）或者在一个独立的表里面，这个要看这双方直接的对应关系了： 这里的维护指的是当主控放进行增删改查操作时，会同时对关联关系进行对应的更新。  
 

   一对多： 该属性在多的一方。应该在一方的设置 inverse=true ，多的一方设置 inverse=false（多的一方也可以不设置inverse属性，因为默认值是false），这说明关联关系由多的一方来维护。如果要一方维护关 系，就会使在插入或是删除"一"方时去update"多"方的每一个与这个"一"的对象有关系的对象。而如果让"多"方面维护关系时就不会有update 操作，因为关系就是在多方的对象中的，直指插入或是删除多方对象就行了。显然这样做的话，会减少很多操作，提高了效率。  
   
注：  

    单向one-to-many关联关系中，不可以设置inverse="true",因为被控方的映射文件中没有主控方的信息。</br>

   多对多： 属性在独立表中。inverse属性的默认值为false。在多对多关联关系中，关系的两端inverse不能都设为false,即默认的情况是不对的，如果都设为false,在做插入操作时会导致在关系表中插入两次关系。也不能都设为 true，如果都设为true,任何操作都不会触发对关系表的操作。因此在任意一方设置inverse=true，另一方inverse=false。  
   

   一对一： 其实是一对多的一个特例,inverse 的设置也是一样的，主要还是看关联关系的属性在哪一方，这一方的inverse=false。

   多对一： 也就是一对多的反过来，没什么区别。  
   

**3.cascade属性**
cascade属性的作用是描述关联对象进行操作时的级联特性。因此，只有涉及到关系的元素才有cascade属性。 
具 有cascade属性的标记包括<many-to-one /> <one-to-one /> <any /> <set /><bag /> <idbag /> <list /> <array /> 
注意：<ont-to-many />和 <many-to-many />是用在集合标记内部的，所以是不需要cascade属性的。 
级联操作：指当主控方执行某项操作时，是否要对被关联方也执行相同的操作。  

**4.inverse和cascade的区别**  
***作用的范围不*同**：  
Inverse是设置在集合元素中的。  
Cascade对于所有涉及到关联的元素都有效。  
<many-to-one/><ont-to-many/>没有inverse属性，但有cascade属性   
***执行的策略不同***:  
Inverse 会首先判断集合的变化情况，然后针对变化执行相应的处理。  
Cascade 是直接对集合中每个元素执行相应的处理   
***执行的时机不同***：  
Inverse是在执行SQL语句之前判断是否要执行该SQL语句  
Cascade则在主控方发生操作时用来判断是否要进行级联操作  
***执行的目标不同***：  
Inverse对于<ont-to-many>和<many-to-many>处理方式不相同。  
对于<ont-to-many>，inverse所处理的是对被关联表进行修改操作。  
对于<many-to-many>，inverse所处理的则是中间关联表。  

总结：  
one-to-many中，建议inverse=”true”，由“many”方来进行关联关系的维护  
many-to-many中，只设置其中一方inverse=”false”，或双方都不设置  
Cascade，通常情况下都不会使用。特别是删除，一定要慎重。  

操作建议  
 一般对many-to-one和many-to-many不设置级联，这要看业务逻辑的需要;对one-to-one和one-to-many设置级联。  
 many-to-many关联关系中，一端设置inverse=”false”，另一端设置为inverse=”true”。在one-to-many关联关系中，设置inverse=”true”,由多端来维护关系表。

 
 
  

