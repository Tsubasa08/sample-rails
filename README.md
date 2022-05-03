# README

## command
### rails new
```
docker-compose run --rm --no-deps app rails new . -G --force --database=mysql
```

### db create
```
docker-compose run app rails db:create
```

### migration
```
docker-compose run app rails db:migrate
```
