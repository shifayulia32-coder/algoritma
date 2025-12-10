
```
#include <iostream>
#include <string>
using namespace std;

int main() {

    const int jumlah = 15;

    int kode[jumlah] = {
        1001, 1002, 1003, 1004, 1005,
        1006, 1007, 1008, 1009, 1010,
        1011, 1012, 1013, 1014, 1015
    };

    string nama[jumlah] = {
        "Es teller",
        "Es jelly",
        "Es campur",
        "Es jeruk",
        "Es cincau",
        "Es kepal milo",
        "Es strawberry",
        "Es buah",
        "Es buah es krim",
        "Es doger",
        "Es oyen",
        "Es avocado",
        "Es durian",
        "Es rainbow",
        "Es coklat"
    };

    // Daftar harga sesuai urutan
    int harga[jumlah] = {
        12000, 10000, 15000, 8000, 9000,
        13000, 11000, 14000, 17000, 12000,
        15000, 16000, 20000, 13000, 10000
    };

    int pilihan;
    char ulang;

    do {
        cout << "\n========== MENU PENCARIAN RAJA ES ==========\n";
        cout << "1. Cari berdasarkan NAMA minuman\n";
        cout << "2. Cari berdasarkan KODE minuman\n";
        cout << "3. Tampilkan semua data minuman\n";
        cout << "4. Keluar\n";
        cout << "============================================\n";
        cout << "Pilih menu: ";
        cin >> pilihan;

        cin.ignore();

        // ======================= CARI NAMA =======================
        if (pilihan == 1) {
            string cariNama;
            cout << "\nMasukkan nama minuman: ";
            getline(cin, cariNama);

            bool ketemu = false;

            for (int i = 0; i < jumlah; i++) {
                if (nama[i] == cariNama) {
                    cout << "\nDATA DITEMUKAN!\n";
                    cout << "Kode   : " << kode[i] << endl;
                    cout << "Nama   : " << nama[i] << endl;
                    cout << "Harga  : Rp " << harga[i] << endl;
                    ketemu = true;
                    break;
                }
            }

            if (!ketemu) {
                cout << "\nData tidak ditemukan!\n";
            }

        // ====================== CARI KODE =========================
        } else if (pilihan == 2) {

            int cariKode;
            cout << "\nMasukkan kode minuman: ";
            cin >> cariKode;

            bool ketemu = false;

            for (int i = 0; i < jumlah; i++) {
                if (kode[i] == cariKode) {
                    cout << "\nDATA DITEMUKAN!\n";
                    cout << "Kode   : " << kode[i] << endl;
                    cout << "Nama   : " << nama[i] << endl;
                    cout << "Harga  : Rp " << harga[i] << endl;
                    ketemu = true;
                    break;
                }
            }

            if (!ketemu) {
                cout << "\nData tidak ditemukan!\n";
            }

        // ====================== TAMPILKAN SEMUA ===================
        } else if (pilihan == 3) {
            cout << "\n=== DAFTAR SEMUA MINUMAN ===\n";
            for (int i = 0; i < jumlah; i++) {
                cout << kode[i] << " - " << nama[i] 
                     << " - Rp " << harga[i] << endl;
            }

        } else if (pilihan == 4) {
            cout << "\nKeluar dari program...\n";
            break;
        } else {
            cout << "\nPilihan tidak valid!\n";
        }

        cout << "\nIngin kembali ke menu? (y/n): ";
        cin >> ulang;

    } while (ulang == 'y' || ulang == 'Y');

    cout << "\nTerima kasih telah menggunakan sistem pencarian RAJA ES!\n";

    return 0;
}

```
