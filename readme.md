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

Jika dilihat dari kode modifikasi diatas, kita bisa melihat bahwa terdapat kode duplikat. Kita bisa melakukan refactoring dengan melakukan if-else pada `status_line` dan `file_name` seperti kode dibawah.

![Commit 3 screen capture code after refactor](/assets/images/afterRefactor.PNG)







