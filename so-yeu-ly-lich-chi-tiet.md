```sql
--loai_so_yeu_ly_lich_chitiet
CREATE TABLE IF NOT EXISTS 'loai_so_yeu_ly_lich_chitiet'(
	id INTEGER primary key AUTOINCREMENT,
  	name varchar(50) UNIQUE,
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
INSERT into loai_so_yeu_ly_lich_chitiet (name) VALUES 
('QUÁ TRÌNH ĐÀO TẠO, BỒI DƯỠNG'),
('TÓM TẮT QUÁ TRÌNH CÔNG TÁC'),
('ĐẶC ĐIỂM LỊCH SỬ BẢN THÂN'),
('KHEN THƯỞNG, KỶ LUẬT'),
('QUAN HỆ GIA ĐÌNH'),
('HOÀN CẢNH KINH TẾ GIA ĐÌNH'),
('NHẬN XÉT, ĐÁNH GIÁ CỦA CƠ QUAN, TỔ CHỨC, ĐƠN VỊ SỬ DỤNG');
SELECT * from loai_so_yeu_ly_lich_chitiet;
--chuyen_mon
CREATE TABLE IF NOT EXISTS 'chuyen_mon'(
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ten_co_so_dao_tao varchar(100),
  	chuyen_nganh_dao_tao varchar(100),
  	hinh_thuc_dao_tao varchar(50),
  	vanbang_trinhdo varchar(50),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--ly_luan_chinh_tri
CREATE TABLE IF NOT EXISTS 'ly_luan_chinh_tri'(
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ten_co_so_dao_tao varchar(100),
  	hinh_thuc_dao_tao varchar(50),
  	van_bang_duoc_cap varchar(50),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--Bồi dưỡng quản lý nhà nước/ chức danh nghề nghiệp/ nghiệp vụ chuyên ngành
CREATE TABLE IF NOT EXISTS 'nghiep_vu_chuyen_nganh' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ten_co_so_dao_tao varchar(100),
  	chung_chi_duoc_cap varchar(50),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--Bồi dưỡng kiến thức an ninh, quốc phòng
CREATE TABLE IF NOT EXISTS 'boi_duong_kien_thuc_an_ninh_quoc_phong' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ten_co_so_dao_tao varchar(100),
  	chung_chi_duoc_cap varchar(50),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
CREATE TABLE IF NOT EXISTS 'tin_hoc' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ten_co_so_dao_tao varchar(100),
  	chung_chi_duoc_cap varchar(50),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--ngoai_ngu
CREATE TABLE IF NOT EXISTS 'ngoai_ngu' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ten_co_so_dao_tao varchar(100),
  	ten_ngoai_ngu varchar(50),
  	chung_chi_duoc_cap varchar(50),
  	diem_so float,
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--tom_tat_qua_trinh_cong_tac
CREATE TABLE IF NOT EXISTS 'tom_tat_qua_trinh_cong_tac' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	don_vi_cong_tac varchar(100),
  	chuc_danh varchar(100),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--ban_than_co_lam_viec_cho_che_do_cu
CREATE TABLE IF NOT EXISTS 'ban_than_co_lam_viec_cho_che_do_cu' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	chuc_danh_don_vi_dia_diem TEXT,
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--lam_viec_o_nuoc_ngoai
CREATE TABLE IF NOT EXISTS 'ban_than_co_lam_viec_cho_che_do_cu' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	to_chuc_dia_chi_cong_viec TEXT,
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--khen_thuong
CREATE TABLE IF NOT EXISTS 'khen_thuong' (
	id INTEGER primary key AUTOINCREMENT,
  	nam datetime,
  	xep_loai_chuyen_mon varchar(20),
  	xep_loai_thi_dua varchar(20),
  	hinh_thuc_khen_thuong varchar(20),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--ky_luat
CREATE TABLE IF NOT EXISTS 'ky_luat' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	hinh_thuc varchar(20),
  	hanh_vi_vi_pham_chinh varchar(20),
  	co_quan_quyet_dinh varchar(20),
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--quan_he_gia_dinh_ruot
CREATE TABLE IF NOT EXISTS 'quan_he_gia_dinh_ruot' (
	id INTEGER primary key AUTOINCREMENT,
  	moi_quan_he varchar(50),
  	ho_va_ten varchar(50),
  	nam_sinh datetime,
  	thong_tin_than_nhan text,
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--quan_he_gia_dinh_ruot_ben_vo_hoac_chong
CREATE TABLE IF NOT EXISTS 'quan_he_gia_dinh_ruot_ben_vo_hoac_chong' (
	id INTEGER primary key AUTOINCREMENT,
  	moi_quan_he varchar(50),
  	ho_va_ten varchar(50),
  	nam_sinh datetime,
  	thong_tin_than_nhan text,
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--luong_ban_than
CREATE TABLE IF NOT EXISTS 'luong_ban_than' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	ma_so varchar(10),
  	bac_luong varchar(50),
  	he_so_luong float,
  	tien_luong_theo_vi_tri double
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);
--phu_cap_khac
CREATE TABLE IF NOT EXISTS 'phu_cap_khac' (
	id INTEGER primary key AUTOINCREMENT,
  	bat_dau datetime,
  	ket_thuc datetime,
  	loai_phu_cap varchar(10),
  	phan_tram_huong_phu_cap float,
  	he_so_phu_cap float,
  	hinh_thuc_huong varchar(50),
  	gia_tri double,
  	loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet(id),
  	create_at datetime DEFAULT CURRENT_DATE,
  	update_at DEFAULT null
);

```
