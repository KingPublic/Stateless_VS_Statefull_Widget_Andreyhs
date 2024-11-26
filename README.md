Berikut adalah contoh file `README.md` yang menjelaskan cara kerja manajemen state menggunakan **StatelessWidget** dan **StatefulWidget** serta skenario penggunaannya:

```markdown
# Codelabs: Stateful & Stateless Widgets

## Tujuan
Pada codelab ini, kita akan membangun dua versi aplikasi: satu menggunakan **StatelessWidget** dan yang lainnya menggunakan **StatefulWidget**. Anda akan mempelajari bagaimana manajemen state bekerja berbeda pada kedua pendekatan ini.

## Langkah 1: Setup Proyek Flutter
Untuk memulai, buatlah proyek Flutter baru menggunakan lingkungan pengembangan pilihan Anda (misalnya Android Studio, VSCode, atau command line). Nama proyek ini adalah `state_management_codelab`.

## Langkah 2: Membuat Aplikasi Counter dengan StatelessWidget
Pada langkah pertama, kita akan membuat aplikasi counter sederhana menggunakan **StatelessWidget**.

1. Buka file `lib/main.dart` dan ganti kode yang ada dengan kode berikut:
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyStatelessApp());
}

class MyStatelessApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Stateless Counter App')),
        body: CounterWidget(),
      ),
    );
  }
}

class CounterWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          Text('Counter Value: 0'),
          SizedBox(height: 10),
          ElevatedButton(
            onPressed: () {
              // TODO: Increment counter
            },
            child: Text('Increment'),
          ),
        ],
      ),
    );
  }
}
```

Pada contoh ini, kita menggunakan **StatelessWidget** untuk aplikasi counter. **StatelessWidget** tidak memiliki state yang dapat berubah setelah widget dibuat. Oleh karena itu, meskipun tombol ditekan, nilai counter tidak akan berubah karena tidak ada pengelolaan state di sini.

## Langkah 3: Membuat Aplikasi Counter dengan StatefulWidget
Pada langkah kedua, kita akan membuat aplikasi counter yang mirip, tetapi kali ini menggunakan **StatefulWidget**.

1. Modifikasi file `lib/main.dart` untuk menyertakan versi **StatefulWidget**:
```dart
class MyStatefulWidgetApp extends StatefulWidget {
  @override
  _MyStatefulWidgetAppState createState() => _MyStatefulWidgetAppState();
}

class _MyStatefulWidgetAppState extends State<MyStatefulWidgetApp> {
  int counter = 0;

  void incrementCounter() {
    setState(() {
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Stateful Counter App')),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text('Counter Value: $counter'),
              SizedBox(height: 10),
              ElevatedButton(
                onPressed: incrementCounter,
                child: Text('Increment'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

void main() {
  runApp(MyStatelessApp());
  // Uncomment the following line to run the StatefulWidget version:
  // runApp(MyStatefulWidgetApp());
}
```

Pada kode ini, kita membuat aplikasi menggunakan **StatefulWidget** dengan sebuah variabel `counter` yang dapat berubah nilainya ketika tombol ditekan. Dengan menggunakan **setState**, kita memperbarui nilai counter dan merender ulang tampilan widget.

## Langkah 4: Menjalankan Aplikasi
1. Buka terminal dan arahkan ke direktori proyek Anda.
2. Jalankan aplikasi menggunakan perintah berikut:
   ```bash
   flutter run
   ```
3. Secara default, aplikasi akan menjalankan versi **StatelessCounter**. Untuk beralih ke **StatefulCounter**, komentar baris `runApp(MyStatelessApp());` dan aktifkan baris `runApp(MyStatefulWidgetApp());`.

## Langkah 5: Observasi
Setelah menjalankan kedua versi aplikasi (Stateless dan Stateful), perhatikan bagaimana perilaku counter di masing-masing versi saat tombol "Increment" ditekan.
- **StatelessWidget**: Tidak ada perubahan pada counter, karena nilai counter tidak dapat dikelola secara dinamis di dalam widget ini.
- **StatefulWidget**: Nilai counter berubah ketika tombol "Increment" ditekan, berkat penggunaan metode `setState` yang mengubah state dan memperbarui tampilan UI.

## Pembahasan: Perbedaan Manajemen State

### 1. **StatelessWidget**
- **State tidak dapat berubah** setelah widget dibuat.
- Biasanya digunakan ketika widget hanya perlu menampilkan data yang tidak berubah atau tidak memerlukan interaksi dinamis.
- **Contoh Penggunaan**: Widget statis yang hanya menampilkan teks atau gambar tanpa interaksi.

### 2. **StatefulWidget**
- **State dapat berubah** dan mengubah tampilan widget secara dinamis.
- Cocok untuk widget yang memiliki interaksi atau data yang perlu diperbarui seiring waktu (misalnya, form input, counter, atau aplikasi yang membutuhkan pembaruan UI secara real-time).
- **Contoh Penggunaan**: Aplikasi dengan form input, penghitungan dinamis (seperti aplikasi kalkulator), atau aplikasi dengan data yang sering berubah.

## Kapan Menggunakan StatelessWidget dan StatefulWidget?
- **StatelessWidget** cocok untuk tampilan UI yang tidak bergantung pada perubahan data secara dinamis. Jika widget hanya menampilkan informasi statis, **StatelessWidget** adalah pilihan yang tepat.
- **StatefulWidget** digunakan ketika UI bergantung pada data yang berubah selama eksekusi aplikasi, seperti tombol yang bisa ditekan atau formulir yang membutuhkan input dari pengguna.

```
Dengan `README.md` ini, saya memberikan penjelasan yang jelas mengenai perbedaan antara **StatelessWidget** dan **StatefulWidget**, serta kapan harus memilih salah satu dari keduanya berdasarkan kebutuhan aplikasi Flutter kalian.
