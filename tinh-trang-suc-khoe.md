```sql
create table if not EXISTS 'tinh_trang_suc_khoe' (
	id INTEGER primary key AUTOINCREMENT,
  	title varchar(50) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);

INSERT into tinh_trang_suc_khoe VALUES ('YẾU'), ('TRUNG BÌNH'), ('KHÁ'), ('TỐT'), ('KHỎE');
SELECT * from tinh_trang_suc_khoe
```
