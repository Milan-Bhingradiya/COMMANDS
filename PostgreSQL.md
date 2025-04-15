# DB

C:\Users\DELL>psql -U postgres -h localhost -p 5555 -d test    

# 🚀 Basic PostgreSQL Commands to Explore Local Database

Once you're connected to PostgreSQL (`psql`), you can use the following commands to explore your databases, tables, and schemas.

---

## 📌 General Commands
| Command | Description |
|---------|-------------|
| `\?` | Show all available commands in `psql` |
| `\q` | Quit/Exit `psql` |
| `SELECT version();` | Show PostgreSQL version |
| `SELECT current_database();` | Show the currently connected database |
| `SELECT current_user;` | Show the current user |

---

## 📌 Database Management
| Command | Description |
|---------|-------------|
| `\l` or `\list` | List all databases |
| `\c database_name` | Connect to a specific database |
| `DROP DATABASE database_name;` | Delete a database |

---

## 📌 Table Management
| Command | Description |
|---------|-------------|
| `\dt` | List all tables in the current database |
| `\dt+` | List tables with additional details |
| `SELECT * FROM table_name;` | Show all rows in a table |
| `SELECT COUNT(*) FROM table_name;` | Count total records in a table |
| `DROP TABLE table_name;` | Delete a table |

---

## 📌 Schema & Column Information
| Command | Description |
|---------|-------------|
| `\dn` | List all schemas |
| `\d table_name` | Show table structure (columns, types, constraints) |
| `\d+ table_name` | Show detailed table information |
| `SELECT column_name FROM information_schema.columns WHERE table_name = 'table_name';` | List all columns of a table |

---

## 📌 User Management
| Command | Description |
|---------|-------------|
| `\du` | List all users and their roles |
| `CREATE USER username WITH PASSWORD 'password';` | Create a new user |
| `DROP USER username;` | Delete a user |
| `ALTER USER username WITH SUPERUSER;` | Grant superuser privileges |

---

## 📌 Running Queries
| Command | Description |
|---------|-------------|
| `SELECT * FROM table_name;` | Retrieve all rows from a table |
| `INSERT INTO table_name (column1, column2) VALUES ('value1', 'value2');` | Insert data |
| `UPDATE table_name SET column1 = 'new_value' WHERE id = 1;` | Update a row |
| `DELETE FROM table_name WHERE id = 1;` | Delete a row |

---

## 📌 Backup & Restore
| Command | Description |
|---------|-------------|
| `pg_dump -U postgres -d database_name -f backup.sql` | Backup a database |
| `psql -U postgres -d database_name -f backup.sql` | Restore a database |

---

## 📌 Exit PostgreSQL
To exit the `psql` shell, simply type:
```sh
\q
```

---

Now you can explore your local PostgreSQL database easily! 🚀

