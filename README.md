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
    string status[jumlah] = {
        "Dalam Proses",
        "Dikirim",
        "Selesai",
        "Dibatalkan",
        "Dalam Proses",
        "Dikirim"
    };

    string cari;
    cout << "=== SISTEM PENCARIAN DATA RAJA ES ===\n";
    cout << "Masukkan nama minuman yang ingin dicari: ";
    getline(cin, cari);

    bool ketemu = false;

    for (int i = 0; i < jumlah; i++) {
        if (nama[i] == cari) {
            cout << "\nData ditemukan!\n";
            cout << "Kode   : " << kode[i] << endl;
            cout << "Nama   : " << nama[i] << endl;
            cout << "Status : " << status[i] << endl;
            ketemu = true;
            break;
        }
    }

    if (!ketemu) {
        cout << "\nData tidak ditemukan!" << endl;
    }

    return 0;
}
```
