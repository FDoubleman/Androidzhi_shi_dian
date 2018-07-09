#### Activity的四种启动模式对比

**standard\(默认标准启动模式\):**

> 每次创建都会产生新的实例，谁启动了该模式的Activity，该Activity就属于启动它的Activity的任务栈中

**singleTop\(栈顶复用模式\):**

> 如果新的activity已经位于栈顶，那么这个Activity不会被重写创建，同时它的onNewIntent\(Intent intent\)方法会被调用，通过此方法的参数我们可以去除当前请求的信息，该 Activity的实例不在该栈或者不在栈顶 时，其行为同standard启动模式

**singleTask\(站内复用模式\):**

> 如果栈中存在这个Activity的实例就会复用这个Activity，不管它是否位于栈顶，复用时，会将它上面的Activity全部出栈，并且会回调该实例的onNewIntent方法。

**singleInstance\(全局唯一模式\):**

> 具备singleTask模式的所有特性外，与它的区别就是，这种模式下的Activity会单独占用一个Task栈，具有全局唯一性，即整个系统中就这么一个实例，由于栈内复用的特性，后续的请求均不会创建新的Activity实例，除非这个特殊的任务栈被销毁了，当复用该实例 会回调onNewIntent方法



