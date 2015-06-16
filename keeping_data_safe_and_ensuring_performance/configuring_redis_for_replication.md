# Configuring Redis for replication

在4.1.1节提过，当一个slave连接到master时，master将会启动一个``BGSAVE``操作。在master端配置复制集，我们只需要确保4.1展示的``dir``和``dbfilename``配置选项中列出的路径和文件名能被Redis进程可写入。
