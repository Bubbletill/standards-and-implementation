# Point of Sale Dependencies
Bubbletill POS and BO required at least Java 18 or higher. To ensure all the required JFX dependencies are also installed, [Bell Soft's Liberica Full JRE](https://bell-sw.com/pages/downloads) is required.

# Backend Dependencies
Backend requires Python3 with the following dependencies which can be installed via PIP:
- flask
- mysql-connector-python
- redis

# System Dependencies
Both the controller and local POS devices require an instance of MySQL 8. For more details on setting up the database, see `dbsetup.md`.
