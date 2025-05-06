#### Module 08: High Level Networking - Advanced Programming
#### Nama : Micheline Wijaya Limbergh
#### NPM : 230627013 

1.What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
Tiga jenis RPC—unary, server streaming, dan bidirectional streaming—berbeda dalam alur komunikasinya. Unary hanya melibatkan satu permintaan dan satu balasan, cocok untuk kebutuhan sederhana seperti mengambil data tunggal. Server streaming memberikan sejumlah data setelah satu permintaan dari klien, ideal untuk pengambilan daftar panjang. Sedangkan bidirectional streaming memungkinkan pertukaran pesan bolak-balik secara simultan, sangat tepat untuk aplikasi interaktif seperti layanan pesan instan.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
Ketika membangun layanan gRPC di Rust, aspek keamanan tidak bisa diabaikan. Sistem harus dapat memverifikasi identitas pengguna (autentikasi), membatasi hak akses mereka (otorisasi), dan menjaga agar data tetap terenkripsi selama transmisi. Misalnya, penggunaan TLS sangat penting untuk mengenkripsi koneksi, dan token berbasis waktu seperti JWT bisa membantu memastikan siapa yang boleh mengakses fungsi tertentu.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
Menyusun komunikasi dua arah secara simultan dalam Rust melalui gRPC bukanlah hal sepele. Kita perlu mengatur alur pesan secara asinkron, yang bisa cukup kompleks terutama dalam aplikasi seperti obrolan langsung. Salah satu tantangannya adalah menjaga konsistensi antar-pesan yang dikirim dan diterima, serta memastikan tidak ada pesan yang hilang ketika koneksi tiba-tiba terputus.

4.What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?
ReceiverStream dari tokio_stream::wrappers cukup berguna saat ingin menyalurkan data secara terus-menerus ke klien dalam layanan gRPC. Keunggulannya adalah fleksibilitas saat menerima dan mengirim aliran data. Namun, jika tidak dikendalikan dengan baik, bisa timbul masalah seperti konsumsi memori berlebih atau antrian data yang terlalu panjang jika klien tidak segera membaca.

5.In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
Agar kode layanan gRPC lebih mudah dikembangkan ke depannya, penting untuk merancang strukturnya dengan prinsip modular. Misalnya, pemisahan antara logika bisnis, definisi protokol, dan implementasi layanan akan memudahkan pengelolaan. Penggunaan trait dan abstraksi juga bisa mempercepat proses refactoring dan menambah fitur baru tanpa mengacaukan kode lama.

6.In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?
Untuk menangani skenario pembayaran yang lebih kompleks di MyPaymentService, diperlukan validasi data secara menyeluruh, koneksi ke pihak ketiga seperti gateway pembayaran, serta pencatatan transaksi untuk keperluan pelaporan. Penanganan kegagalan transaksi, baik karena error sistem maupun masalah eksternal, juga harus disiapkan agar sistem tetap andal.

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
gRPC memiliki dampak besar dalam menyusun sistem terdistribusi karena memungkinkan layanan-layanan berbeda berkomunikasi secara efisien melalui format biner yang ringan. Walau sangat efektif antar backend, ada tantangan saat harus terhubung dengan teknologi non-gRPC, misalnya aplikasi berbasis web murni, yang memerlukan perantara seperti gRPC-Web atau REST gateway.

8.What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
HTTP/2—protokol dasar gRPC—menawarkan kemampuan seperti koneksi paralel dan header yang dikompresi, membuatnya lebih cepat dan efisien dibanding HTTP/1.1. Sementara WebSocket memang bisa digunakan untuk komunikasi dua arah, namun tidak memberikan jaminan struktur dan performa seperti gRPC. Di sisi lain, HTTP/1.1 masih banyak digunakan karena lebih sederhana dan didukung luas, tapi kurang ideal untuk sistem berskala besar yang membutuhkan efisiensi tinggi.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
REST API hanya mengizinkan satu permintaan dan satu tanggapan per interaksi, membuatnya kurang optimal untuk skenario yang butuh komunikasi waktu nyata. Sebaliknya, gRPC dengan kemampuan bidirectional streaming memungkinkan pertukaran data secara langsung dan berkelanjutan, menjadikannya pilihan lebih baik untuk aplikasi yang menuntut kecepatan dan respons cepat antar pengguna.

10.What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
Perbedaan mendasar antara gRPC dan REST terletak pada format datanya. gRPC menggunakan Protocol Buffers yang memiliki struktur baku (schema), sehingga lebih ketat dan konsisten. Sementara REST lebih longgar dengan JSON yang fleksibel tapi rawan kesalahan struktur. Dengan skema yang jelas, gRPC membantu pengembang menjaga integritas data dan mempercepat pengembangan antarlayanan.

