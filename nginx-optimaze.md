# Get worker proccess number(cpu cores)
```
cat /proc/cpuinfo |grep processor
```
or
```
nproc --all
```
# Get free memmory
```
free -m
```


# Formula maximum clients Nginx
```
max_clients = worker_processes * worker_connections
```
## ET worker connections via command top on linux
```
worker_connections = free memmory(Mb) / 60 Mb (60 is avg memmory for per request)
```


# Config FPM
## pm.max_children
```
pm.max_children =  free memmory(Mb) / 60
```
## pm.min_spare_servers
```
pm.min_spare_servers = 20% * pm.max_children
```
or
```
pm.min_spare_servers = (cpu cores) * 2
```
## pm.max_spare_servers
```
pm.max_spare_servers = 60% * pm.max_children
```
or
```
pm.max_spare_servers = (cpu cores) * 4
```

# Config Example
## EC2
- Nginx
```
worker_process: 1
worker_connections: 1024
multi_accept: on
```
- PHP
```
pm = dynamic
pm.max_children  = 75
pm.start_servers = 30
pm.min_spare_servers = 15
pm.max_spare_servers = 45
pm.max_requests = 1000
```

# Config PHP opcache
```
vi /etc/php/7.2/cli/conf.d/10-opcache.ini
```
## Change file like this
```
zend_extension=opcache.so
opcache.enable=1
opcache.enable_cli=1
opcache.memory_consumption=128
opcache.interned_strings_buffer=30
opcache.max_accelerated_files=20000
opcache.max_wasted_percentage=5
opcache.use_cwd=1
opcache.validate_timestamps=1
opcache.revalidate_freq=999999999
opcache.fast_shutdown=1
```

# Note for update config Joomla
## Install Redis Driver
- sudo apt install php7.2-dev
- sudo pecl install redis
- sudo apt install php7.2-redis
redis-cli -h sfs-ps-redis.wwjqsb.ng.0001.euc1.cache.amazonaws.com -p 6379 