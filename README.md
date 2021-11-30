# percona-playback
Docker container for percona playback. The [original repo](https://github.com/Percona-Lab/query-playback) doesn't give complete details about how to install the tool successfully and they no longer maintain the project.

## How to use
- `git clone git@github.com:turbo8p/percona-playback.git`
- `cd percona-playback && docker-compose up -d`
- `docker exec -it percona-playback bash`
- `percona-playback --version`


## Cli Doc
```
percona-playback --help
```


## Sample commands

### Use slowlog file as input
```
percona-playback --mysql-host=test-host --mysql-user=root --mysql-password=root --mysql-schema=mydb --query-log-file=mysql-slow.log
```

### Use general log file as input
```
percona-playback --input-plugin general-log --mysql-host=test-host --mysql-user=root --mysql-password=root --mysql-schema=mydb --general-log-file=mysql-general.log
```

## Get logs from mysql
You have two options to use as replay input.

1. Slow log
2. General log

### Slow log
Add below config to your `my.cnf` and restart the service. This will ensure that Mysql logs every queries.
```
[mysqld]
slow_query_log=1
slow_query_log_file=/path/to/mysql-slow.log
long_query_time=0.000
```

### General log
```
[mysqld]
general_log_file=/path/to/mysql-general.log
general_log=1
```
