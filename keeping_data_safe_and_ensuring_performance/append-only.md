# 重写/压缩append-only文件

随着时间的推移，AOF占用容量会越来越高。

想解决AOF容量占用越来越高的问题，我们可以使用``BGREWRITEAOF``，这会尽可能删掉冗余的命令重写AOF，使命令更短。 ``BGREWRITEAOF``工作方式非常类似于快照``BGSAVE``: 执行一个fork，然后在子进程执行重写append-only log。因此，所有限制快照性能相关因素如fork时间，内存使用，等等同样限制着append-only文件。更糟糕的是，因为AOFs可以在一次dump中增长许多次(如果不受控制的话)，当时AOF重写时，OS需要删除AOF，这可能导致当删除一个十几GB的AOF时系统挂起好几秒。

使用快照时，我们可以使用``save``配置选项启用自动使用``BGSAVE``写入快照。使用AOFs时，有两个配置选项自动启用``BGREWRITEAOF``的执行: ``auto-aof-rewrite-percentage``和``auto-aof-rewrite-min-size``。使用以下范例的值，``auto-aof-rewrite-percentage 100``和``auto-aof-rewrite-min-size 64mb``，意思是当AOF启用时，redis会在AOF比上次完成重写AOF时的容量大至少100%时开启一个``BGREWRITEAOF``，并且AOF容量至少在64MB时。参照这个配置点，如果我们的AOF重写太频繁，我们可以提高100，代表再增大100%时重写，不过这会导致Redis花费更多rewrite时间。

如果有可能，建议将快照和AOF添加到其他服务器。

无论快照还是append-only files，都可以在系统重启或崩溃时保持数据完整性。如果要提高读取性能或增加数据安全性，我们可能需要复制集。
