```sql
-- TABLE
CREATE TABLE
	'account' (
		id INTEGER PRIMARY KEY AUTOINCREMENT,
		username varchar(30) UNIQUE,
		password varchar(15),
		status boolean,
		create_at DATETIME DEFAULT CURRENT_TIMESTAMP,
		update_at DATETIME,
		role tinyint DEFAULT 1 REFERENCES role_account (id)
	);

CREATE TABLE
	'bac_luong' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(5) UNIQUE,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'bac_ngach_cong_chuc' (
		id tinyint primary key,
		name varchar(100) UNIQUE,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'bac_ngach_vien_chuc' (
		id tinyint primary key,
		name varchar(100) UNIQUE,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'ban_than_co_lam_viec_cho_che_do_cu' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		chuc_danh_don_vi_dia_diem TEXT,
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'boi_duong_kien_thuc_an_ninh_quoc_phong' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ten_co_so_dao_tao varchar(100),
		chung_chi_duoc_cap varchar(50),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'cap_bac_cap_loai_quan_ham_quan_doi' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(50) UNIQUE,
		cap_loai_quan_ham_quan_doi TINYINT,
		create_at datetime DEFAULT CURRENT_TIME,
		update_at DEFAULT null,
		FOREIGN key (cap_loai_quan_ham_quan_doi) REFERENCES cap_loai_quan_ham_quan_doi (id)
	);

CREATE TABLE
	'cap_loai_quan_ham_quan_doi' (
		id TINYINT primary key,
		name varchar(50) UNIQUE,
		loai_quan_ham_quan_doi TINYINT,
		create_at datetime DEFAULT CURRENT_TIME,
		update_at DEFAULT null,
		FOREIGN key (loai_quan_ham_quan_doi) REFERENCES loai_quan_ham_quan_doi (id)
	);

CREATE TABLE
	'cap_nhom_chuc_danh_dang' (
		id tinyint primary key,
		name varchar(100) UNIQUE,
		nhom_chuc_danh_dang tinyint,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null,
		FOREIGN KEY (nhom_chuc_danh_dang) REFERENCES nhom_chuc_danh_dang (id)
	);

CREATE TABLE
	'chuc_danh_dang' (
		id tinyint primary key,
		name varchar(100) UNIQUE,
		cap_nhom_chuc_danh_dang tinyint,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null,
		FOREIGN KEY (cap_nhom_chuc_danh_dang) REFERENCES cap_nhom_chuc_danh_dang (id)
	);

CREATE TABLE
	'chuc_danh_nghe_nghiep_cong_chuc' (
		id VARCHAR(6) primary key,
		name varchar(100) UNIQUE,
		bac_ngach_cong_chuc tinyint create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null,
		FOREIGN key (bac_ngach_cong_chuc) REFERENCES bac_ngach_cong_chuc (id)
	);

CREATE TABLE
	'chuc_danh_nghe_nghiep_vien_chuc' (
		id VARCHAR(10) primary key,
		name varchar(100) UNIQUE,
		bac_ngach_vien_chuc tinyint create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null,
		FOREIGN key (bac_ngach_vien_chuc) REFERENCES bac_ngach_vien_chuc (id)
	);

CREATE TABLE
	'chuyen_mon' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ten_co_so_dao_tao varchar(100),
		chuyen_nganh_dao_tao varchar(100),
		hinh_thuc_dao_tao varchar(50),
		vanbang_trinhdo varchar(50),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'coquan_tochuc_donvi_tuyendung' (
		id TINYINT primary key,
		name varchar(50) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'danh_hieu_nha_nuoc_phong_tang' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(50) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'dan_toc' (
		id TINYINT primary key,
		name varchar(30) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'doi_tuong_chinh_sach' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(100) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIME,
		update_at DEFAULT null
	);

CREATE TABLE
	'gioi_tinh' (
		id TINYINT primary key,
		name varchar(3) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'he_so_luong_cong_chuc' (
		nhom_loai_cong_chuc INTEGER,
		bac_luong INTEGER,
		he_so FLOAT DEFAULT 1.0,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null,
		FOREIGN KEY (nhom_loai_cong_chuc) REFERENCES nhom_loai_cong_chuc (id),
		FOREIGN KEY (bac_luong) REFERENCES bac_luong (id)
	);

CREATE TABLE
	'he_so_luong_vien_chuc' (
		nhom_loai_vien_chuc INTEGER,
		bac_luong INTEGER,
		he_so FLOAT DEFAULT 1.0,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null,
		FOREIGN KEY (nhom_loai_vien_chuc) REFERENCES nhom_loai_vien_chuc (id),
		FOREIGN KEY (bac_luong) REFERENCES bac_luong (id)
	);

CREATE TABLE
	'hoc_ham' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(15) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'khen_thuong' (
		id INTEGER primary key AUTOINCREMENT,
		nam datetime,
		xep_loai_chuyen_mon varchar(20),
		xep_loai_thi_dua varchar(20),
		hinh_thuc_khen_thuong varchar(20),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'ky_luat' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		hinh_thuc varchar(20),
		hanh_vi_vi_pham_chinh varchar(20),
		co_quan_quyet_dinh varchar(20),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'loai_cong_chuc' (
		id VARCHAR(10) primary key,
		name varchar(2) UNIQUE,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'loai_quan_ham_quan_doi' (
		id TINYINT primary key,
		name varchar(50) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIME,
		update_at DEFAULT null
	);

CREATE TABLE
	'loai_so_yeu_ly_lich_chitiet' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(50) UNIQUE,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'loai_vien_chuc' (
		id VARCHAR(10) primary key,
		name varchar(2) UNIQUE,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'luong_ban_than' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ma_so varchar(10),
		bac_luong varchar(50),
		he_so_luong float,
		tien_luong_theo_vi_tri double loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'ly_luan_chinh_tri' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ten_co_so_dao_tao varchar(100),
		hinh_thuc_dao_tao varchar(50),
		van_bang_duoc_cap varchar(50),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'nghiep_vu_chuyen_nganh' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ten_co_so_dao_tao varchar(100),
		chung_chi_duoc_cap varchar(50),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'ngoai_ngu' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ten_co_so_dao_tao varchar(100),
		ten_ngoai_ngu varchar(50),
		chung_chi_duoc_cap varchar(50),
		diem_so float,
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'nhom_chuc_danh_dang' (
		id tinyint primary key,
		name varchar(15) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'nhom_loai_cong_chuc' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(2) UNIQUE,
		loai_cong_chuc VARCHAR(10),
		he_so FLOAT,
		bac_luong INTEGER,
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null,
		FOREIGN KEY (loai_cong_chuc) REFERENCES loai_cong_chuc (id)
	);

CREATE TABLE
	'nhom_loai_vien_chuc' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(2) UNIQUE,
		loai_vien_chuc VARCHAR(10),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null,
		FOREIGN KEY (loai_vien_chuc) REFERENCES loai_vien_chuc (id)
	);

CREATE TABLE
	'nhom_mau' (
		id tinyint primary key,
		name varchar(10) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'phu_cap_khac' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		loai_phu_cap varchar(10),
		phan_tram_huong_phu_cap float,
		he_so_phu_cap float,
		hinh_thuc_huong varchar(50),
		gia_tri double,
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'quan_he_gia_dinh_ruot' (
		id INTEGER primary key AUTOINCREMENT,
		moi_quan_he varchar(50),
		ho_va_ten varchar(50),
		nam_sinh datetime,
		thong_tin_than_nhan text,
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'quan_he_gia_dinh_ruot_ben_vo_hoac_chong' (
		id INTEGER primary key AUTOINCREMENT,
		moi_quan_he varchar(50),
		ho_va_ten varchar(50),
		nam_sinh datetime,
		thong_tin_than_nhan text,
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'role_account' (
		id TINYINT PRIMARY KEY,
		title varchar(20) UNIQUE,
		status boolean,
		create_at DATETIME DEFAULT CURRENT_TIMESTAMP,
		update_at DATETIME
	);

CREATE TABLE
	so_yeu_ly_lich (
		anh_mau BLOB,
		ho_va_ten varchar(50),
		gioi_tinh varchar(3), --TINYINT REFERENCES gioi_tinh(id),
		cac_ten_goi_khac varchar(50) DEFAULT '',
		sinh_ngay datetime,
		noi_sinh varchar(100),
		que_quan varchar(100),
		dan_toc varchar(30), --TINYINT REFERENCES dan_toc(id),
		so_cccd varchar(12) UNIQUE,
		ngay_cap_cccd datetime,
		so_dien_thoai varchar(10) DEFAULT '',
		so_bhxh varchar(10),
		so_bhyt varchar(15),
		noi_o_hien_nay varchar(100),
		thanh_phan_gia_dinh_xuat_than varchar(30), --TINYINT REFERENCES thanh_phan_gia_dinh(id),
		nghe_nghiep_truoc_khi_duoc_tuyen_dung varchar(100) DEFAULT 'Không nghề nghiệp',
		ngay_duoc_tuyen_dung_lan_dau datetime,
		coquan_tochuc_donvi_tuyendung varchar(50), --TINYINT REFERENCES coquan_tochuc_donvi_tuyendung(id),
		ngay_vao_co_quan_hien_dang_cong_tac datetime,
		ngay_vao_dang_cong_san_viet_nam datetime,
		ngay_chinh_thuc datetime,
		ngay_tham_gia_to_chuc_chinh_tri_xa_hoi_dau_tien datetime,
		ngay_nhap_ngu datetime,
		ngay_xuat_ngu datetime,
		quan_ham_cao_nhat varchar(50), --INTEGER REFERENCES cap_bac_cap_loai_quan_ham_quan_doi(id),
		doi_tuong_chinh_sach varchar(100), --INTEGER REFERENCES doi_tuong_chinh_sach(id),
		trinh_do_giao_duc_pho_thong varchar(15), --INTEGER REFERENCES trinh_do_giao_duc_pho_thong(id),
		trinh_do_chuyen_mon_cao_nhat varchar(15), --INTEGER REFERENCES trinh_do_chuyen_mon(id),
		hoc_ham varchar(15) DEFAULT 'Không', --INTEGER REFERENCES hoc_ham(id),
		danh_hieu_nha_nuoc_phong_tang varchar(50), --INTEGER REFERENCES danh_hieu_nha_nuoc_phong_tang(id),
		chuc_vu_hien_tai varchar(150),
		ngay_bo_nhiem datetime,
		ngay_bo_nhiem_lai datetime,
		duoc_quy_hoach_chuc_danh varchar(50) DEFAULT '',
		chuc_vu_kiem_nhiem varchar(150) DEFAULT '',
		chuc_vu_dang_hien_tai varchar(100), --tinyint REFERENCES chuc_danh_dang(id),
		chuc_vu_dang_kiem_nhiem varchar(100), --tinyint REFERENCES chuc_danh_dang(id),
		cong_viec_chinh_duoc_giao varchar(150) DEFAULT '',
		so_truong_cong_tac varchar(150) DEFAULT '',
		cong_viec_lam_lau_nhat varchar(150) DEFAULT '',
		tien_luong double,
		ngach_nghe_nghiep varchar(100),
		ma_so_ngach_nghe_nghiep varchar(10),
		ngay_bo_nhiem_ngach_nghe_nghiep datetime,
		bac_luong_ngach_nghe_nghiep varchar(5), --INTEGER REFERENCES bac_luong(id),
		he_so_luong_ngach_nghe_nghiep float,
		ngay_huong_luong_ngach_nghe_nghiep datetime,
		phan_tram_huong_luong_ngach_nghe_nghiep DOUBLE,
		phu_cap_tham_nien_vuot_khung_ngach_nghe_nghiep FLOAT,
		ngay_huong_PCTNVK_ngach_nghe_nghiep datetime,
		phu_cap_chuc_vu float,
		phu_cap_kiem_nhiem float,
		phu_cap_khac float,
		vi_tri_viec_lam varchar(50),
		ma_so_vi_tri_viec_lam varchar(10),
		bac_luong_vi_tri_viec_lam DOUBLE,
		luong_theo_muc_tien DOUBLE DEFAULT 1800000,
		ngay_huong_luong_vi_tri_viec_lam datetime,
		phan_tram_huong_luong DOUBLE, --theo he so luong cong chuc hoac vien chuc,
		phu_cap_tham_nien_vuot_khung FLOAT,
		ngay_huong_PCTNVK datetime,
		tinh_trang_suc_khoe varchar(15), --tinyint REFERENCES tinh_trang_suc_khoe(id),
		chieu_cao FLOAT,
		can_nang FLOAT,
		nhom_mau varchar(10) --tinyint REFERENCES nhom_mau(id)
	);

CREATE TABLE
	sqlite_sequence (name, seq);

CREATE TABLE
	'thanh_phan_gia_dinh' (
		id TINYINT primary key,
		name varchar(50) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'tinh_trang_suc_khoe' (
		id INTEGER primary key AUTOINCREMENT,
		title varchar(15) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'tin_hoc' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		ten_co_so_dao_tao varchar(100),
		chung_chi_duoc_cap varchar(50),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'tom_tat_qua_trinh_cong_tac' (
		id INTEGER primary key AUTOINCREMENT,
		bat_dau datetime,
		ket_thuc datetime,
		don_vi_cong_tac varchar(100),
		chuc_danh varchar(100),
		loai_so_yeu_ly_lich_chitiet INTEGER REFERENCES loai_so_yeu_ly_lich_chitiet (id),
		create_at datetime DEFAULT CURRENT_DATE,
		update_at DEFAULT null
	);

CREATE TABLE
	'ton_giao' (
		id TINYINT primary key,
		name varchar(50) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'trinh_do_chuyen_mon' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(15) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

CREATE TABLE
	'trinh_do_giao_duc_pho_thong' (
		id INTEGER primary key AUTOINCREMENT,
		name varchar(15) UNIQUE,
		create_at datetime DEFAULT CURRENT_TIMESTAMP,
		update_at DEFAULT null
	);

-- INDEX
-- TRIGGER
-- VIEW
```
