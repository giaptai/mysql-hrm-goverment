```sql
--bac_luong
CREATE TABLE IF NOT EXISTS 'bac_luong'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(5) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
INSERT INTO bac_luong (name) VALUES ('Bậc 1'),('Bậc 2'), ('Bậc 3'), ('Bậc 4'), ('Bậc 5'),
('Bậc 6'), ('Bậc 7'), ('Bậc 8'), ('Bậc 9'), ('Bậc 10'), ('Bậc 11'), ('Bậc 12');
SELECT * from bac_luong;
--loai vien chuc
CREATE TABLE IF NOT EXISTS 'loai_vien_chuc'(
	id VARCHAR(10) primary key,
  	name varchar(2) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
INSERT INTO loai_vien_chuc (id, name) values (0, 'A3'), (1, 'A2'), (2, 'A1'), (3, 'A0'), (4, 'B');
SELECT * FROM loai_vien_chuc;
--loai cong chuc
CREATE TABLE IF NOT EXISTS 'loai_cong_chuc'(
	id VARCHAR(10) primary key,
  	name varchar(2) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
INSERT INTO loai_cong_chuc (id, name) values (0, 'A3'), (1, 'A2'), (2, 'A1'), (3, 'A0'), (4, 'B'),  (5, 'C');
SELECT * FROM loai_cong_chuc;
--nhom_loai_vien_chuc
CREATE TABLE IF NOT EXISTS 'nhom_loai_vien_chuc'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(2) UNIQUE,
    loai_vien_chuc VARCHAR(10),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null,
  	FOREIGN KEY (loai_vien_chuc) REFERENCES loai_vien_chuc(id)
);
--ALTER TABLE nhom_loai_vien_chuc 
--DROP COLUMN bac_luong FLOAT, 
--add COLUMN bac_luong integer REFERENCES bac_luong(id);

INSERT into nhom_loai_vien_chuc (name, loai_vien_chuc) values ('A3.1', 0), ('A3.2', 0), ('A2.1', 1), ('A2.2', 1),
('A1', 2), ('A0', 3), ('B', 4);
SELECT * FROM nhom_loai_vien_chuc;
--nhom_loai_cong_chuc
CREATE TABLE IF NOT EXISTS 'nhom_loai_cong_chuc'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(2) UNIQUE,
    loai_cong_chuc VARCHAR(10),
  	he_so FLOAT,
  	bac_luong INTEGER,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null,
  	FOREIGN KEY (loai_cong_chuc) REFERENCES loai_cong_chuc(id)
);
INSERT into nhom_loai_cong_chuc (name, loai_cong_chuc) values 
('A3.1', 0), ('A3.2', 0),
('A2.1', 1), ('A2.2', 1),
('A1', 2), ('A0', 3), ('B', 4), ('C1', 5);
SELECT * FROM nhom_loai_cong_chuc;
-- he_so_luong_vien_chuc
CREATE TABLE IF NOT EXISTS 'he_so_luong_vien_chuc'(
	nhom_loai_vien_chuc INTEGER,
  	bac_luong INTEGER,
  	he_so FLOAT DEFAULT 1.0,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null,
  	FOREIGN KEY (nhom_loai_vien_chuc) REFERENCES nhom_loai_vien_chuc(id),
  	FOREIGN KEY (bac_luong) REFERENCES bac_luong(id)
);
INSERT into he_so_luong_vien_chuc (nhom_loai_vien_chuc, bac_luong, he_so) values 
(1, 1, 6.2), (1, 2, 6.56), (1, 3, 6.92), (1, 4, 7.28), (1, 5, 7.64), (1, 6, 8.00),
(2, 1, 5.75),(2, 2, 6.11), (2, 3, 6.47), (2, 4, 6.83), (2, 5, 7.19), (2, 6, 7.55),
(3, 1, 4.4), (3, 2, 4.74), (3, 3, 5.08), (3, 4, 5.42), (3, 5, 5.76), (3, 6, 6.10), (3, 7, 6.44), (3, 8, 6.78),
(4, 1, 4.0), (4, 2, 4.34), (4, 3, 4.68), (4, 4, 5.02), (4, 5, 5.36), (4, 6, 5.7), (4, 7, 6.04), (4, 8, 6.38),
(5, 1, 2.34),(5, 2, 2.67), (5, 3, 3.00), (5, 4, 3.33), (5, 5, 3.66), (5, 6, 3.99), (5, 7, 4.32), (5, 8, 4.65), (5, 9, 4.98),
(6, 1, 2.10),(6, 2, 2.41), (6, 3, 2.72), (6, 4, 3.03), (6, 5, 3.34), (6, 6, 3.65), (6, 7, 3.96), (6, 8, 4.27), (6, 9, 4.58), (6, 10, 4.89),
(7, 1, 1.86),(7, 2, 2.06), (7, 3, 2.26), (7, 4, 2.46), (7, 5, 2.66), (7, 6, 2.86), (7, 7, 3.06), (7, 8, 3.26), (7, 9, 3.46), (7, 10, 3.66), (7, 11, 3.86), (7, 12, 4.06);
select * from he_so_luong_vien_chuc;
-- he_so_luong_cong_chuc
CREATE TABLE IF NOT EXISTS 'he_so_luong_cong_chuc'(
	nhom_loai_cong_chuc INTEGER,
  	bac_luong INTEGER,
  	he_so FLOAT DEFAULT 1.0,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null,
  	FOREIGN KEY (nhom_loai_cong_chuc) REFERENCES nhom_loai_cong_chuc(id),
  	FOREIGN KEY (bac_luong) REFERENCES bac_luong(id)
);
INSERT into he_so_luong_cong_chuc (nhom_loai_cong_chuc, bac_luong, he_so) values 
(1, 1, 6.2), (1, 2, 6.56), (1, 3, 6.92), (1, 4, 7.28), (1, 5, 7.64), (1, 6, 8.00),
(2, 1, 5.75),(2, 2, 6.11), (2, 3, 6.47), (2, 4, 6.83), (2, 5, 7.19), (2, 6, 7.55),
(3, 1, 4.4), (3, 2, 4.74), (3, 3, 5.08), (3, 4, 5.42), (3, 5, 5.76), (3, 6, 6.10), (3, 7, 6.44), (3, 8, 6.78),
(4, 1, 4.0), (4, 2, 4.34), (4, 3, 4.68), (4, 4, 5.02), (4, 5, 5.36), (4, 6, 5.7), (4, 7, 6.04), (4, 8, 6.38),
(5, 1, 2.34),(5, 2, 2.67), (5, 3, 3.00), (5, 4, 3.33), (5, 5, 3.66), (5, 6, 3.99), (5, 7, 4.32), (5, 8, 4.65), (5, 9, 4.98),
(6, 1, 2.10),(6, 2, 2.41), (6, 3, 2.72), (6, 4, 3.03), (6, 5, 3.34), (6, 6, 3.65), (6, 7, 3.96), (6, 8, 4.27), (6, 9, 4.58), (6, 10, 4.89),
(7, 1, 1.86),(7, 2, 2.06), (7, 3, 2.26), (7, 4, 2.46), (7, 5, 2.66), (7, 6, 2.86), (7, 7, 3.06), (7, 8, 3.26), (7, 9, 3.46), (7, 10, 3.66), (7, 11, 3.86), (7, 12, 4.06),
(8, 1, 1.65), (8, 2, 1.83), (8, 3, 2.01), (8, 4, 2.19), (8, 5, 2.37), (8, 6, 2.55), (8, 7, 2.73), (8, 8, 2.91), (8, 9, 3.09), (8, 10, 3.27), (8, 11, 3.45), (8, 12, 3.63);
select * from he_so_luong_cong_chuc;
--
```
