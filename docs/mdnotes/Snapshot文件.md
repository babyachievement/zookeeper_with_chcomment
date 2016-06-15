#1. Snapshot文件
Snapshot文件是内存中的datatree在某一时刻的镜像。Snapshot文件由实现Snapshot接口的类可以对datatree做镜像生成，该接口的实现将数据保存到Snapshot文件中。
Zookeeper会按中照一定的机制定时地生成snapshot文件。Zookeeper中FileSnap类实现了SnapShot接口，负责将Datatree写入到snapshot文件中哦。
Snapshot文件是一个二进制文件，每条数据由两部分组成：header+body。

FileSnap使用FileHeader类作为Snapshot数据的header的抽象。FileHeader有三个属性：

```java
public class FileHeader implements Record {
  private int magic; //常量ZKSN  代表zookeeper snapshot文件
  private int version;// 版本
  private long dbid;
}
```

