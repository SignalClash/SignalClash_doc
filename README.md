# ⚔️ SignalClash

SignalClash adalah **game battle berbasis prediksi harga** di blockchain **Sui**, menggunakan **oracle Pyth Network** sebagai sumber data harga real-time dan terpercaya. Pemain bertarung dengan memilih **coin** dan posisi **UP / DOWN** dalam durasi waktu tertentu untuk memenangkan **Battle Coin**.

---

## 🚀 Konsep Utama

SignalClash menggabungkan:

* **On-chain battle** (fair & transparan)
* **Oracle Pyth** untuk data harga real-time
* **Time-based prediction** (open → close)
* **Reward berbasis coin Sui**

Cocok untuk:

* GameFi
* Prediction market
* Edukasi Web3 & DeFi

---

## 🪙 Battle Coin

Battle Coin adalah coin utama dalam ekosistem SignalClash.

Fungsi:

* Biaya masuk battle
* Reward kemenangan
* Insentif partisipasi

Coin ini dibuat sebagai **Custom Coin Sui** menggunakan `TreasuryCap`.

---

## 🔮 Oracle: Pyth Network

SignalClash menggunakan **Pyth Network** sebagai oracle harga.

### Alasan menggunakan Pyth

* Harga real-time
* Low latency
* Banyak asset (Crypto, Forex, Commodities)
* Sudah terintegrasi dengan Sui

### Contoh Pair yang Didukung

* BTC / USD
* ETH / USD
* SOL / USD
* SUI / USD

Harga **OPEN** dan **CLOSE** diambil langsung dari Pyth on-chain feed.

---

## ⏱️ Durasi Battle

Setiap battle memiliki dua fase utama:

### 1️⃣ Open Phase

* Durasi: **5 menit**
* Pemain dapat:

  * Join battle
  * Memilih coin dan posisi (UP / DOWN)
  * Mengunci Battle Coin

Jika fase ini berakhir:

* Tidak ada pemain baru yang bisa masuk

### 2️⃣ Close Phase

* Durasi: **5 menit**
* Sistem akan:

  * Mengambil harga **OPEN** dari oracle
  * Menunggu hingga waktu close
  * Mengambil harga **CLOSE** dari oracle

### Total Durasi Battle

> ⏱️ **10 menit per battle**

---

## 🧠 Mekanisme Penentuan Pemenang

Pemenang battle ditentukan berdasarkan **signal perubahan harga masing-masing coin**:

1. Ambil persentase perubahan harga (OPEN → CLOSE) untuk setiap coin.
2. Bandingkan persentase kenaikan tiap coin.
3. Coin dengan persentase kenaikan **tertinggi** adalah pemenangnya.

### Contoh:

* Coin SOL: +17%
* Coin SUI: +1%

**SOL menang**, karena kenaikan persentasenya lebih tinggi.

Jika terjadi **tie**, reward dibagi rata.

---

## 🏆 Distribusi Reward

* Total pool = seluruh Battle Coin peserta
* Sistem:

  * Mengambil fee protocol (opsional)
  * Sisanya dibagi ke pemenang sesuai coin yang menang

Jika tie:

* Semua pemain mendapat refund

---

## 🏗️ Arsitektur Smart Contract (Sui Move)

### Module Utama

* `signalclash::battle`
* `signalclash::coin`
* `signalclash::oracle`

### Struktur Battle (Contoh)

```move
struct Battle has key {
    id: UID,
    assets: vector<vector<u8>>,  // list of coins yang dipertandingkan
    open_prices: vector<u64>,
    close_prices: vector<u64>,
    open_time: u64,
    close_time: u64,
    is_closed: bool
}
```

---

## 🔐 Keamanan & Fairness

* Harga berasal dari **oracle Pyth** (bukan input admin)
* Logic sepenuhnya on-chain
* Tidak bisa mengubah hasil setelah battle dimulai

---

## 🖥️ Frontend Flow

1. User pilih coin
2. Join battle
3. Pilih UP / DOWN
4. Tunggu hasil
5. Klaim reward

---

## 🛠️ Tech Stack

* **Blockchain**: Sui
* **Smart Contract**: Move
* **Oracle**: Pyth Network
* **Frontend**: React + Sui Wallet Adapter
* **Backend (opsional)**: Indexer / API

---

## 📌 Roadmap

* [ ] Multi-asset battle
* [ ] Variable duration battle
* [ ] NFT badge untuk winner
* [ ] Leaderboard
* [ ] DAO governance

---

## 📄 Lisensi

MIT License

---

## ✨ Penutup

SignalClash bukan sekadar game, tapi **arena strategi & sinyal harga** di Web3.

> *"Read the signal. Win the clash."* ⚔️📈
