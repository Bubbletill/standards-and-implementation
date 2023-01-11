# Database Setup
Bubbletill uses MySQL 8 as its database, operating with a master-slave replication system. MySQL 8 should be installed on the controller as the master, and on each register as a slave. 

Bubbletill operates within the `bubbletill` database created in MySQL. Further details on the tables will be provided soon.

## Database Accounts
The controller's database (primary database) should have an account called `bubbletill` which has access over the `bubbletill` database and have the `REPLICATION SLAVE` and `REPLICATION CLIENT` permissions.

The local POS's database (secondary database) should also have an account called `bubbletill` with access over the `bubbletill` database. 

## Server IDs
The primary database should have an ID of `100`, whilst the secondary databases should have an ID of `100 + reg number`. For example, register 1 would be `101`, register 2 would be `102`, etc.
