Milestone 1:

Milestone ini membelajari bagaimana membuat single thread web server dan bagaimana implementasi requestnya. Awalnya
cukup straightforward dimana terdapat `TcpListener` yang di bind pada `127.0.0.1:7878` artinya untuk membuka
web yang dibuat kita cukup menulis `127.0.0.1:7878` pada kolom search di browser (atau bisa juga dengan `localhost:7878`). Listener ini diambil setiap ketika kita membuka localhost tersebut sehingga ngeprint 
`Connection established`. 

Kemudian ketika menghandle request dari browser, terbuatlah method `handle_connection()`. Kita bisa lihat didasarkan dari log bahwa method ini melihat kateristik localhost yang kita konek dan ada istilah-istilah seperti `GET`, `Host`, dan lain-lain.