# Go Simple Bank project 
Following are the steps and command and concepts used

Check resources folder for pdfs and other stuff 

### 1.  DB and migrations
we create a db schema i.e up and down scripts to migrate from one db to other like we will be using postgres and nextime we run this applications we can just use migrate function to import all schema related to our project

Install migrate with
> https://github.com/golang-migrate/migrate/blob/master/cmd/migrate/README.md

Easiest way would be downloading binary and copying it to /usr/bin/ 

To create empty files for init schema's
> migrate create -ext sql -dir db/migration -seq init_schema

Then add the content/queries you written (or created from https://dbdiagram.io/home, where you create tables and it spits out queries for various db's)


### 2. Makefile for ease od managing docker and other related tasks
we can use Makfile for longer commands with configs with predefined functions. this eases the work of somebody who uses a project for first time

> Have a look at the Makefile


### 3. Golang connection to DB
There are different ways of doing this (refer 04 in Resources)

eg:
1. https://gorm.io/index.html
2. https://github.com/jmoiron/sqlx
3. https://docs.sqlc.dev/en/stable/overview/install.html

install sqlc [v1.4.0] cli tool in same way as done for migrate

once you write a query like
```shell
[root@docker Golang-project]# ll db/query/account.sql
-rw-r--r--. 1 root root 121 May 15 00:46 db/query/account.sql
[root@docker Golang-project]# cat db/query/account.sql
-- name: CreateAccount :one
INSERT INTO accounts (
  owner,
  balance,
  currency
) VALUES (
  $1, $2, $3
) RETURNING *;
[root@docker Golang-project]#
```

And run `sqlc migrate` it will generate some golang files under `db/sqlc/` which we can use to interact with DB

