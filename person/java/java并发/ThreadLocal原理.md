####ThreadLocal原理
   ThreadLocalMap里面有一个Entry<ThreadLocal, Object>
    key是一个ThreadLocal,弱引用保存
    value是保存的值,初始为null
    每一个Thread里面保存一个ThreadLocalMap的引用
    通过获取当前线程来获取到当前的ThreadLocal,再通过ThreadLocalMap获取到当前的value
    ThreadLocalMap底层是一个数组,每个数组保存一个value
    table默认大小16,超过一半容量时扩容两倍,每个key都重新映射到新table
    处理key冲突的方式是开放定址法,通过加一个固定的值(0x61c88647,这个值好像和黄金分割有关,很玄学),
    直到没有key保存过再保存到当前桶
