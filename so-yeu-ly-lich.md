```sql
  --so yeu ly lich
  /*
  create table if not exists so_yeu_ly_lich (
  	anh_mau BLOB,
    	ho_va_ten varchar(50),
    	gioi_tinh TINYINT REFERENCES gioi_tinh(id),
    	cac_ten_goi_khac varchar(50) DEFAULT '',
  	sinh_ngay datetime,
    	noi_sinh varchar(100),
    	que_quan varchar(100),
    	dan_toc TINYINT REFERENCES dan_toc(id),
    	so_cccd varchar(12) UNIQUE,
    	ngay_cap_cccd datetime,
    	so_dien_thoai varchar(10) DEFAULT '',
    	so_bhxh varchar(10),
    	so_bhyt varchar(15),
    	noi_o_hien_nay varchar(100),
    	thanh_phan_gia_dinh_xuat_than TINYINT REFERENCES thanh_phan_gia_dinh(id),
    	nghe_nghiep_truoc_khi_duoc_tuyen_dung varchar(100) DEFAULT 'Không nghề nghiệp',
    	ngay_duoc_tuyen_dung_lan_dau datetime,
    	coquan_tochuc_donvi_tuyendung TINYINT FOREIGN KEY REFERENCES coquan_tochuc_donvi_tuyendung(id),
    	ngay_vao_co_quan_hien_dang_cong_tac datetime,
    	ngay_vao_dang_cong_san_viet_nam datetime,
    	ngay_chinh_thuc datetime
    	ngay_tham_gia_to_chuc_chinh_tri_xa_hoi_dau_tien_ngay_vao_doan_tncshcm_cong_doan_hoi datetime,
    	ngay_nhap_ngu datetime,
     	ngay_xuat_ngu datetime,
     	quan_ham_cao_nhat INTEGER FOREIGN KEY REFERENCES cap_bac_cap_loai_quan_ham_quan_doi(id),
    	doi_tuong_chinh_sach INTEGER FOREIGN KEY REFERENCES doi_tuong_chinh_sach(id),
      trinh_do_giao_duc_pho_thong INTEGER FOREIGN KEY REFERENCES trinh_do_giao_duc_pho_thong(id),
      trinh_do_chuyen_mon_cao_nhat INTEGER FOREIGN KEY REFERENCES trinh_do_chuyen_mon_cao_nhat(id),
    	hoc_ham INTEGER FOREIGN KEY REFERENCES hoc_ham(id),
    	danh_hieu_nha_nuoc_phong_tang INTEGER FOREIGN KEY REFERENCES danh_hieu_nha_nuoc_phong_tang(id),
      chuc_vu_hien_tai varchar(150),
    	ngay_bo_nhiem datetime,
    	ngay_bo_nhiem_lai datetime,
    	duoc_quy_hoach_chuc_danh varchar(50) DEFAULT '',
    	chuc_vu_kiem_nhiem varchar(150) DEFAULT '',
    	chuc_vu_dang_hien_tai tinyint FOREIGN KEY REFERENCES chuc_danh_dang(id),
    	chuc_vu_dang_kiem_nhiem tinyint FOREIGN KEY REFERENCES chuc_danh_dang(id),
    	cong_viec_chinh_duoc_giao varchar(150) DEFAULT '',
    	so_truong_cong_tac varchar(150) DEFAULT '',
    	cong_viec_lam_lau_nhat varchar(150) DEFAULT '',
    	tien_luong double,
    	ngach_nghe_nghiep varchar(100),
    	ma_so_ngach_nghe_nghiep varchar(10),
    	ngay_bo_nhiem_ngach_nghe_nghiep datetime,
    	bac_luong INTEGER FOREIGN KEY REFERENCES bac_luong(id),
    	luong_theo_muc_tien DOUBLE DEFAULT 1800000,
    	ngay_huong_luong datetime,
    	phan_tram_huong_luong DOUBLE --theo he so luong cong chuc hoac vien chuc,
    	phu_cap_tham_nien_vuot_khung FLOAT,
    	ngay_huong_PCTNVK datetime,
    	tinh_trang_suc_khoe tinyint FOREIGN key REFERENCES tinh_trang_suc_khoe(id),
    	chieu_cao FLOAT,
    	can_nang FLOAT,
    	nhom_mau tinyint FOREIGN key REFERENCES nhom_mau(id)
  );
  */
  create table if not exists so_yeu_ly_lich (
  	anh_mau BLOB,
    	ho_va_ten varchar(50),
    	gioi_tinh TINYINT REFERENCES gioi_tinh(id),
    	cac_ten_goi_khac varchar(50) DEFAULT '',
  	sinh_ngay datetime,
    	noi_sinh varchar(100),
    	que_quan varchar(100),
    	dan_toc TINYINT REFERENCES dan_toc(id),
    	so_cccd varchar(12) UNIQUE,
    	ngay_cap_cccd datetime,
    	so_dien_thoai varchar(10) DEFAULT '',
    	so_bhxh varchar(10),
    	so_bhyt varchar(15),
    	noi_o_hien_nay varchar(100),
    	thanh_phan_gia_dinh_xuat_than TINYINT REFERENCES thanh_phan_gia_dinh(id),
    	nghe_nghiep_truoc_khi_duoc_tuyen_dung varchar(100) DEFAULT 'Không nghề nghiệp',
    	ngay_duoc_tuyen_dung_lan_dau datetime,
    	coquan_tochuc_donvi_tuyendung TINYINT REFERENCES coquan_tochuc_donvi_tuyendung(id),
    	ngay_vao_co_quan_hien_dang_cong_tac datetime,
    	ngay_vao_dang_cong_san_viet_nam datetime,
    	ngay_chinh_thuc datetime
    	ngay_tham_gia_to_chuc_chinh_tri_xa_hoi_dau_tien_ngay_vao_doan_tncshcm_cong_doan_hoi datetime,
    	ngay_nhap_ngu datetime,
     	ngay_xuat_ngu datetime,
     	quan_ham_cao_nhat INTEGER REFERENCES cap_bac_cap_loai_quan_ham_quan_doi(id),
    	doi_tuong_chinh_sach INTEGER REFERENCES doi_tuong_chinh_sach(id),
      trinh_do_giao_duc_pho_thong INTEGER REFERENCES trinh_do_giao_duc_pho_thong(id),
      trinh_do_chuyen_mon_cao_nhat INTEGER REFERENCES trinh_do_chuyen_mon_cao_nhat(id),
    	hoc_ham INTEGER REFERENCES hoc_ham(id),
    	danh_hieu_nha_nuoc_phong_tang INTEGER REFERENCES danh_hieu_nha_nuoc_phong_tang(id),
      chuc_vu_hien_tai varchar(150),
    	ngay_bo_nhiem datetime,
    	ngay_bo_nhiem_lai datetime,
    	duoc_quy_hoach_chuc_danh varchar(50) DEFAULT '',
    	chuc_vu_kiem_nhiem varchar(150) DEFAULT '',
    	chuc_vu_dang_hien_tai tinyint REFERENCES chuc_danh_dang(id),
    	chuc_vu_dang_kiem_nhiem tinyint REFERENCES chuc_danh_dang(id),
    	cong_viec_chinh_duoc_giao varchar(150) DEFAULT '',
    	so_truong_cong_tac varchar(150) DEFAULT '',
    	cong_viec_lam_lau_nhat varchar(150) DEFAULT '',
    	tien_luong double,
    	ngach_nghe_nghiep varchar(100),
    	ma_so_ngach_nghe_nghiep varchar(10),
    	ngay_bo_nhiem_ngach_nghe_nghiep datetime,
    	bac_luong_ngach_nghe_nghiep INTEGER REFERENCES bac_luong(id),
    	he_so_luong_ngach_nghe_nghiep float,
    	ngay_huong_luong_ngach_nghe_nghiep datetime,
    	phu_cap_chuc_vu float,
    	phu_cap_kiem_nhiem float,
    	phu_cap_khac float,
    	vi_tri_viec_lam varchar(50),
    	ma_so_vi_tri_viec_lam varchar(10),
    	bac_luong_vi_tri_viec_lam DOUBLE,
    	luong_theo_muc_tien DOUBLE DEFAULT 1800000,
    	ngay_huong_luong_vi_tri_viec_lam datetime,
    	phan_tram_huong_luong DOUBLE --theo he so luong cong chuc hoac vien chuc,
    	phu_cap_tham_nien_vuot_khung FLOAT,
    	ngay_huong_PCTNVK datetime,
    	tinh_trang_suc_khoe tinyint REFERENCES tinh_trang_suc_khoe(id),
    	chieu_cao FLOAT,
    	can_nang FLOAT,
    	nhom_mau tinyint REFERENCES nhom_mau(id)
  );
```
