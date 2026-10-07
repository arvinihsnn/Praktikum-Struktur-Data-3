# <h1 align="center">Laporan Praktikum Modul 3 - ABSTRACT DATA TYPE (ADT) </h1>
<p align="center">Arvin Ihsan Fatih - 109082500050</p>

## Dasar Teori
Abstract Data Type (ADT) atau Tipe Data Abstrak, adalah tipe data yang merupakan hasil imajinasi kita dengan memberikan beberapa batasan domain maupun operasinya[1].

### A.  Contoh abstraksi tipe data dengan C sebagai bahasa pemrogramannya.<br/>
Contoh Spesifikasi untuk tipe data abstrak letterstring :
#### 1. Elements : Nilai elemennya adalah karakter ‘a’-’z’,’A’-’Z’, dan termasuk juga spasi. Kita sebut nilai-nilai tersebut sebagai kumpulan karakter (letters).
#### 2. Structure : Terdapat hubungan secara linear di antara elemen letters di dalam suatu string.
#### 3. Domain : letterstring berisi 0 sampai 80 karakter. Domain dari tipe letterstring adalah seluruh kemungkinan nilai yang memenuhi aturan-aturan tersebut[2].

## Guided 

### 1. mahasiswa.h

```C++
#ifndef MAHASISWA_H_INCLUDED
#define MAHASISWA_H_INCLUDED

struct mahasiswa{
    char nim[10];
    int nilai1, nilai2;
};

void inputMhs (mahasiswa &m) ;
float rata2 (mahasiswa m) ;
#endif // MAHASISWA_H_INCLUDED
```
Kode tersebut berfungsi untuk mendefinisikan struktur data mahasiswa dan prototipe fungsi atau prosedur yang digunakan.

### 2. mahasiswa.cpp

```C++
#include <iostream>
#include "mahasiswa.h"

using namespace std;

void inputMhs (mahasiswa &m) {
  cout << "input nim = ";
  cin >> (m).nim;
  cout << "input nilai1 = ";
  cin >> (m).nilai1;
  cout << "input nilai2 = ";
  cin >> (m).nilai2;
}

float rata2(mahasiswa m) {
  return float(m.nilai1 + m.nilai2) / 2;
}
```
Kode tersebut berisi implementasi atau logika pemrograman dari prosedur inputMhs dan fungsi rata2.

### 3. main.cpp

```C++
#include <iostream>
#include "mahasiswa.h"

using namespace std;

int main() 
{
  mahasiswa mhs;
  inputMhs(mhs);
  cout << "rata-rata = " << rata2(mhs);
  return 0;
}
```
Kode tersebut digunakan untuk menjalankan program utama yang memanggil tipe data dan fungsi dari ADT mahasiswa.

## Unguided 

### 1. Buat program yang dapat menyimpan data mahasiswa (max. 10) ke dalam sebuah array dengan field nama, nim, uts, uas, tugas, dan nilai akhir. Nilai akhir diperoleh dari FUNGSI dengan rumus 0.3 * uts+0.4 * uas+0.3 * tugas.

```C++
#include <iostream>
#include <string>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    float uts;
    float uas;
    float tugas;
    float nilaiAkhir;
};

float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return (0.3 * uts) + (0.4 * uas) + (0.3 * tugas);
}

int main() {
    Mahasiswa mhs[10];
    int jumlah;

    cout << "Jumlah mahasiswa (max 10) : ";
    cin >> jumlah;

    if (jumlah > 10) {
        cout << "Maksimal data hanya 10" << endl;
        return 0;
    }

    for (int i = 0; i < jumlah; i++) {
        cout << "\nData Mahasiswa ke-" << i + 1 << endl;
        cout << "Nama        : ";
        cin.ignore();
        getline(cin, mhs[i].nama);
        cout << "NIM         : ";
        cin >> mhs[i].nim;
        cout << "Nilai UTS   : ";
        cin >> mhs[i].uts;
        cout << "Nilai UAS   : ";
        cin >> mhs[i].uas;
        cout << "Nilai Tugas : ";
        cin >> mhs[i].tugas;

        mhs[i].nilaiAkhir = hitungNilaiAkhir(mhs[i].uts, mhs[i].uas, mhs[i].tugas);
    }

    for (int i = 0; i < jumlah; i++) {
        cout << "\nMahasiswa ke-" << i + 1 << endl;
        cout << "Nama        : " << mhs[i].nama << endl;
        cout << "NIM         : " << mhs[i].nim << endl;
        cout << "Nilai UTS   : " << mhs[i].uts << endl;
        cout << "Nilai UAS   : " << mhs[i].uas << endl;
        cout << "Nilai Tugas : " << mhs[i].tugas << endl;
        cout << "Nilai Akhir : " << mhs[i].nilaiAkhir << endl;
    }

    return 0;
}
```
### Output Unguided 1 :
Jumlah mahasiswa (max 10) : 2

Data Mahasiswa ke-1
Nama        : Beni
NIM         : 109082566699
Nilai UTS   : 85
Nilai UAS   : 92
Nilai Tugas : 95

Data Mahasiswa ke-2
Nama        : Edo
NIM         : 109082599966
Nilai UTS   : 70
Nilai UAS   : 98
Nilai Tugas : 90

Mahasiswa ke-1
Nama        : Beni
NIM         : 109082566699
Nilai UTS   : 85
Nilai UAS   : 92
Nilai Tugas : 95
Nilai Akhir : 90.8

Mahasiswa ke-2
Nama        : Edo
NIM         : 109082599966
Nilai UTS   : 70
Nilai UAS   : 98
Nilai Tugas : 90
Nilai Akhir : 87.2

##### Output 1
![Screenshot Output Unguided 1_1](https://github.com/arvinihsnn/Praktikum-Struktur-Data-3/blob/main/Output-Unguided/Ouptut-Unguided-1.png)

Program ini menyimpan data beberapa mahasiswa menggunakan array dari struct Mahasiswa. Fungsi hitungNilaiAkhir() menerima parameter nilai UTS, UAS, dan tugas, lalu mengembalikan hasil perhitungan bobot nilai. Hasil perhitungan tersebut kemudian disimpan ke dalam atribut nilaiAkhir dari masing-masing elemen array.

### 2. Buatlah ADT pelajaran yang dipisah menjadi berkas pelajaran.h, pelajaran.cpp, dan main.cpp sesuai spesifikasi soal.

A. pelajaran.h
```C++
#ifndef PELAJARAN_H
#define PELAJARAN_H

#include <string>
using namespace std;

struct pelajaran {
    string namamapel;
    string kodemapel;
};

pelajaran create_pelajaran(string namapel, string kodepel);
void tampil_pelajaran(pelajaran pel);

#endif // PELAJARAN_H
```

B. pelajaran.cpp
```C++
#include <iostream>
#include "pelajaran.h"

using namespace std;

pelajaran create_pelajaran(string namapel, string kodepel) {
    pelajaran pel;
    pel.namamapel = namapel;
    pel.kodemapel = kodepel;
    return pel;
}

void tampil_pelajaran(pelajaran pel) {
    cout << "nama pelajaran : " << pel.namamapel << endl;
    cout << "nilai : " << pel.kodemapel << endl;
}
```

C. main.cpp
```C++
#include <iostream>
#include "pelajaran.h"

using namespace std;

int main() {
    string namapel = "Struktur Data";
    string kodepel = "STD";
    pelajaran pel = create_pelajaran(namapel, kodepel);
    tampil_pelajaran(pel);
    return 0;
}
```

### Output Unguided 2 :
nama pelajaran : Struktur Data
nilai : STD

##### Output 1
![Screenshot Output Unguided 2_1](https://github.com/arvinihsnn/Praktikum-Struktur-Data-3/blob/main/Output-Unguided/Output-Unguided-2.png)

Program ini mengimplementasikan ADT pelajaran secara utuh. File pelajaran.h mendefinisikan struct dan prototipe fungsi, file pelajaran.cpp merealisasikan pembuat objek pelajaran (create_pelajaran) dan prosedur pencetak (tampil_pelajaran), sedangkan main.cpp berfungsi sebagai penguji output.

### 3. Buatlah program dengan ketentuan : - 2 buah array 2D integer berukuran 3x3 dan 2 buah pointer integer. - fungsi/prosedur yang menampilkan isi sebuah array integer 2D. - fungsi/prosedur yang akan menukarkan isi dari 2 array integer 2D pada posisi tertentu. - fungsi/prosedur yang akan menukarkan isi dari variabel yang ditunjuk oleh 2 buah pointer.

```C++
#include <iostream>
using namespace std;

void tampilArray2D(int arr[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << arr[i][j] << "\t";
        }
        cout << endl;
    }
}

void tukarArray2D(int arr1[3][3], int arr2[3][3], int baris, int kolom) {
    int temp = arr1[baris][kolom];
    arr1[baris][kolom] = arr2[baris][kolom];
    arr2[baris][kolom] = temp;
}

void tukarPointer(int *p1, int *p2) {
    int temp = *p1;
    *p1 = *p2;
    *p2 = temp;
}

int main() {
    int arr1[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int arr2[3][3] = {
        {9, 8, 7},
        {6, 5, 4},
        {3, 2, 1}
    };

    cout << "Array 1 Awal :" << endl;
    tampilArray2D(arr1);
    cout << "\nArray 2 Awal :" << endl;
    tampilArray2D(arr2);

    tukarArray2D(arr1, arr2, 0, 0);
    cout << "\nSetelah ditukar :" << endl;
    cout << "Array 1 :" << endl;
    tampilArray2D(arr1);
    cout << "Array 2 :" << endl;
    tampilArray2D(arr2);

    int a = 100, b = 200;
    int *ptr1 = &a;
    int *ptr2 = &b;

    cout << "\nDitukar dengan Pointer :" << endl;
    cout << "Sebelum ditukar : a = " << *ptr1 << ", b = " << *ptr2 << endl;
    tukarPointer(ptr1, ptr2);
    cout << "Setelah ditukar : a = " << *ptr1 << ", b = " << *ptr2 << endl;

    return 0;
}
```
### Output Unguided 3 :
Array 1 Awal :
1       2       3
4       5       6
7       8       9

Array 2 Awal :
9       8       7
6       5       4
3       2       1

Setelah ditukar :
Array 1 :
9       2       3
4       5       6
7       8       9
Array 2 :
1       8       7
6       5       4
3       2       1

Ditukar dengan Pointer :
Sebelum ditukar : a = 100, b = 200
Setelah ditukar : a = 200, b = 100

##### Output 1
![Screenshot Output Unguided 3_1](https://github.com/arvinihsnn/Praktikum-Struktur-Data-3/blob/main/Output-Unguided/Output-Unguided-3.png)

Program ini mendemonstrasikan manipulasi matriks 2D $3 \times 3$ dan penggunaan pointer. Prosedur tampilArray2D mencetak matriks, tukarArray2D menukarkan isi dua matriks pada koordinat indeks tertentu, dan tukarPointer menukarkan nilai dua variabel lewat alamat memori yang ditunjuk oleh pointer.

## Kesimpulan
Praktikum Modul 3 ini memberikan saya pemahaman mengenai konsep Abstract Data Type (ADT) dan penerapannya dalam C++. Dengan memisahkan program menjadi file header (.h), (.cpp), dan (main.cpp), struktur program menjadi lebih rapi, dan terorganisir.

## Referensi
<br>[1] Choirul Huda, S.Kom., M.M.. (2017). Tipe Data. Malang: BINUS UNIVERSITY MALANG. Diakses pada 7 Oktober 2026 melalui https://binus.ac.id/malang/2017/09/tipe-data/
<br>[2] Choirul Huda, S.Kom., M.M.. (2017). Tipe Data Abstrak. Malang: BINUS UNIVERSITY MALANG. Diakses pada 7 Oktober 2026 melalui https://binus.ac.id/malang/2017/09/tipe-data-abstrak/