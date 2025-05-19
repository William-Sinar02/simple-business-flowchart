# simple-business-flowchart
graph TD
    A[Start: Pengguna Membuka Aplikasi] --> B[Pengguna Berinteraksi misalnya Klik Beli Produk]
    B --> C{Frontend: Kumpulkan Data}
    C --> D[Kirim HTTP Request POST /api/purchase]
    
    D --> E{Backend: Terima Permintaan}
    E --> F[Validasi Data misalnya Token, Input]
    F -->|Valid| G[Proses Bisnis misalnya Cek Stok, Proses Pembayaran]
    F -->|Tidak Valid| H[Kembalikan Error ke Frontend]
    
    G --> I[Simpan Data Transaksi ke Database]
    G --> J[Catat Log Aktivitas ke Sistem Logging]
    I --> K[Kembalikan Respons Sukses misalnya JSON]
    J --> K
    
    K --> L{Frontend: Terima Respons}
    L -->|Sukses| M[Tampilkan Hasil misalnya Pembelian Berhasil]
    L -->|Error| N[Tampilkan Pesan Error]
    
    M --> O[End: Pengguna Lanjutkan Interaksi]
    N --> O
    H --> L
