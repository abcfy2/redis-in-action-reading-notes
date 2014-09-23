# Redis命令行

本章讲解的是redis常用的命令，以及一些建议。

完整的命令可以在redis的网站找到: http://redis.io/commands

**REDIS 2.4 和2.6差异**:

Redis 2.4和2.6的区别主要包括(但不局限于)Lua脚本，毫秒级精度的到期时间(``PTTL``, ``PEXPIRE``,和``PEXPIREAT``),一些操作(``BITOP``和``BITCOUNT``),一些命令现在支持多个参数，以前它们只支持一个参数(``RPUSH``,``LPUSH``,``SADD``,``SREM``,``HDEL``,``ZADD``,``ZREM``)
