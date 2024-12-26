//tiket_konser
#include <iostream>
#include <iomanip> // Untuk mengatur format output
#include <string>
using namespace std;

int main() {
    char ulang; // Variabel untuk menentukan apakah ingin input ulang
    double grandTotalHarga = 0;   // Akumulasi total harga
    double grandPotongan = 0;     // Akumulasi potongan
    double grandTotalBayar = 0;   // Akumulasi total bayar
    double grandTotalKembalian = 0; // Akumulasi total kembalian
    string namaPembeli;

    // Input data utama
    cout << "Penjualan Tiket Konser Musik 2024\n";
    cout << "---------------------------------\n";
    cout << "Masukkan Nama Pembeli: ";
    getline(cin, namaPembeli);

    do {
        string kodeKonser;
        int jenisTiket, jumlahBeli;
        double hargaTiket, totalHarga, potongan = 0, totalBayar, uangBayar, uangKembali;

        cout << "Masukkan Kode Konser (JB/BM/BC): ";
        cin >> kodeKonser;
        cout << "Jenis Tiket (1. VVIP, 2. VIP, 3. Tribun): ";
        cin >> jenisTiket;
        cout << "Jumlah Beli: ";
        cin >> jumlahBeli;

        // Menentukan harga tiket berdasarkan kode konser dan jenis tiket
        if (kodeKonser == "JB") {
            if (jenisTiket == 1) {
                hargaTiket = 12000000; // Harga VVIP JB
            } else if (jenisTiket == 2) {
                hargaTiket = 6000000; // Harga VIP JB
            } else if (jenisTiket == 3) {
                hargaTiket = 1500000;  // Harga Tribun JB
            } else {
                cout << "Jenis tiket tidak valid!\n";
                continue;
            }
        } else if (kodeKonser == "BM") {
            if (jenisTiket == 1) {
                hargaTiket = 8500000; // Harga VVIP BM
            } else if (jenisTiket == 2) {
                hargaTiket = 5000000; // Harga VIP BM
            } else if (jenisTiket == 3) {
                hargaTiket = 1000000;  // Harga Tribun BM
            } else {
                cout << "Jenis tiket tidak valid!\n";
                continue;
            }
        } else if (kodeKonser == "BC") {
            if (jenisTiket == 1) {
                hargaTiket = 6000000; // Harga VVIP BC
            } else if (jenisTiket == 2) {
                hargaTiket = 3500000; // Harga VIP BC
            } else if (jenisTiket == 3) {
                hargaTiket = 600000;  // Harga Tribun BC
            } else {
                cout << "Jenis tiket tidak valid!\n";
                continue;
            }
        } else {
            cout << "Kode konser tidak valid!\n";
            continue;
        }

        // Menghitung total harga
        totalHarga = hargaTiket * jumlahBeli;

        // Menghitung potongan (diskon)
        if (jumlahBeli > 5 || totalHarga > 5000000) {
            potongan = totalHarga * 0.1; // Diskon 10%
        }

        // Menghitung total bayar
        totalBayar = totalHarga - potongan;

        // Input uang bayar dan menghitung kembalian
        cout << fixed << setprecision(2); // Format 2 angka di belakang koma
        cout << "\nRincian Pembayaran:\n";
        cout << "---------------------------------\n";
        cout << "Kode Konser        : " << kodeKonser << endl;
        cout << "Jenis Tiket        : " 
             << (jenisTiket == 1 ? "VVIP" : jenisTiket == 2 ? "VIP" : "Tribun") << endl;
        cout << "Jumlah Tiket       : " << jumlahBeli << endl;
        cout << "Harga Satuan       : Rp" << hargaTiket << endl;
        cout << "Total Harga        : Rp" << totalHarga << endl;
        cout << "Potongan           : Rp" << potongan << endl;
        cout << "Total Bayar        : Rp" << totalBayar << endl;

        do {
            cout << "Masukkan Uang Bayar: Rp";
            cin >> uangBayar;

            if (uangBayar < totalBayar) {
                cout << "Uang yang dimasukkan kurang! Silakan masukkan jumlah yang cukup.\n";
            }
        } while (uangBayar < totalBayar);

        uangKembali = uangBayar - totalBayar;

        cout << "Uang Kembali       : Rp" << uangKembali << endl;
        cout << "---------------------------------\n";

        // Menambahkan ke total akumulasi
        grandTotalHarga += totalHarga;
        grandPotongan += potongan;
        grandTotalBayar += totalBayar;
        grandTotalKembalian += uangKembali;

        // Menanyakan apakah ingin input ulang
        cout << "Apakah Anda ingin input ulang? (y/n): ";
        cin >> ulang;

    } while (ulang == 'y' || ulang == 'Y'); // Mengulang jika pengguna memilih 'y' atau 'Y'

    // Menampilkan akumulasi di akhir program
    cout << "\nTotal Akumulasi Pembelian:\n";
    cout << "---------------------------------\n";
    cout << "Nama Pembeli       : " << namaPembeli << endl;
    cout << "Total Harga        : Rp" << grandTotalHarga << endl;
    cout << "Total Potongan     : Rp" << grandPotongan << endl;
    cout << "Total Bayar        : Rp" << grandTotalBayar << endl;
    cout << "Total Kembalian    : Rp" << grandTotalKembalian << endl;
    cout << "---------------------------------\n";

    cout << "Terima kasih telah membeli tiket konser kami!\n";

    return 0;
}
