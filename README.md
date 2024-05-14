# Go Simple Bank project 
Following are the steps and command and concepts used

Check resources folder for pdfs and other stuff 

### 1.  DB and migrations
we create a db schema i.e up and down scripts to migrate from one db to other like we will be using postgres and nextime we run this applications we can just use migrate function to import all schema related to our project

To create empty files for init schema's
> migrate create -ext sql -dir db/migration -seq init_schema

Then add the content/queries you written (or created from https://dbdiagram.io/home, where you create tables and it spits out queries for various db's)


### 2. Makefile for ease od managing docker and other related tasks
we can use Makfile for longer commands with configs with predefined functions. this eases the work of somebody who uses a project for first time

> Have a look at the Makefile