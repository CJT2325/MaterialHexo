---
title: Activity四种启动方式
---
#####  Activity启动方式有四种，分别为：
- standard
- singleTop
- singleTask
- singleInstance


可以根据不同的应用场景来设置启动方式，从而避免重复创建的问题
可以在AndroidManifest.xml里对应的Avitity标签中设置启动方式

```
<activity  
    android:name=".MainActivity"  
    android:launchMode="standard" />  
```

#### standard(默认启动方式)
在这个模式下，都能创建一个新的实例在Task中，允许多个Avtivity叠加。即每次打开该Avtivity时候，不管Task中是否存在该Activity的实例，都会重新去创建一个新的实例放到栈顶。
#### singleTop
这个模式下允许多个实例，但是不允许多个Avtivity叠加，即如果打开该Activity时候栈顶不是该Activity的实例的话，就会新建一个实例放到栈顶，如果栈顶是该Activity的实例，就不会重新创建实例，而是调用其onNewIntent()方法。
#### singleTask
这个模式下Activity在Task中只能存在一个实例，当打开该Activity的时候Task中不存在该实例，就会创建一个新的实例放入栈顶，如果在Task中已经存在实例的情况下，就会将该实例其上的所有其他activity实例销毁掉，再调用该Avtivity的onNewIntent()。
如果在别的应用启动该Activity则会新建一个Task，并在该Task中启动该Avtivity，之后在该Activity启动的其他Activity都会在该Task中创建。
#### singleInstance
这个模式下Task只能存在该Activity唯一个实例，在其他Activity中启动该Activity会新建一个Task启动该Activity，同时该Task不允许存在其他Activity的实例。