<a href='./Intro.md'><< Learn the Intro</a>

## Table of Content
- [How to create a user?](#how-to-create-a-user)
- [How to display all the databases in PSQL?](#how-to-display-all-the-databases-in-psql)
- [How to quit from current session from logged in user?](#how-to-quit-from-current-session-from-logged-in-user)
- [How to display all the tables in PSQL?](#how-to-display-all-the-tables-in-psql)
- [How to display detailed version for a particular table?](#how-to-display-detailed-version-for-a-particular-table)


# How to create a user?

To create a new user, we must need to log in with superuser account, once logged in execute this command in the terminal

Syntax: `=> CREATE USER user_name WITH PASSWORD 'password';`

replace user_name and actual_password with real username and password.

# How to display all the databases in PSQL?

Use `\l` (backslash l) command

# How to quit from current session from logged in user?

Use `\q` for quit command

# How to display all the tables in PSQL?

use `\dt` command to display all the table based on the logged in user.

# How to display detailed version for a particular table?

use `\d+ table_name` command, which display everything about the table.