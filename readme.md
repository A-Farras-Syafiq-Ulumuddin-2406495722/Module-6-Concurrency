# Milestone 1

Milestone ini membelajari bagaimana membuat single thread web server dan bagaimana implementasi requestnya. Awalnya
cukup straightforward dimana terdapat `TcpListener` yang di bind pada `127.0.0.1:7878` artinya untuk membuka
web yang dibuat kita cukup menulis `127.0.0.1:7878` pada kolom search di browser (atau bisa juga dengan `localhost:7878`). Listener ini diambil setiap ketika kita membuka localhost tersebut sehingga ngeprint 
`Connection established`. 

Kemudian ketika menghandle request dari browser, terbuatlah method `handle_connection()`. Kita bisa lihat didasarkan dari log bahwa method ini melihat kateristik localhost yang kita konek dan ada istilah-istilah seperti `GET`, `Host`, dan lain-lain. Ketika ini keluar sesuatu di log maka kita mendapat responsenya.

# Milestone 2

![Commit 2 screen capture](/assets/images/commit2.png)

Milestone ini memodifikasi method `handle_connection()` yang paling terlihat yaitu menampilkan file `hello.html` pada web yang dibuka melalui `localhost`. Jadi didalam method ada 3 variabel baru yaitu `status_line`, `content`, dan `length` yang kemudian disatukan menjadi `response`. Lalu setelah itu `stream.write_all(response.as_bytes()).unwrap();` akan melakukan kerjanya.

# Milestone 3

![Commit 3 screen capture](/assets/images/commit3.png)

Pada milestone ini melakukan validasi request dan melakukan pemilihan pada response-nya. Kita bisa dengan menambahkan `if-else` di method `handle_connection()`. Jadi yang di cek yaitu `request_line` apakah mengandung request line dari GET yang mengandung `/` path. Jika iya, maka akan direspon dengan `hello.html` tetapi jika tidak direspon dengan `bad.html` seperti gambar diatas.

![Commit 3 screen capture code before refactor](/assets/images/beforeRefactor.PNG)

Jika dilihat dari kode modifikasi diatas, kita bisa melihat bahwa terdapat kode duplikat. Kita bisa melakukan refactoring dengan melakukan if-else hanya merubah nilai pada `status_line` dan `file_name` seperti kode dibawah.

![Commit 3 screen capture code after refactor](/assets/images/afterRefactor.PNG)

# Milestone 4

Milestone ini melakukan simulasi pada slow request. Jadi caranya yaitu pada kode terdapat `status_line` dan `filename` dimodifikasi yang sebelumnya menggunakan if, sekarang menggunakan match karena ada kasus baru yaitu menambahkan sifat
`sleep` selama 5 detik. Cara menjalankan simulasinya yaitu dengan membuka dua tab `localhost:7878` dan `localhost:7878/sleep`. Ada dua kemungkinan dan salah satunya yaitu ketika menjalankan `localhost:7878` maka hasilnya akan langsung keluar. Kemungkinan lainnya yaitu dengan menjalankan `localhost:7878/sleep` terlebih dahulu yang hasilnya baru keluar setelah 5 detik, tetapi disaat interval 5 detik itu dan menjalankan `localhost:7878` terjadi bahwa hasil berikut tidak langsung selesai dan beliau baru selesai disaat dengan `localhost:7878/sleep` selesai.

# Milestone 5

Pada milestone ini diberikan cara membuat single-thread menjadi multi-thread menggunakan pool thread. Maksud pool thread yaitu membatasi jumlah thread yang dikerjakan secara konkurensi. Milestone ini menggunakan Compile-Driven Development disebabkan cara membuatnya dengan mengecek dengan `cargo check` terus menerus. Sebagai contoh di `main.rs` dimasukkan `Threadpool` tetapi saat di compile terjadi error lalu setelah itu dibuatlah `Threadpool` di dalam `lib.rs`.
Pada tutorial tanpa disadari ini untuk membiasakan pemula pengguna Rust untuk selalu meng-compile, selain itu juga dikasih tau implementasi alternatif untuk multi-thread ini.




