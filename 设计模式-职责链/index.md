# 职责链


# 职责链

## 数据结构模式

1. ***什么是数据结构模式***
   - *常常有一些组件在内部具有特定的数据结构, 如果让客户程序依赖这些特定的数据结构, 将极大的破坏组件的复用*
2. ***典型模式***
   - *Composite*
   - *Iterator*
   - *Chain of Resposibility*

## 职责链前言

1. *这个模式 其实随着现在数据结构的发展 也过时了*
2. *但是还是老话 模式过时 思想不会过时*

## 动机

1. *在软件构建过程中, 一个请求可能被多个对象处理, 但是每个请求在运行时只能有一个接受者，如果显式指定, 将必不可少的带来发送者和接受者的紧耦合*
2. *如何使请求的发送者不需要指定具体的接受者?*
3. *让请求的接受者自己在运行时决定来处理请求, 从而使两者解藕*

## 模式定义

1. *使多个对象都有机会处理请求, 从而避免请求的发送者和接受者之间的耦合关系，将这些对象形成一条链表, 并沿着这条链传递请求, 直到有一个对象处理它为止*

## 要点总结

1. *职责链模式的应用场合在于 "一个请求可能有多个接受者, 但是最后真正的接受者只有一个"，这时候请求发送者与接受者的耦合有可能出现"变化脆弱"的症状, 职责链的目的就是将二者解藕, 从而更好的应对变化*
2. *应用了职责链模式后, 对象的职责分派将更具有灵活性，我们可以在运行时动态添加/修改请求的处理职责*
3. *如果请求传递到职责链的末尾仍得不到处理, 应该有一个合理的缺省机制，这也是每一个接受对象的责任, 而不是发出*

