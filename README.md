# percona-playback
Docker container for percona playback. The [original repo](https://github.com/Percona-Lab/query-playback) doesn't give complete details about how to install the tool successfully and they no longer maintain the project.

## How to use
- `git clone git@github.com:turbo8p/percona-playback.git`
- `cd percona-playback && docker-compose up -d`
- `docker exec -it percona-playback bash`
- `percona-playback`


## Sample commands

### Use slowlog file as input
```
percona-playback --mysql-host=test-host --mysql-user=root --mysql-password=root --mysql-schema=mydb --query-log-file=mysql.slow
```

### Use general log file as input
```
percona-playback --input-plugin general-log --mysql-host=test-host --mysql-user=root --mysql-password=root --mysql-schema=mydb --general-log-file=mysql-general.log
```
