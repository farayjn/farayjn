#include<iostream>
#include<string>
#include<Windows.h>

using namespace std;

void header() {
	cout << "=================================================================================" << endl;
	cout << "                                 BOOKING HOTEL" << endl;
	cout << "=================================================================================" << endl;
	cout << endl;
}

void header2(string nama) {
	cout << "=================================================================================" << endl;
	cout << "                                 BOOKING HOTEL" << endl;
	cout << "=================================================================================" << endl;
	cout << "@" << nama << endl;
	cout << endl;
}

void yt() {
	cout << "1. Ya" << endl;
	cout << "2. Tidak" << endl;
	cout << "Masukan Pilihan Anda (1-2) : ";
}

void salahinput(string nama) {
	header2(nama);
	cout << "Anda salah memasukan pilihan, silahkan coba lagi" << endl;
	Sleep(1500);
	system("cls");
}

void tanggaltidakvalid(string nama) {
	header2(nama);
	cout << "Tanggal Yang Anda Masukan Tidak Valid, Silahkan Coba Lagi" << endl;
	Sleep(1500);
	system("cls");
}

void solo_serenity_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in	
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Serenity" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_serenity_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Serenity" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_serenity_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Serenity" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_zenith_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Zenith" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_zenith_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Zenith" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_zenith_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Zenith" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_mirage_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Mirage" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_mirage_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Mirage" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void solo_mirage_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Solo" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Mirage" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_panorama_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Panorama" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_panorama_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi		\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Panorama" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_panorama_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Panorama" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_infinia_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Infinia" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_infinia_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Infinia" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_infinia_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Infinia" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_solara_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Solara" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_solara_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Solara" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void jarakta_solara_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Jakarta" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Solara" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;


	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_synergy_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Synergy" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;


	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_synergy_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Synergy" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_synergy_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Synergy" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_odyssey_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Odyssey" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_odyssey_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Odyssey" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_odyssey_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}
	
	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Odyssey" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_elysium_standart(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1000000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Elysium" << endl;
	cout << "[*] Tipe Kamar	\t: Standart Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_elysium_deluxe(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1250000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}


	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Elysium" << endl;
	cout << "[*] Tipe Kamar	\t: Deluxe Room" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}

void bali_elysium_presidential(string nama) {
	string namapemesan, kode, nomortelp;
	int din, dout, min, mout, yin, yout, jumlahkamar, harga, ditemukan = 0, hargadiskon;
	int hargakamar = 1500000;
	int diskon = 80;

	string Promo[4] = { "diskonmurah", "palingmurah", "palingmurahseindonesia" };

	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: ";
	cin >> namapemesan;
	system("cls");

	mengulangnomortelp:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: ";
	cin >> nomortelp;
	system("cls");
	if (nomortelp.length() >= 10 && nomortelp.length() <= 13) {
		goto lanjut;
	}
	else {
		header2(nama);
		cout << "Nomor Telepon Yang Anda Masukan Tidak Valid" << endl;
		Sleep(1500);
		system("cls");
		goto mengulangnomortelp;
	}

	lanjut:
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: ";
	cin >> jumlahkamar;
	system("cls");

	CI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;

	//user memasukan tanggal check in
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: ";
	cin >> din;
	cout << "	Bulan	\t: ";
	cin >> min;
	cout << "	Tahun	\t: ";
	cin >> yin;

	//memeriksa tanggal check in
	if (yin >= 1000 && yin <= 9999) {
		if (min >= 1 && min <= 12) {
			if (min == 1 || min == 3 || min == 5 || min == 7 || min == 8 || min == 10 || min == 12) {
				if (din >= 1 && din <= 31) {
					system("cls");
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CI;
				}
			}
			else if (min == 4 || min == 6 || min == 9 || min == 11) {
				if (din >= 1 && din <= 30) {
					system("cls");;
					goto CO;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					system("cls");
					goto CI;
				}
			}
			else if (min == 2) {
				int s;
				s = yin % 4;
				if (s == 0) {
					if (din >= 1 && din <= 29) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CI;
					}
				}
				else if (s != 0) {
					if (din >= 1 && din <= 28) {
						system("cls");
						goto CO;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						system("cls");
						goto CI;

					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CI;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CI;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CI;
	}

	CO:
	//menampilkan ulang 
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;

	//user memasukan tanggal check out
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: ";
	cin >> dout;
	cout << "	Bulan	\t: ";
	cin >> mout;
	cout << "	Tahun	\t: ";
	cin >> yout;

	//memeriksa tanggal check out
	if (yout >= 1000 && yout <= 9999) {
		if (mout >= 1 && mout <= 12) {
			if (mout == 1 || mout == 3 || mout == 5 || mout == 7 || mout == 8 || mout == 10 || mout == 12) {
				if (dout >= 1 && dout <= 31) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 4 || mout == 6 || mout == 9 || mout == 11) {
				if (dout >= 1 && dout <= 30) {
					system("cls");
					goto COCI;
				}
				else {
					system("cls");
					tanggaltidakvalid(nama);
					goto CO;
				}
			}
			else if (mout == 2) {
				int s;
				s = yout % 4;
				if (s == 0) {
					if (dout >= 1 && dout <= 29) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
				else if (s != 0) {
					if (dout >= 1 && dout <= 28) {
						system("cls");
						goto COCI;
					}
					else {
						system("cls");
						tanggaltidakvalid(nama);
						goto CO;
					}
				}
			}
			else {
				system("cls");
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {
			system("cls");
			tanggaltidakvalid(nama);
			goto CO;;
		}
	}
	else {
		system("cls");
		tanggaltidakvalid(nama);
		goto CO;
	}

	//memeriksa apakah tanggal check out lebih lama dibandingkan tanggal check in
	COCI:
	if (yout > yin) {
		system("cls");
		goto sisaCOCI;
	}
	else if (yout == yin) {
		if (mout > min) {
			system("cls");
			goto sisaCOCI;
		}
		else if (mout == min) {
			if (dout > din) {
				system("cls");
				goto sisaCOCI;
			}
			else {
				tanggaltidakvalid(nama);
				goto CO;
			}
		}
		else {  
			tanggaltidakvalid(nama);
			goto CO;
		}
	}
	else {
		tanggaltidakvalid(nama);
		goto CO;
	}

	sisaCOCI:
	//menampilkan ulang
	header2(nama);
	cout << "Silahkan Isi Data Berikut " << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;

	//menghitung jumlah hari
	int bulan = 0, lama, jumlah = 0, jumlah2 = 0, jumlah3 = 0, total = 0, sisahari, sisahari2 = 0;

	int m[13] = { 0,31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

	if (yin == yout) {
		if (mout == min) {
			lama = dout - din;
		}
		else if (mout > min) {
			for (int i = min + 1; i <= mout - 1; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			lama = jumlah + sisahari + dout;
		}
	}
	else if (yout > yin) {
		if (yout - yin == 1) {
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			total = jumlah + sisahari;
			for (int i = 1; i <= (mout - 1); i++) {
				jumlah2 = jumlah2 + m[i];
			}
			lama = total + jumlah2 + dout;
		}
		else if (yout - yin != 1) {
			jumlah2 = (yout - (yin + 1)) * 365;
			for (int i = min + 1; i <= 12; i++) {
				jumlah = jumlah + m[i];
			}
			sisahari = m[min] - din;
			for (int i = 1; i <= mout - 1; i++) {
				jumlah3 = jumlah3 + m[i];
			}
			lama = jumlah + jumlah2 + jumlah3 + sisahari + dout;
		}
	}

	//menampilkan data pemesanan
	system("cls");
	header2(nama);
	cout << "Data Pemesanan " << endl;
	cout << "[*] Lokasi	\t: Bali" << endl;
	cout << "[*] Nama Hotel	\t: Hotel Elysium" << endl;
	cout << "[*] Tipe Kamar	\t: Presidential Suite" << endl;
	cout << "[*] Nama	\t: " << namapemesan << endl;
	cout << "[*] Nomor Telepon\t: " << nomortelp << endl;
	cout << "[*] Jumlah Kamar\t: " << jumlahkamar << endl;
	cout << "[*] Tanggal Check In" << endl;
	cout << "	Tanggal	\t: " << din << endl;
	cout << "	Bulan	\t: " << min << endl;
	cout << "	Tahun	\t: " << yin << endl;
	cout << "[*] Tanggal Check Out" << endl;
	cout << "	Tanggal	\t: " << dout << endl;
	cout << "	Bulan	\t: " << mout << endl;
	cout << "	Tahun	\t: " << yout << endl;
	cout << "[*] Lama Booking\t: " << lama << " hari" << endl;



	harga = lama * jumlahkamar * hargakamar;
	cout << "[*] Total Harga	\t: Rp. " << harga << endl;

	cout << endl;
	cout << "Jika Anda Memiliki Kode Promo Silahkan Diisi, Jika Tidak Punya Tulis 'Tidak'" << endl;
	cout << "[*] Kode Promo\t: ";
	cin >> kode;

	if (kode != "Tidak" && kode != "tidak") {
		for (int i = 0; i < 4; i++) {

			if (kode == Promo[i]) {
				ditemukan = 1;
				hargadiskon = (harga * diskon) / 100;
				cout << endl;
				cout << "Anda Mendapatkan Potongan Harga" << endl;
				cout << "[*] Total Harga Setelah Diskon\t: Rp. " << hargadiskon << endl;
			}
		}
		if (ditemukan == 0) {
			cout << endl;
			cout << "Anda Tidak Mendapatkan Potongan Harga" << endl;
		}
	}
}



int main() {
	string pil, password;


	//ARRAY NAMA HOTEL SOLO
	string NamaHotelSolo[5]{ "Hotel Serenity", "Hotel Zenith", "Hotel Mirage", "Kembali", "Keluar" };


	//ARRAY NAMA HOTEL JAKARTA
	string NamaHotelJakarta[5]{ "Hotel Panorama", "Hotel Infinia", "Hotel Solara", "Kembali", "Keluar" };


	//ARRAY NAMA HOTEL BALI
	string NamaHotelBali[5]{ "Hotel Synergy", "Hotel Odyssey", "Hotel Elysium", "Kembali", "Keluar" };


	//ARRAY TIPE KAMAR
	string TipeKamar[5]{ "Standart Room", "Deluxe Room", "Presidential Suite", "Kembali", "Keluar" };


	string PenjelasanTipe[3];
	PenjelasanTipe[0] = { "Kamar hotel standar adalah tipe kamar dasar dengan fasilitas seperti tempat tidur,\nkamar mandi pribadi, dan perabotan sederhana.Harganya relatif terjangkau dan\nmenyediakan kenyamanan dasar untuk penginapan.\n" };
	PenjelasanTipe[1] = { "Kamar Deluxe adalah tipe kamar hotel yang menawarkan fasilitas dan kenyamanan\nlebih dari standar room. Biasanya, ini mencakup ruang yang lebih besar, dekorasi\nyang lebih mewah, dan mungkin tambahan fasilitas seperti minibar atau\npemandangan yang lebih baik. Harganya lebih tinggi daripada standar room karena\nmenawarkan pengalaman menginap yang lebih eksklusif.\n" };
	PenjelasanTipe[2] = { "Presidential Suite adalah tipe kamar hotel paling mewah dengan ruang besar, fasilitas\nkelas atas, dan desain eksklusif. Biasanya dipesan oleh tamu terkemuka, selebritas,\natau pejabat tinggi, suite ini menawarkan pengalaman menginap yang istimewa\ndengan harga yang sangat tinggi.\n" };



	//array untuk menampung data akun
	string data[2][50];

	int ditemukan = 0, ditemukan2 = 0, nako, pako, s = 0;;
	string nama, pass;
	//menu register/buat akun
	menulogin:
	header();
	cout << "1. Login" << endl;
	cout << "2. Register" << endl;
	cout << "3. Keluar" << endl;
	cout << "Masukan Pilihan Anda (1-3) : ";
	cin >> pil;
	system("cls");

	//login
	if (pil == "1") {
		//user memasukan username
		loginun:
		header();
		cout << "[*] Masukan username : ";
		cin >> nama;

		//memeriksa username
		for (int k = 0; k < 50; k++) {
			for (int b = 0; b < 2; b++) {
				if (data[b][k] == nama) {
					ditemukan = 1;
					nako = k;
					if (b == 0) {
						system("cls");
						goto loginpw;
					}
					else {
						system("cls");
						header();
						cout << "Username Anda Tidak Terdaftar" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
				}
			}
		}

		//jika username tidak ditemukan
		if (ditemukan == 0) {
			cout << "Username Anda Tidak Terdaftar" << endl;
			Sleep(1500);
			system("cls");
			goto menulogin;
		}


		//user memasukan username
		loginpw:
		header();
		cout << "[*] Masukan username : " << nama << endl;
		cout << "[*] Masukan password : ";
		cin >> pass;

		//memeriksa password
		for (int k = 0; k < 50; k++) {
			for (int b = 0; b < 2; b++) {
				if (data[b][k] == pass) {
					ditemukan2 = 1;
					pako = k;

					if (b == 1) {

						//jika username & password sesuai
						if (nako == pako) {
							cout << "Login Anda Berhasil" << endl;
							Sleep(1500);
							system("cls");
							goto PemilihanLokasiHotel;
						}

						//jika tidak username & password sesuai
						else {
							cout << "Username & Password Anda Tidak Sesuai" << endl;
							Sleep(1500);
							system("cls");
							goto menulogin;
						}
					}
					else {
						system("cls");
						header();
						cout << "Password Anda Tidak Terdaftar" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
				}
			}
		}

		//jika password tidak ditemukan
		if (ditemukan2 == 0) {
			cout << "Password Anda Tidak Terdaftar" << endl;
			Sleep(500);
			system("cls");
			goto menulogin;
		}
	}


	//buat akun
	else if (pil == "2") {
		buatakun:
		header();

		for (int k = s; k < 50; k++) {
			for (int b = 0; b < 2; b++) {
				if (b == 0) {
					cout << "[*] Masukan Username : ";
					cin >> data[b][k];
				}
				else if (b == 1) {
					cout << "[*] Masukan Password : ";
					cin >> data[b][k];
				}

			}
			cout << "Akun Anda Sudah Berhasil Dibuat" << endl;
			s++;
			Sleep(1500);
			system("cls");
			goto menulogin;
		}
	}


	//keluar
	else if (pil == "3") {
		exit(0);
	}


	//lihat data akun
	else if (pil == "qwert") {
		header();
		cout << "\tData Akun" << endl;
		cout << "\nNama\tPassword\n";
		for (int x = 0; x <= s; x++) {
			for (int z = 0; z < 2; z++) {
				cout << data[z][x] << "\t";
			}
			cout << endl;
		}
		cout << "Tekann 'K' untuk kembali :";
		cin >> pil;
		if (pil == "K" || pil == "k") {
			system("cls");
			goto menulogin;
		}
		else {
			system("cls");
			header();
			cout << "Tanggal Yang Anda Masukan Tidak Valid, Silahkan Coba Lagi" << endl;
			Sleep(1500);
			system("cls");
			goto menulogin;
		}
	}


	//salah input
	else {
		header();
		cout << "Anda salah memasukan pilihan, silahkan coba lagi" << endl;
		Sleep(1500);
		system("cls");
		goto menulogin;
	}



	//menu pilihan lokasi hotel
	PemilihanLokasiHotel:
	header2(nama);
	cout << "Pilihan Lokasi Hotel Yang Tersedia :" << endl;
	cout << "1. Solo" << endl;
	cout << "2. Jakarta" << endl;
	cout << "3. Bali" << endl;
	cout << "4. Logout" << endl;
	cout << "5. Keluar" << endl;
	cout << "Masukan Pilihan Anda (1-5) : ";
	cin >> pil;
	system("cls");


	//SOLO
	if (pil == "1") {
		solo:
		header2(nama);
		cout << "Pilihan Hotel Yang Tersedia Di Solo :" << endl;

		//menampilkan nama hotel di solo
		for (int i = 0; i < 5; i++) {
			cout << i + 1 << ". " << NamaHotelSolo[i] << endl;
		}

		cout << "Masukan Pilihan Anda (1-5) : ";
		cin >> pil;
		system("cls");


		//SOLO_SERENITY
		if (pil == "1") {

			tipekamar_solo_serenity:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Serenity Solo :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");


			//solo serenity standart room
			if (pil == "1") {

				//memberikan penjelasan tentang kamar
				penjelasan1:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");

				if (pil == "1") {
					solo_serenity_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w1:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q1:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang1;
								}

								else {
									salahinput(nama);
									goto q1;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang1;
					}

					else {
						salahinput(nama);
						goto w1;
					}


				}

				else if (pil == "2") {
					ulang1:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_serenity;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang1;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan1;
				}

			}//tutup solo serenity standart room


			//solo serenity deluxe room
			else if (pil == "2") {

				//memberikan penjelasan tentang kamar
				penjelasan2:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");



				if (pil == "1") {
					solo_serenity_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w2:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q2:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang2;
								}

								else {
									salahinput(nama);
									goto q2;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang2;
					}

					else {
						salahinput(nama);
						goto w2;
					}


				}

				else if (pil == "2") {
					ulang2:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_serenity;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang2;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan2;
				}
			}//tutup solo serenity deluxe room


			//solo serenity presidential suite
			else if (pil == "3") {

				//memberikan penjelasan tentang kamar
				penjelasan3:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");



				if (pil == "1") {
					solo_serenity_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w3:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q3:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang3;
								}

								else {
									salahinput(nama);
									goto q3;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang3;
					}

					else {
						salahinput(nama);
						goto w3;
					}


				}

				else if (pil == "2") {
					ulang3:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_serenity;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang3;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan3;
				}
			}//tutup solo serenity presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}


			//user salah input
			else {
				salahinput(nama);
				goto tipekamar_solo_serenity;
			}

		}//TUTUP_SOLO_SERENITY


		//SOLO_ZENITH
		else if (pil == "2") {

			tipekamar_solo_zenith:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Zenith Solo :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";

			cin >> pil;
			system("cls");


			//solo zenith standart room
			if (pil == "1") {

				//memberikan penjelasan tentang kamar
				penjelasan4:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");



				if (pil == "1") {
					solo_zenith_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w4:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q4:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang4;
								}

								else {
									salahinput(nama);
									goto q4;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang4;
					}

					else {
						salahinput(nama);
						goto w4;
					}


				}

				else if (pil == "2") {
					ulang4:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_zenith;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang4;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan4;
				}
			}//tutup solo zenith standart room


			//solo zenith deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan5:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					solo_zenith_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w5:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q5:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang5;
								}

								else {
									salahinput(nama);
									goto q5;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang5;
					}

					else {
						salahinput(nama);
						goto w5;
					}


				}

				else if (pil == "2") {
					ulang5:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_zenith;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang5;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan5;
				}
			}//tutup solo zenith deluxe room


			//solo zenith presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan6:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					solo_zenith_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w6:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q6:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang6;
								}

								else {
									salahinput(nama);
									goto q6;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang6;
					}

					else {
						salahinput(nama);
						goto w6;
					}


				}

				else if (pil == "2") {
					ulang6:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_zenith;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang6;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan6;
				}
			}//tutup solo zenith presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}


			//user salah input
			else {
				salahinput(nama);
				goto tipekamar_solo_serenity;
			}
		}//TUTUP_SOLO_ZENITH


		//SOLO_MIRAGE
		else if (pil == "3") {

			tipekamar_solo_mirage:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Mirage Solo :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");


			//solo mirage standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan7:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					solo_mirage_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w7:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q7:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang7;
								}

								else {
									salahinput(nama);
									goto q7;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang7;
					}

					else {
						salahinput(nama);
						goto w7;
					}


				}

				else if (pil == "2") {
					ulang7:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_mirage;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang7;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan7;
				}
			}//tutup solo mirage standart room


			//solo mirage deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan8:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					solo_mirage_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w8:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q8:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang8;
								}

								else {
									salahinput(nama);
									goto q8;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang8;
					}

					else {
						salahinput(nama);
						goto w8;
					}


				}

				else if (pil == "2") {
					ulang8:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_mirage;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang8;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan8;
				}
			}//tutup solo mirage deluxe room


			//solo mirage presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan9:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					solo_mirage_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w9:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q9:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang9;
								}

								else {
									salahinput(nama);
									goto q9;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang9;
					}

					else {
						salahinput(nama);
						goto w9;
					}


				}

				else if (pil == "2") {
					ulang9:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_solo_mirage;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang9;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan9;
				}
			}//tutup solo mirage presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}


			//user salah input
			else {
				salahinput(nama);
				goto tipekamar_solo_mirage;
			}
		}//TUTUP_SOLO_MIRAGE


		//KEMBALI
		else if (pil == "4") {
			goto PemilihanLokasiHotel;
		}


		//KELUAR
		else if (pil == "5") {
			exit;
		}


		//USER SALAH INPUT
		else {
			salahinput(nama);
			goto solo;
		}
	}//TUTUP SOLO


	//JAKARTA
	else if (pil == "2") {
		jakarta:
		header2(nama);
		cout << "Pilihan Hotel Yang Tersedia Di Jakarta :" << endl;

		//menampilkan nama hotel di solo
		for (int i = 0; i < 5; i++) {
			cout << i + 1 << ". " << NamaHotelJakarta[i] << endl;
		}

		cout << "Masukan Pilihan Anda (1-5) : ";
		cin >> pil;
		system("cls");

		//JAKARTA_PANORAMA
		if (pil == "1") {

		tipekamar_jakarta_panorama:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Panorama Jakarta :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");



			//jakarta panorama standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan10:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_panorama_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w10:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q10:
								header2(nama);;
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang10;
								}

								else {
									salahinput(nama);
									goto q10;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang10;
					}

					else {
						salahinput(nama);
						goto w10;
					}


				}

				else if (pil == "2") {
					ulang10:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_panorama;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang10;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan10;
				}
			}//tutup jakarta panorama standart room


			//jakarta panorama deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan11:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_panorama_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w11:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q11:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang11;
								}

								else {
									salahinput(nama);
									goto q11;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang11;
					}

					else {
						salahinput(nama);
						goto w11;
					}


				}

				else if (pil == "2") {
					ulang11:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_panorama;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang11;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan11;
				}
			}//tutup jakarta panorama deluxe room


			//jakarta panorama presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan12:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_panorama_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w12:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q12:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang12;
								}

								else {
									salahinput(nama);
									goto q12;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang12;
					}

					else {
						salahinput(nama);
						goto w12;
					}


				}

				else if (pil == "2") {
					ulang12:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_panorama;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang12;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan12;
				}
			}//jakarta panorama presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}
		}//TUTUP_JAKARTA_PANORAMA


		//JAKARTA_INFINIA
		else if (pil == "2") {

			tipekamar_jakarta_infinia:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Infinia Jakarta :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");


			//jakarta infinia standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan13:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_infinia_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w13:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q13:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang13;
								}

								else {
									salahinput(nama);
									goto q13;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang13;
					}

					else {
						salahinput(nama);
						goto w13;
					}


				}

				else if (pil == "2") {
					ulang13:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_infinia;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang13;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan13;
				}
			}//tutup jakarta infinia standart room


			//jakarta infinia deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan14:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_infinia_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w14:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q14:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang14;
								}

								else {
									salahinput(nama);
									goto q14;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang14;
					}

					else {
						salahinput(nama);
						goto w14;
					}


				}

				else if (pil == "2") {
					ulang14:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_infinia;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang14;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan14;
				}
			}//tutup jakarta infinia deluxe room


			//jakarta infinia presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan15:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_infinia_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w15:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q15:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang15;
								}

								else {
									salahinput(nama);
									goto q15;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang15;
					}

					else {
						salahinput(nama);
						goto w15;
					}


				}

				else if (pil == "2") {
					ulang15:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_infinia;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang15;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan15;
				}
			}//tutup jakarta infinia presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}
		}//TUTUP_JAKARTA_INFINIA


		//JAKARTA_SOLARA
		else if (pil == "3") {

			tipekamar_jakarta_solara:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Solara Jakarta :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");


			//jakarta solara standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan16:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_solara_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w16:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q16:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang16;
								}

								else {
									salahinput(nama);
									goto q16;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang16;
					}

					else {
						salahinput(nama);
						goto w16;
					}


				}

				else if (pil == "2") {
					ulang16:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_solara;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang16;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan16;
				}
			}//tutup jakarta solara standart room


			//jakarta solara deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan17:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_solara_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w17:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q17:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang16;
								}

								else {
									salahinput(nama);
									goto q17;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang17;
					}

					else {
						salahinput(nama);
						goto w17;
					}


				}

				else if (pil == "2") {
					ulang17:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_solara;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang17;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan17;
				}
			}//tutup jakarta solara deluxe room


			//jakarta solara presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan18:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					jarakta_solara_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w18:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q18:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang18;
								}

								else {
									salahinput(nama);
									goto q18;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang18;
					}

					else {
						salahinput(nama);
						goto w18;
					}


				}

				else if (pil == "2") {
				ulang18:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_jakarta_solara;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang18;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan18;
				}
			}//tutup jakarta solara presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}
		}//TUTUP_JAKARTA SOLARA


		//KEMBALI
		else if (pil == "4") {
			goto PemilihanLokasiHotel;
		}


		//KELUAR
		else if (pil == "5") {
			exit;
		}


		//USER SALAH INPUT
		else {
			salahinput(nama);
			goto jakarta;
		}
	}//TUTUP JAKARTA


	//BALI
	else if (pil == "3") {
		bali:
		header2(nama);
		cout << "Pilihan Hotel Yang Tersedia Di Bali :" << endl;

		//menampilkan nama hotel di solo
		for (int i = 0; i < 5; i++) {
			cout << i + 1 << ". " << NamaHotelBali[i] << endl;
		}

		cout << "Masukan Pilihan Anda (1-5) : ";
		cin >> pil;
		system("cls");


		//BALI_SYNERGY
		if (pil == "1") {

			tipekamar_bali_synergy:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Synergy Bali :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");


			//bali synergy standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan19:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_synergy_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w19:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q19:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang19;
								}

								else {
									salahinput(nama);
									goto q19;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang19;
					}

					else {
						salahinput(nama);
						goto w19;
					}


				}

				else if (pil == "2") {
					ulang19:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_synergy;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang19;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan19;
				}
			}//tutup bali synergy standart room


			//bali synergy deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan20:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_synergy_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w20:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q20:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang20;
								}

								else {
									salahinput(nama);
									goto q20;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang20;
					}

					else {
						salahinput(nama);
						goto w20;
					}


				}

				else if (pil == "2") {
					ulang20:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_synergy;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang20;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan20;
				}
			}//tutup bali synergy deluxe room


			//bali synergy presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan21:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_synergy_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w21:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q21:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang21;
								}

								else {
									salahinput(nama);
									goto q21;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang21;
					}

					else {
						salahinput(nama);
						goto w21;
					}


				}

				else if (pil == "2") {
					ulang21:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_synergy;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang21;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan21;
				}
			}//tutup bali synergy presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}
		}//TUTUP_BALI_SYNERGY


		//BALI_ODYSSEY
		else if (pil == "2") {

			tipekamar_bali_odyssey:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Serenity Solo :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");



			//bali odyssey standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan22:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_odyssey_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w22:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q22:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang22;
								}

								else {
									salahinput(nama);
									goto q22;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang22;
					}

					else {
						salahinput(nama);
						goto w22;
					}


				}

				else if (pil == "2") {
					ulang22:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_odyssey;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang22;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan22;
				}
			}//tutup bali odyssey standart room


			//bali odyssey deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan23:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_odyssey_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w23:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q23:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang23;
								}

								else {
									salahinput(nama);
									goto q23;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang23;
					}

					else {
						salahinput(nama);
						goto w23;
					}


				}

				else if (pil == "2") {
					ulang23:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_odyssey;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang23;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan23;
				}
			}//bali odyssey deluxe room


			//bali odyssey presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan24:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_odyssey_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w24:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q24:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang24;
								}

								else {
									salahinput(nama);
									goto q24;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang24;
					}

					else {
						salahinput(nama);
						goto w24;
					}


				}

				else if (pil == "2") {
					ulang24:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_odyssey;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang24;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan24;
				}
			}//tutup bali odyssey presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}
		}//TUTUP_BALI_ODYSSEY


		//BALI_ELYSIUM
		else if (pil == "3") {

			tipekamar_bali_elysium:
			header2(nama);
			cout << "Tipe Kamar Yang Tersedia Di Hotel Elysium Bali :" << endl;
			for (int i = 0; i < 5; i++) {
				cout << i + 1 << ". " << TipeKamar[i] << endl;
			}
			cout << "Masukan Pilihan Anda (1-5) : ";
			cin >> pil;
			system("cls");


			//bali elysium standart room
			if (pil == "1") {


				//memberikan penjelasan tentang kamar
				penjelasan25:
				header2(nama);
				cout << PenjelasanTipe[0];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_elysium_standart(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w25:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q25:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang25;
								}

								else {
									salahinput(nama);
									goto q25;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang25;
					}

					else {
						salahinput(nama);
						goto w25;
					}


				}

				else if (pil == "2") {
					ulang25:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_elysium;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang25;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan25;
				}
			}//tutup bali elysium standart room


			//bali elysium deluxe room
			else if (pil == "2") {


				//memberikan penjelasan tentang kamar
				penjelasan26:
				header2(nama);
				cout << PenjelasanTipe[1];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_elysium_deluxe(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w26:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q26:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang26;
								}

								else {
									salahinput(nama);
									goto q26;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang26;
					}

					else {
						salahinput(nama);
						goto w26;
					}


				}

				else if (pil == "2") {
					ulang26:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_elysium;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang26;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan26;
				}
			}//tutup bali elysium deluxe room


			//bali elysium presidential suite
			else if (pil == "3") {


				//memberikan penjelasan tentang kamar
				penjelasan27:
				header2(nama);
				cout << PenjelasanTipe[2];
				//konfirmasi pemesanan 
				cout << "Apakah Anda Ingin Memesan Kamar Ini ? " << endl;
				yt();
				cin >> pil;
				system("cls");


				if (pil == "1") {
					bali_elysium_presidential(nama);
					/////////////////////////////////////////////////////////////////////
					Sleep(4000);
					system("cls");
					w27:
					header2(nama);
					cout << "Apakah Anda Ingin Memesan Hotel Terdebut : " << endl;
					yt();
					cin >> pil;
					system("cls");

					//jika melanjutkan pemesanan hotel
					if (pil == "1") {

						for (int i = 0; i < 3; i++) {
							header2(nama);
							cout << "[*] Masukan Password Anda : ";
							cin >> password;
							system("cls");

							if (password == pass) {
								header2(nama);
								cout << "Selamat Booking Hotel Anda Berhasil" << endl;
								Sleep(1500);
								system("cls");

								//menanyakan user apakah mau memesan hotel kembali
								q27:
								header2(nama);
								cout << "Apakah Anda Ingin Memesan Hotel Lagi ?" << endl;
								yt();
								cin >> pil;
								system("cls");

								if (pil == "1") {
									goto PemilihanLokasiHotel;
								}

								else if (pil == "2") {
									goto ulang27;
								}

								else {
									salahinput(nama);
									goto q27;

								}

							}

							header2(nama);
							cout << "Anda Salah Memasukan Password" << endl;
							Sleep(1500);
							system("cls");
						}

						//jika user sudah 3 kali salah memasukan password maka akan langsumg kembali ke menu awal
						header2(nama);
						cout << "Anda Sudah 3 Kali Memasukan password Yang Salah" << endl;
						Sleep(1500);
						system("cls");
						goto menulogin;
					}
					//jika tidak melanjutkan pemesanan hotel
					else if (pil == "2") {
						goto ulang27;
					}

					else {
						salahinput(nama);
						goto w27;
					}


				}

				else if (pil == "2") {
					ulang27:
					header2(nama);
					cout << "1. Kembali" << endl;
					cout << "2. Keluar" << endl;
					cout << "Masukan Pilihan Anda (1-2) : ";
					cin >> pil;
					system("cls");

					if (pil == "1") {
						system("cls");
						goto tipekamar_bali_elysium;
					}
					else if (pil == "2") {
						exit;
					}
					else {
						salahinput(nama);
						goto ulang27;
					}
				}

				else {
					salahinput(nama);
					goto penjelasan27;
				}
			}//tutup bali elysium presidential suite


			//kembali
			else if (pil == "4") {
				system("cls");
				goto solo;
			}


			//keluar
			else if (pil == "5") {
				exit;
			}
		}//TUTUP_BALI_ELYSIUM


		//KEMBALI
		else if (pil == "4") {
			goto PemilihanLokasiHotel;
		}


		//KELUAR
		else if (pil == "5") {
			exit;
		}


		//USER SALAH INPUT
		else {
			salahinput(nama);
			goto jakarta;
		}
	}//TUTUP BALI


	//LOGOUT
	else if (pil == "4") {
		goto menulogin;
	}


	//KELUAR
	else if (pil == "5") {
		exit;
	}


	//USER SALAH INPUT
	else {
		salahinput(nama);
		goto PemilihanLokasiHotel;
	}
}
