# Configuring Redis for replication

在4.1.1节提过，当一个slave连接到master时，master将会启动一个``BGSAVE``操作。在master端配置复制集，我们只需要确保4.1展示的``dir``和``dbfilename``配置选项中列出的路径和文件名能被Redis进程可写入。

尽管有很多选项控制slave，只有一个选项是必须开启的: ``slaveof``。如果我们设置``slaveof host port``在配置文件中，Redis启动时将会使用配置文件中提供的host和port作为连接的master Redis server。如果我们有一个已经运行的系统，我们可以告诉Redis server停掉slaving，或者作为一个新的或不同的master的slave。要连接到一个新的master，我们可以使用``SLAVEOF host port``命令，或者如果我们想停止从master更新数据，我们可以使用``SLAVEOF no one``。
