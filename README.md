redis-monitor
---------

base [RedisLive](https://github.com/nkrode/RedisLive)

features:
*  cluster support: support multiple redis-instance in one page
*  light load: redis info base
*  metrics: memory, comands, Key HitRate, keyspace, master-slave change, expire keys
*  notification: crash, master-slave stats changed notify

### configuration
vim src/redis_live.conf

config：

- RedisStatsServer: metrics also save in redis, config RedisStatsServer for metrics storage backend

- others: other setttigs you can config on dashboard settings tab

```
{"master_slave_sms": "1,1",
 "RedisStatsServer": {"port": 6379, "server": "127.0.0.1"}
, "sms_alert": "192.168.110.207:9999",
 "DataStoreType": "redis",
  "RedisServers": [
  {"instance": "Master1", "group": "Test1", "port": 6379, "server": "127.0.0.1"}
, {"instance": "Slave1", "group": "Test1", "port": 6380, "server": "127.0.0.1"}
]}

```

### install deps
	pip install -r requirements.txt

### run
    cd src/
    # 1. start web process
    python redis_live.py
    # 2. start metrics collector process
    python redis_monitor.py 

    # 3. open dashboard: http://127.0.0.1:8888/index.html

### install centos services
    cd install/centos
    ./redis-monitor.sh

### overview
![Redis Live](https://raw.github.com/LittlePeng/redis-monitor/master/design/redis-live.png)
![Redis Live](https://raw.github.com/LittlePeng/redis-monitor/master/design/overview.png)

