### 🚀 Panduan Instalasi Bot moss

Selamat datang di panduan instalasi bot! Ikuti langkah-langkah di bawah ini untuk memasang dan mengonfigurasi bot dengan benar. Panduan ini dibuat untuk pengguna baru agar mudah dipahami.

📱 **Untuk Pengguna Mobile (Termux):** [Lihat panduan di sini](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## Daftar Isi

1. [Persyaratan Sistem](#persyaratan-sistem)
2. [Instalasi Bot](#instalasi-bot)
3. [Konfigurasi Bot](#konfigurasi-bot)
4. [Menjalankan Bot](#menjalankan-bot)
5. [Memperbarui Bot](#memperbarui-bot)
6. [Kontak & Dukungan](#kontak--dukungan)

---

## Persyaratan Sistem

Sebelum menjalankan bot, pastikan kamu sudah menginstal:

* **Node.js** (Versi: `22.11.0`)
* **npm** (Versi: `10.9.0`)
* **Git**
* **Docker** *(Opsional)*

📥 **Node.js & npm:** [Unduh di sini](https://t.me/KeoAirDropFreeNe/257/1462)
📥 **Git:** [Unduh di sini](https://t.me/KeoAirDropFreeNe/257/60831)

---

## Instalasi Bot

<details>
<summary><strong>🔧 Instal lewat Git</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 Instalasi Manual</strong></summary>

1. Unduh dan ekstrak file bot secara manual.
2. Jalankan perintah `npm install` seperti di atas.

</details>

<details>
<summary><strong>🐳 Instal lewat Docker</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 Di **Windows CMD**, gunakan `%cd%` sebagai pengganti `$(pwd)`

</details>

---

## Konfigurasi Bot

<details open>
<summary><strong>📜 1. <code>configs.json</code> - Konfigurasi Utama</strong></summary>

```json
{
  "proxyMode": "round",
  "rotateProxy": false,
  "skipInvalidProxy": true,
  "proxyRotationInterval": 2,
  "delayEachAccount": [1, 1],
  "timeToRestartAllAccounts": 300,
  "howManyAccountsRunInOneTime": 1,

  "doTasks": true,

  "bindReferralCode": {
    "enabled": true,
    "codes": ["EYG3CP8I"]
  },

  "tradeSettings": {
    "enabled": true,
    "pairs": ["BTC", "ETH", "SOL"],
    "marginAmount": [10, 20],
    "countPerSession": [10, 20],
    "balanceReservePercent": 10,
    "longShortBias": 0.55,
    "maxConcurrentTrades": 1
  },

  "chatWithAi": {
    "enabled": true,
    "amount": [10, 20]
  }
}
```

### 🧩 **Penjelasan Parameter**

| **Nama Parameter**                    | **Tipe**           | **Default**           | **Deskripsi**                                                   |
| ------------------------------------- | ------------------ | --------------------- | --------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | Mengaktifkan rotasi proxy antar akun                            |
| `proxyMode`                           | `string`           | `"round"`             | Mode pembagian proxy — `"static"` atau `"round"`                |
| `skipInvalidProxy`                    | `boolean`          | `true`                | Lewati akun dengan proxy yang tidak valid                       |
| `proxyRotationInterval`               | `number`           | `2`                   | Interval rotasi proxy (dalam menit)                             |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | Rentang waktu tunda acak antar akun (dalam detik)               |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | Waktu (detik) sebelum semua akun diulang kembali                |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | Jumlah akun yang dijalankan secara bersamaan                    |
| `doTasks`                             | `boolean`          | `true`                | Aktifkan tugas otomatis utama                                   |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | Aktifkan pengikatan kode referral otomatis                      |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | Daftar kode referral yang akan digunakan secara acak            |
| `tradeSettings.enabled`               | `boolean`          | `true`                | Aktifkan fitur perdagangan otomatis                             |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | Pasangan token yang akan diperdagangkan                         |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | Margin acak (dalam 💎) untuk setiap perdagangan                 |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | Jumlah perdagangan dalam setiap sesi                            |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | Persentase saldo yang disisakan (tidak digunakan untuk trading) |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | Preferensi posisi LONG/SHORT (0.55 = 55% LONG / 45% SHORT)      |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | Jumlah maksimum transaksi berjalan bersamaan                    |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | Aktifkan fitur obrolan dengan AI                                |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | Jumlah percakapan AI per sesi                                   |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - Data Pengguna</strong></summary>

📥 [Panduan dari Telegram](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - Daftar Proxy</strong></summary>

📥 [Proxy Gratis dari Webshare](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - Daftar Dompet</strong></summary>

📥 [Buat dompet di sini](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## Menjalankan Bot

<details open>
<summary><strong>🪟 Jalankan di Windows (.bat)</strong></summary>

1. Klik dua kali `run.bat`
2. Bot akan otomatis memperbarui, menginstal dependensi, dan mulai berjalan.

> Jika gagal, klik kanan → **Run as Administrator**
> Atau jalankan melalui CMD:

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Jalankan di Linux/macOS (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Jalankan dengan Docker</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> Untuk memulai ulang:

```bash
docker start moss-container
```

</details>

---

## Memperbarui Bot

<details>
<summary><strong>🔄 Jika diinstal lewat Git</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Jika menggunakan Docker</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## Kontak & Dukungan

* **Dukung saya via:** [Ekstensi Chrome](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - Kode Referal: `EYG3CP8I`
* **Donasi:** [Klik di sini](https://t.me/KeoAirDropFreeNe/312/27801)
* **Kontak (Kerja):** [@MeoMunDep](https://t.me/MeoMunDep)
* **Grup Dukungan:** [Gabung di sini](https://t.me/KeoAirDropFreeNe)
* **Channel Update:** [Lihat di sini](https://t.me/KeoAirDropFreeNee)
* **YouTube:** [Tonton di sini](https://www.youtube.com/@keoairdropfreene)
* **Instagram:** [Ikuti](https://www.instagram.com/meomundep)
* **Tiktok:** [Ikuti](https://www.tiktok.com/@meomundep)

---

⚠️ **Disclaimer:** Kode ini disediakan "sebagaimana adanya" tanpa jaminan apa pun. Gunakan dengan risiko sendiri. Dilarang keras menjual atau mendistribusikan ulang kode ini dalam bentuk apa pun.

<p align="center">
  <sub>✨ Dibuat oleh <b>@MeoMunDep</b> | ✨ Terima kasih telah menggunakan bot ini — semoga kamu sukses dan cuan! 🚀</sub>
</p>
