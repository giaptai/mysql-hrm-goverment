```sql
--bac ngach/chuc danh nghe nghiep cong chuc 
CREATE TABLE IF NOT EXISTS 'bac_ngach_cong_chuc'(
	id tinyint primary key,
  	name varchar(100) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
INSERT INTO bac_ngach_cong_chuc (id, name) values (5, 'Khác'),(4, 'Nhân viên'), (0, 'Chuyên viên cao cấp'), (1, 'Chuyên viên chính'),  (2, 'Chuyên viên'),  (3, 'Cán sự- Trung cấp');
SELECT * FROM bac_ngach_cong_chuc;
--bac ngach/chuc danh nghe nghiep vien chuc
CREATE TABLE IF NOT EXISTS 'bac_ngach_vien_chuc'(
	id tinyint primary key,
  	name varchar(100) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
INSERT INTO bac_ngach_vien_chuc (id, name) values 
(0, 'Ngạch viên chức chuyên ngành tương đương với ngạch chuyên viên cấp'), 
(1, 'Ngạch viên chức chuyên ngành tương đương với ngạch chuyên viên chính'), 
(2, 'Viên chức chuyên ngành tương đương với ngạch chuyên viên'), 
(3, 'Ngạch viên chức chuyên ngành tương đương với ngạch cán sự'),
(4, 'Ngạch nhân viên');
SELECT * FROM bac_ngach_vien_chuc;
--chuc_danh_nghe_nghiep cong chuc
CREATE TABLE IF NOT EXISTS 'chuc_danh_nghe_nghiep_cong_chuc'(
	id VARCHAR(6) primary key,
  	name varchar(100) UNIQUE,
  	bac_ngach_cong_chuc tinyint
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null,
  	FOREIGN key (bac_ngach_cong_chuc) REFERENCES bac_ngach_cong_chuc(id)
);
INSERT INTO chuc_danh_nghe_nghiep_cong_chuc (id, name, bac_ngach_cong_chuc) values ('01.001', 'Chuyên viên cao cấp', 0), 
('04.023', 'Thanh tra viên cao cấp', 0);
SELECT * FROM chuc_danh_nghe_nghiep_cong_chuc;
--chuc_danh_nghe_nghiep vien chuc
CREATE TABLE IF NOT EXISTS 'chuc_danh_nghe_nghiep_vien_chuc'(
	id VARCHAR(10) primary key,
  	name varchar(100) UNIQUE,
  	bac_ngach_vien_chuc tinyint
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null,
  	FOREIGN key (bac_ngach_vien_chuc) REFERENCES bac_ngach_vien_chuc(id)
);
INSERT INTO chuc_danh_nghe_nghiep_vien_chuc (id, name, bac_ngach_vien_chuc) values ('V.07.01.01', 'Giảng viên cao cấp (hạng I)', 0), 
('V.07.01.02', 'Giảng viên chính (hạng II)', 1);
SELECT * FROM chuc_danh_nghe_nghiep_vien_chuc;
```
