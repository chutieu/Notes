##### How to use emoji in Rails.
```
default: &default
  adapter: mysql2
  encoding: utf8mb4
  collation: utf8mb4_bin
  pool: 5
  username: root
  password: root
  host: localhost
  
development:
  <<: *default
  database: development
test:
  <<: *default
  database: test
production:
  <<: *default
  database: production
```
we use ```encoding: utf8mb4``` and ```collation: utf8mb4_bin``` help DB use emoji easy. 

If DB has been create as :

```
default: &default
  adapter: mysql2
  pool: 5
  username: root
  password: root
  host: localhost
  
development:
  <<: *default
  database: development
test:
  <<: *default
  database: test
production:
  <<: *default
  database: production
```
We need add ```encoding: utf8mb4``` and ```collation: utf8mb4_bin``` to database file  and run commands : 
```
ALTER DATABASE production CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci;
```
If table use emoji, we need change table as : 
```
ALTER TABLE table_name CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```