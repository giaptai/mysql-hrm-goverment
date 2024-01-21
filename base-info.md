```sql
-- DAN TOC
CREATE TABLE IF NOT EXISTS 'dan_toc'(
	id TINYINT primary key,
  	name varchar(30) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
insert into dan_toc (id, name) VALUES (0, 'Kinh'), ( 1, 'Tày');
select * from dan_toc;
--gioi tinh
CREATE TABLE IF NOT EXISTS 'gioi_tinh'(
	id TINYINT primary key,
  	name varchar(15) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
insert into gioi_tinh (id, name) VALUES (0, 'Nam'), ( 1, 'Nữ');
select * from gioi_tinh;
--ton giao
CREATE TABLE IF NOT EXISTS 'ton_giao'(
	id TINYINT primary key,
  	name varchar(50) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
insert into ton_giao (id, name) VALUES (0, 'Phật giáo'), ( 1, 'Công giáo'), ( 3, 'Tin Lành');
select * from ton_giao;
--thanh phan gia dinh xuat than
CREATE TABLE IF NOT EXISTS 'thanh_phan_gia_dinh'(
	id TINYINT primary key,
  	name varchar(50) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
insert into thanh_phan_gia_dinh (id, name) VALUES (0, 'Cố nông'), ( 1, 'Bần nông'),
( 3, 'Trung nông'), (4, 'Phú nông/ Địa chủ'), (5, 'Công chức/ Viên chức'),  (6, 'Nghèo đói'),
(7, 'Tiểu thương'), (8, 'Tiểu chủ'), (9, 'Tư sản'), (10, 'Tiểu tư sản');
select * from thanh_phan_gia_dinh;
--Cơ quan, tổ chức, đơn vị tuyển dụng
CREATE TABLE IF NOT EXISTS 'coquan_tochuc_donvi_tuyendung'(
	id TINYINT primary key,
  	name varchar(50) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
insert into coquan_tochuc_donvi_tuyendung (id, name) VALUES (0, 'Tòa án nhân dân tối cao'), ( 1, 'Viện kiểm sát nhân dân tối cao'),
( 3, 'Kiểm toán Nhà nước'), (4, 'Văn phòng Quốc hội'), (5, 'Văn phòng Chủ tịch nước');
select * from coquan_tochuc_donvi_tuyendung;
-- loai_quan_ham_quan_doi
CREATE TABLE IF NOT EXISTS 'loai_quan_ham_quan_doi'(
	id TINYINT primary key,
  	name varchar(50) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
insert into loai_quan_ham_quan_doi (id, name) VALUES (0, 'Sĩ quan'), ( 1, 'Quân nhân chuyên nghiệp'),
( 2, 'Hạ sĩ quan'), (3, 'Binh sĩ');
select * from loai_quan_ham_quan_doi;
--cap loai quan ham quan doi
CREATE TABLE IF NOT EXISTS 'cap_loai_quan_ham_quan_doi'(
	id TINYINT primary key,
  	name varchar(50) UNIQUE,
  	loai_quan_ham_quan_doi TINYINT,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null,
  	FOREIGN key (loai_quan_ham_quan_doi) REFERENCES loai_quan_ham_quan_doi(id)
);
insert into cap_loai_quan_ham_quan_doi (id, name, loai_quan_ham_quan_doi) VALUES 
(0, 'Cấp tướng', 0), ( 1, 'Cấp tá', 0),(2, 'Cấp úy', 0), 
(3, 'Cao cấp', 1), (4, 'Trung cấp', 1), (5, 'Sơ cấp', 1), 
(6, 'Cao cấp I', 2), (7, 'Trung cấp I', 2), (8, 'Sơ cấp I', 2), 
(9, 'Trung cấp II', 3), (10, 'Sơ cấp II', 3);
SELECT * FROM cap_loai_quan_ham_quan_doi;
--cap bac trong cap loai quan ham quan doi
CREATE TABLE IF NOT EXISTS 'cap_bac_cap_loai_quan_ham_quan_doi'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(50) UNIQUE,
  	cap_loai_quan_ham_quan_doi TINYINT,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null,
  	FOREIGN key (cap_loai_quan_ham_quan_doi) REFERENCES cap_loai_quan_ham_quan_doi(id)
);
insert into cap_bac_cap_loai_quan_ham_quan_doi (name, cap_loai_quan_ham_quan_doi) VALUES 
('Đại tướng', 0), ('Thượng tướng', 0), ('Trung tướng', 0), ('Thiếu tướng', 0),
('Đại tá', 1), ('Thượng tá', 1), ('Trung tá', 1), ('Thiếu tá', 1);
select * from cap_bac_cap_loai_quan_ham_quan_doi;
--doi tuong chinh sach
CREATE TABLE IF NOT EXISTS 'doi_tuong_chinh_sach'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(100) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO doi_tuong_chinh_sach (name) values ('Dân tộc thiểu số'), ('Con liệt sĩ');
SELECT * FROM doi_tuong_chinh_sach;
--trinh_do_giao_duc_pho_thong
CREATE TABLE IF NOT EXISTS 'trinh_do_giao_duc_pho_thong'(
	id INTEGER  primary key AUTOINCREMENT,
  	name varchar(15) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO trinh_do_giao_duc_pho_thong (name) values ('10/10'), ('12/12');
SELECT * FROM trinh_do_giao_duc_pho_thong;
--Trình độ chuyên môn cao nhất
CREATE TABLE IF NOT EXISTS 'trinh_do_chuyen_mon_cao_nhat'(
	id INTEGER  primary key AUTOINCREMENT,
  	name varchar(15) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO trinh_do_chuyen_mon_cao_nhat (name) values ('Sơ cấp'), ('Trung cấp'),
('Cao đẳng'), ('Đại học'), ('Thạc sĩ'), ('Tiến sĩ');
SELECT * FROM trinh_do_chuyen_mon_cao_nhat;
--hoc ham
CREATE TABLE IF NOT EXISTS 'hoc_ham'(
	id INTEGER  primary key AUTOINCREMENT,
  	name varchar(15) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO hoc_ham (name) values ('Giáo sư'), ('Phó giáo sư');
SELECT * FROM hoc_ham;
--danh_hieu_nha_nuoc_phong_tang
CREATE TABLE IF NOT EXISTS 'danh_hieu_nha_nuoc_phong_tang'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(15) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO danh_hieu_nha_nuoc_phong_tang (name) values ('Tỉnh Anh hùng'), ('Thành phố Anh hùng'), 
('Bà mẹ Việt Nam Anh hùng'), ('Anh hùng Lực lượng vũ trang nhân dân'),
('Anh hùng Lao động'), ('Nhà giáo nhân dân'), ('Nhà giáo ưu tú');
SELECT * FROM danh_hieu_nha_nuoc_phong_tang;
--nhom_chuc_danh_dang
CREATE TABLE IF NOT EXISTS 'nhom_chuc_danh_dang'(
	id tinyint primary key,
  	name varchar(15) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO nhom_chuc_danh_dang (id, name) values
(0, 'Các chức danh lãnh đạo chủ chốt và lãnh đạo cấp cao của Đảng và Nhà nước'), (1, 'Chức danh cán bộ thuộc diện Bộ Chính trị, Ban Bí thư quản lý'), 
(2, 'Khung chức danh, chức vụ thuộc diện cấp ủy, tổ chức đảng, lãnh đạo cơ quan, đơn vị quản lý');
SELECT * FROM nhom_chuc_danh_dang;
--cap_nhom_chuc_danh_dang
CREATE TABLE IF NOT EXISTS 'cap_nhom_chuc_danh_dang'(
	id tinyint primary key,
  	name varchar(100) UNIQUE,
  	nhom_chuc_danh_dang tinyint,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null,
  	FOREIGN KEY (nhom_chuc_danh_dang) REFERENCES nhom_chuc_danh_dang(id)
);
INSERT INTO cap_nhom_chuc_danh_dang (id, name, nhom_chuc_danh_dang) values 
(0, 'Lãnh đạo chủ chốt của Đảng và Nhà nước', 0), 
(1, 'Lãnh đạo cấp cao của Đảng, Nhà nước và Mặt trận Tổ quốc Việt Nam', 0), 
(2, 'Các chức danh thuộc diện Bộ Chính trị quản lý', 1), 
(3, 'Các chức danh diện Ban Bí thư quản lý', 1), 
(4, 'Tổng cục trưởng và tương đương', 2), 
(5, 'Phó Tổng cục trưởng và tương đương', 2), 
(6, 'Vụ trưởng và tương đương', 2), 
(7, 'Phó vụ trưởng và tương đương', 2), 
(8, 'Trưởng phòng và tương đương', 2), 
(9, 'Phó trưởng phòng và tương đương', 2), 
(10, 'Cán bộ xã, phường, thị trấn', 2);
SELECT * FROM cap_nhom_chuc_danh_dang;
--chuc_danh_dang
CREATE TABLE IF NOT EXISTS 'chuc_danh_dang'(
	id tinyint primary key,
  	name varchar(100) UNIQUE,
  	cap_nhom_chuc_danh_dang tinyint,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null,
  	FOREIGN KEY (cap_nhom_chuc_danh_dang) REFERENCES cap_nhom_chuc_danh_dang(id)
);
INSERT INTO chuc_danh_dang (id, name, cap_nhom_chuc_danh_dang) values (0, 'Tổng Bí thư', 0), (1, 'Thường trực Ban Bí thư', 1);
SELECT * FROM chuc_danh_dang;
--nhóm máu
CREATE TABLE IF NOT EXISTS 'nhom_mau'(
	id tinyint primary key,
  	name varchar(100) UNIQUE,
  	create_at datetime DEFAULT CURRENT_TIME,
  	update_at DEFAULT null
);
INSERT INTO nhom_mau (id, name) values (0, 'A'), (1, 'B'),  (2, 'AB'),  (3, 'O');
SELECT * FROM nhom_mau;
```
