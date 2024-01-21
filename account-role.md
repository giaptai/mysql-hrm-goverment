```sql
--role_account
create table if not EXISTS 'role_account'(
	id TINYINT PRIMARY KEY,
  	title varchar(50) UNIQUE,
  	status boolean,
  	create_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  	update_at DATETIME
);
insert into role_account (id, title, status) values (0, 'ADMIN', 1), (1, 'EMPLOYEE', 1);
SELECT * FROM role_account;
--account
CREATE TABLE if not EXISTS 'account'(
	id INTEGER PRIMARY KEY AUTOINCREMENT,
  	username varchar(30),
  	password varchar(15),
  	status boolean,
  	create_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    update_at DATETIME
);
alter table account add COLUMN role tinyint REFERENCES role_account(id)
INSERT INTO account (username, password, status) VALUES ('ThuNTM', '001225145523', 1),('TaiNG', '001478111451', 1);
SELECT * from account;
```
