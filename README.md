# Docker

## Useful configs

```export FORMAT="ID\t{{.ID}}\nNAME\t{{.Names}}\nIMAGE\t{{.Image}}\nPORTS\t{{.Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n"```

usage

```docker ps -a --format="$FORMAT"```


## Running Chef unit tests and linting inside docker

```docker run --rm -w /WORKDIR -v /COOKBOOKDIR:/WORKDIR -ti chef/chefdk:3.1.0```
* ```/WORKDIR``` - is dir inside container under which we are mounting cookbook dir from our local machine
* ```/COOKBOOKDIR``` - path to cookbook directory on our local machine which we want to test
* ```-w``` is used to set docker container "WORKDIR" so after starting container we already ```cd``` into our cookbook directory and are ready to run tests
### Running
```docker run --rm -w /WORKDIR -v /COOKBOOKDIR:/WORKDIR -ti chef/chefdk:3.1.0 foodcritic .``` - check chef specific linting with "foodcritic"  
```docker run --rm -w /WORKDIR -v /COOKBOOKDIR:/WORKDIR -ti chef/chefdk:3.1.0 cookstyle``` - check code style checks with "cookstyle"  
```docker run --rm -w /WORKDIR -v /COOKBOOKDIR:/WORKDIR -ti chef/chefdk:3.1.0 rspec``` - run unit test with "rspec"  
