Game Batu Gunting Kertas (Multiplayer dengan Thread & Shared Memory)

Proyek ini adalah permainan Batu–Gunting–Kertas dimana dua pemain yang berjalan secara bersamaan menggunakan multithreading, shared memory, dan message queue di bahasa C. 

Fitur
- 2 pemain bermain secara bersamaan
- Thread digunakan untuk pemain dan wasit
- Shared memory (IPC) untuk berbagi data antara proses
- Message queue untuk komunikasi antar pemain
- Pemain bisa bermain hingga 3 ronde
- Skor akan diakumulasi dan ditampilkan

Teknologi yang Digunakan
- Bahasa C
- POSIX Threads (pthread)
- Shared Memory (shmget, shmat, shmdt)
- Message Queue (msgget, msgsnd)
- Linux System Calls (unistd.h, sys/ipc.h, dll)

Cara Kompilasi & Menjalankan
Kompilasi
gcc main.c -o bgt -lpthread

Jalankan
./bgt

Aturan Permainan
- Pemain akan diminta memilih:
  1: Batu
  2: Kertas
  3: Gunting
  0: Keluar

- Hasil akan dihitung oleh wasit berdasarkan aturan:
  - Batu vs Gunting → Batu menang
  - Kertas vs Batu → Kertas menang
  - Gunting vs Kertas → Gunting menang
  - Jika sama → Seri

- Skor akan ditampilkan setelah setiap ronde

Fitur Sistem

- Mutex (pthread_mutex_t) untuk menjaga sinkronisasi
- Setiap pemain berjalan di thread terpisah
- Wasit membaca hasil dan mencetak skor
- Shared memory menyimpan pilihan pemain
- Message queue untuk sinkronisasi pengiriman

Contoh Output
Pemain 1, masukkan pilihan (1: Batu, 2: Kertas, 3: Gunting, 0: Keluar): 1
Pemain 2, masukkan pilihan (1: Batu, 2: Kertas, 3: Gunting, 0: Keluar): 2
Pemain 1 memilih: 1
Pemain 2 memilih: 2
Hasil: Pemain 2 menang!
Skor: Pemain 1 - 0, Pemain 2 - 1

Catatan

- Program ini hanya berjalan di Linux (karena menggunakan header <unistd.h> dan IPC System V)
- Harus dijalankan di terminal (bukan GUI IDE)
- Jika stuck: gunakan ipcs -m dan ipcrm -m [id] untuk menghapus shared memory
