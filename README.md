# Super Cashier
Super Cashier adalah program berbasis python yang dirancang agar seorang pelanggan dapat memasukkan sendiri item serta jumlah dan harga item ke dalam daftar pesanan yang kemudian akan disimpan di dalam SQLite database.

# Background
Andaikan seorang pemilik supermarket besar di salah satu kota di Indonesia memiliki rencana untuk melakukan perbaikan proses bisnis, yaitu membuat sistem kasir self-service dengan harapan:
- Pelanggan bisa langsung memasukkan item, jumlah item, dan harga item yang dibeli serta beberapa fitur lain.
- Pelanggan yang tidak berada di kota tersebut bisa membeli barang dari supermarket tersebut.

# Requirements
Beberapa fitur program yang dibutuhkan pada Super Cashier antara lain:
1. Pelanggan dapat memasukkan nama, jumlah, dan harga item ke dalam daftar pesanan
2. Pelanggan dapat memperbarui nama, jumlah, dan harga item yang telah dimasukkan sebelumnya
3. Pelanggan dapat menghapus salah satu atau seluruh item dari daftar pesanan
4. Pelanggan dapat memeriksa ulang daftar pesanan yang telah dibuat
5. Pelanggan dapat menerima diskon jika memenuhi syarat pembelian
6. Pelanggan dapat melihat total pembayaran dari keseluruhan transaksi

# Alur Program
![A flowchart image that explains how the program runs](https://lh3.googleusercontent.com/pw/AJFCJaXPrGmCn_n0w9pvshdnaMMgzsLxWApr7Vks2uZvyklySxjuy6bfPfGl46TZX1F52c5l67OTG55RJnXpoJXz1p-u5D2V0pVQJFIwgyvMmTO-a0zdKTWYZ4URSm31zEduQdhBjVKU1qggYrT-eehMtWs79c9pfShqSxYVCCD4drhF3COfcoZEje4tsmpkOYxgu1ikT3mXYDbL89-PiNOb3ypIo0UHzvB8UCXcpBj7iu7hHJ90OL2AlVBCwrvYOV_AUZd8Xt6Sbc21J-8J-cI3VhgPXgvRNkMxzvR9WeDRMs2XHl3jyIYGHnU6neATdLx6c5dXeWg0iNpdwo7-2WEPEYDuCe7pRAXeGBlN2MQaJ5j1txE_piP7D1__1ynKCkBcHAIyZdOLpu8rf0qjP8VG0gHbTlnMV59Tdm-DR9hWCBivI6FrpjPM6nOf4APKpAiEzbKL9iy1Ti8Rk-LE5dV-JTFdM5BI7JooXN6bxf5f4x_DyMoaBySSw2qLmqp7tJ_bJjrHrdVS4H0nHNgIe-vqTUT274p8dYO2EhVlEVBHB-BXWpYMOJGNjPu7wpwDFFfArlAYaQaTPOClpymQeeDQBfkAbzyKyZj-kU9gsKjQ_4gjGUytLiBw6Si6u89UrTclMWDwrkK8iYLh8sOGiDoqZ0bbTNMmmDTMt6NQpfRHAvKiLEZY_KkNt28gHWp_b401-gz0Jf6VSZhu1rhMJsYOOPkMFrMzEVzS3Tzn5N0MgQ2Xe2QJJh5yPXaUMKQNS8RPtdTY0q6VxuRKc9bUPNlf3K1cMLHwIf2L-oSPqFmLnLZledNBnm2cNEaYIZKpXYiwg6bGi7NbhwJxfy9ZfJ-ei4zF_aFsQWGa-otTuvnQVl90QNQVWgA-LPxltaTcgsuCWqZk632xs7aP_75jnPI98g=w1920-h713-s-no?authuser=0)
**START**
1. Pelanggan akan diminta memasukkan nama item, jumlah item, dan harga item secara berurutan melalui fungsi *input_item()*. *input_item()* akan memastikan apakah pelanggan masih ingin menambah pesanan. Jika ya, pelanggan akan diminta untuk memasukkan nama, jumlah, dan harga item berikutnya. Jika pelanggan sudah selesai memasukkan item, *input_item()* akan berhenti bekerja dan mengembalikan nilai nama, jumlah, dan harga item dalam bentuk **list**.
2. List nama, jumlah, dan harga item akan masuk ke dalam fungsi *add_item()* yang akan memasangkan item dan detail item ke dalam dictionary **order_items**.
3. Jika pelanggan ingin mengubah data di dalam pesanan, pelanggan bisa menggunakan fitur **update**. Terdapat tiga fitur update:
    - update nama item: fungsi *input_update_name()* akan berjalan dan pelanggan akan diminta memasukkan nama item sebelumnya dan nama item yang akan menggantikan. Fungsi *update_item_name()* akan mengganti nama item di dalam **order_items** sesuai input dari pelanggan.
    - update jumlah item: fungsi *input_update_qty()* akan berjalan dan pelanggan akan diminta memasukkan nama item yang jumlahnya ingin diganti dan jumlah item yang baru. Fungsi *update_item_qty()* akan mengganti jumlah item di dalam **order_items** sesuai input dari pelanggan.
    - update harga item: fungsi *input_update_price()* akan berjalan dan pelanggan akan diminta memasukkan nama item yang harganya ingin diganti dan harga item yang baru. Fungsi *update_item_price()* akan mengganti harga item di dalam **order_items** sesuai input dari pelanggan.
4. Jika pelanggan ingin menghapus data di dalam pesanan, pelanggan bisa menggunakan fitur **delete**. Terdapat dua fitur delete:
    - hapus per item: fungsi *input_delete* akan berjalan dan pelanggan akan diminta memasukkan nama item yang ingin dihapus. Fungsi *delete_item()* akan menghapus item di dalam **order_items** sesuai input dari pelanggan.
    - hapus seluruh item: fungsi *reset_transaction()* akan berjalan dan menghapus seluruh isi **order_items**. Pelanggan dapat menambahkan item kembali melalui fungsi *input_item()*.
5. Pelanggan dapat melakukan pengecekan terhadap item yang telah dipesan melalui fungsi *check_order()* yang akan memastikan tidak adanya kesalahan input. Jika ada, pesan kesalahan ditampilkan dan pelanggan diarahkan kembali menuju *input_item()*. Jika tidak ada, data pesanan akan ditampilkan dalam **table_items** yang berisi kolom:
    - No.
    - Nama item
    - Jumlah item
    - Harga per item
    - Total harga
6. Jika pelanggan tidak menemukan kesalahan dalam daftar pesanan, pelanggan dapat melakukan check out melalui fungsi *check_out()*. *check_out()* akan menampilkan data pesanan dan pelanggan akan menerima diskon:
    - 5% jika total harga lebih dari 200.000,
    - 6% jika total harga lebih dari 300.000,
    - 7% jika total harga lebih dari 500.000.
    Data pesanan akan menampilkan **table_items** yang telah ditambahkan kolom:
    - Diskon
    - Harga setelah diskon
    serta akan menampilkan total pembayaran dari seluruh item. 
    Terakhir, *check_out* akan memanggil fungsi *insert_to_table()* untuk memasukkan data ke dalam database.
**END** 

# Penjelasan Code

# Hasil Test Case
1. Pelanggan ingin menambahkan dua item baru. Item yang ditambahkan adalah sebagai berikut:
- Nama Item: Ayam Goreng, Qty: 2, Harga: 20000
- Nama Item: Pasta Gigi, Qty: 3, Harga: 15000

2. Ternyata pelanggan salah memasukkan salah satu item dari belanjaan, maka pelanggan ingin menghapusnya. Item yang ingin dihapuskan adalah Pasta Gigi.

3. Ternyata pelanggan salah memasukkan item yang ingin dibelanjakan! Daripada menghapus satu - satu, maka pelanggan ini menghapus semua item yang sudah ditambahkan.

4. Setelah pelanggan selesai menambahkan item, ia ingin menghitung total belanja yang harus dibayarkan serta melihat item - item yang dibeli.
