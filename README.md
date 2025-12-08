
```
#include <iostream>
#include <string>
using namespace std;

int main() {

    const int jumlah = 6;

    int kode[jumlah] = {101, 102, 103, 104, 105, 106};
    string nama[jumlah] = {
        "Es Teller",
        "Es Jelly Raja",
        "Es Campur",
        "Es Jeruk Segar",
        "Es Cincau Hijau",
        "Es Mangga Lumer"
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
                    cout << "Indeks : " << i << endl;   // <-- TAMPILKAN INDEKS
                    ketemu = true;
                    break;
                }
            }

            if (!ketemu) {
                cout << "\nData tidak ditemukan!\n";
            }

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
                    cout << "Indeks : " << i << endl;  // <-- TAMPILKAN INDEKS
                    ketemu = true;
                    break;
                }
            }

            if (!ketemu) {
                cout << "\nData tidak ditemukan!\n";
            }

        } else if (pilihan == 3) {
            cout << "\n=== DAFTAR SEMUA MINUMAN ===\n";
            for (int i = 0; i < jumlah; i++) {
                cout << "[" << i << "] " << kode[i] << " - " << nama[i] << endl;
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
