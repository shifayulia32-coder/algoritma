# algoritma
```
#include <iostream>
using namespace std;

// Prototipe fungsi
int faktorial(int n);

int main() {
    int n = 5;
    cout << "Faktorial dari " << n << " adalah: " << faktorial(n) << endl;
    return 0;
}

// Definisi fungsi
int faktorial(int n) {
    int hasil = 1;
    for(int i = 1; i <= n; i++) {
        hasil *= i;
    }
    return hasil;
}
```
```
#include <iostream>
#include <string>
using namespace std;

// =====================================
// STRUCT MAHASISWA
// =====================================
struct Mahasiswa {
    string NIM;
    string Nama;
    string Alamat;
    string Kelas;
    float Nilai;
};

// =====================================
// FUNGSI SEQUENTIAL SEARCH
// =====================================
int sequentialSearch(Mahasiswa mhs[], int n, string dicari) {
    for (int i = 0; i < n; i++) {
        if (mhs[i].Nama == dicari) {
            return i;   // ditemukan
        }
    }
    return -1; // tidak ditemukan
}

// =====================================
// FUNGSI BINARY SEARCH
// (Data harus terurut berdasarkan Nama)
// =====================================
int binarySearch(Mahasiswa mhs[], int n, string dicari) {
    int kiri = 0, kanan = n - 1;

    while (kiri <= kanan) {
        int tengah = (kiri + kanan) / 2;

        if (mhs[tengah].Nama == dicari)
            return tengah; // ditemukan

        else if (mhs[tengah].Nama < dicari)
            kiri = tengah + 1;

        else
            kanan = tengah - 1;
    }

    return -1; // tidak ditemukan
}

// =====================================
// MAIN PROGRAM
// =====================================
int main() {
    // Data mahasiswa
    Mahasiswa mhs[5] = {
        {"2301", "Alya", "Jl. Kenanga", "A", 88.5},
        {"2302", "Budi", "Jl. Melati", "A", 76.2},
        {"2303", "Citra", "Jl. Mawar", "B", 91.0},
        {"2304", "Dewi", "Jl. Dahlia", "B", 85.3},
        {"2305", "Evan", "Jl. Sakura", "A", 79.8}
    };

    int n = 5;
    string cari;
    int pilih;

    cout << "=====================================\n";
    cout << "     PROGRAM PENCARIAN MAHASISWA    \n";
    cout << "=====================================\n";

    cout << "Data Mahasiswa (terurut berdasarkan Nama):\n";
    for (int i = 0; i < n; i++) {
        cout << mhs[i].Nama << "  ";
    }
    cout << "\n\n";

    cout << "Masukkan Nama yang ingin dicari: ";
    getline(cin, cari);

    cout << "Pilih Metode Pencarian:\n";
    cout << "1. Sequential Search\n";
    cout << "2. Binary Search\n";
    cout << "Pilihan: ";
    cin >> pilih;

    int posisi;

    if (pilih == 1) {
        posisi = sequentialSearch(mhs, n, cari);
    } else {
        posisi = binarySearch(mhs, n, cari);
    }

    cout << "\n=====================================\n";

    if (posisi != -1) {
        cout << "Data ditemukan pada indeks: " << posisi << endl;
        cout << "NIM    : " << mhs[posisi].NIM << endl;
        cout << "Nama   : " << mhs[posisi].Nama << endl;
        cout << "Alamat : " << mhs[posisi].Alamat << endl;
        cout << "Kelas  : " << mhs[posisi].Kelas << endl;
        cout << "Nilai  : " << mhs[posisi].Nilai << endl;
    } else {
        cout << "Data mahasiswa dengan nama '" << cari << "' tidak ditemukan.\n";
    }

    cout << "=====================================\n";

    return 0;
}
```
```
include <iostream>
#include <string>
#include <algorithm>
using namespace std;
/* run this program using the console pauser or add your own getch, system("pause") or input loop */
struct Mahasiswa {
	string NIM;
	string Nama;
	string Alamat;
	string Kelas; 
	float Nilai;
};
int squentialSearch(Mahasiswa mhs[], int n, string key){
	for (int i = 0; i < n; i++) {
		if (mhs[i].Nama == key){
			return i;
		}
	}
	return -1;
}

bool bandingNama(const Mahasiswa &a, const Mahasiswa &b){
	return a.Nama < b.Nama;
}
int binarysearch(Mahasiswa mhs[], int n, string key) {
	int kiri = 0, kanan = n - 1;
	
	while (kiri <= kanan) {
		int tengah = (kiri + kanan) / 2;
		
		if (mhs[tengah].Nama == key)
		return tengah;
		else if(mhs[tengah].Nama < key)
		kiri = tengah + 1;
		else 
		kanan = tengah - 1;
	}
	return -1;
}
int main(int argc, char** argv) {
	int n; 
	cout << "masukkan jumlah data mahasiswa : ";
	cin >> n;
	
	Mahasiswa mhs [n];
	cin.ignore();
	
	for (int i = 0; i < n; i++) {
		cout << "\nData Mahasiswa ke-"<< i + 1 <<endl;
		cout << " NIM		: ";
		getline (cin, mhs[i].NIM);
		cout << "Nama		: ";
		getline (cin, mhs[i].Nama);
		cout << "Alamat		: ";
		getline (cin, mhs[i].Alamat);
		cout << "Kelas		: ";
		getline (cin, mhs[i].Kelas);
		cout << "Nilai		: ";
		cin >> mhs[i].Nilai;
		cin.ignore();
	}
	
	string cari;
	cout << "\nMasukkan nama yang dicari : ";
	getline(cin, cari);
	
	int hasil1 = squentialSearch(mhs, n, cari);
	
	sort(mhs, mhs + n, bandingNama);
	int hasil2 = binarysearch(mhs, n, cari);
	
	cout << "\n=== HASIL SQUENTIAL SERACH ===" << endl;
	if (hasil1 != -1)
	cout << "Data ditemukan pada indeks ke-"<< hasil1 <<endl;
	else 
		cout << "Data tidak ditemukan"<< endl;
	
	cout << "\n=== HASIL BINARY SEARCH ==="<< endl;
	if (hasil2 != -1)
	cout << "Data ditemukan pada indeks ke-"<<hasil2<< "(setelah sorting)"<<endl;
	else
		cout << "data ditemukan"<<endl;
	return 0;
}

