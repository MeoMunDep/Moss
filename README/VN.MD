### 🚀 Hướng Dẫn Cài Đặt Bot moss

Chào mừng bạn đến với hướng dẫn cài đặt bot! Hãy làm theo các bước dưới đây để cài đặt và cấu hình bot đúng cách. Hướng dẫn này được viết dành cho người mới, dễ hiểu và chi tiết cho từng bước.

📱 **Dành cho người dùng Mobile (Termux):** [Xem hướng dẫn tại đây](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## Mục Lục

1. [Yêu Cầu Hệ Thống](#yêu-cầu-hệ-thống)
2. [Cài Đặt Bot](#cài-đặt-bot)
3. [Cấu Hình Bot](#cấu-hình-bot)
4. [Chạy Bot](#chạy-bot)
5. [Cập Nhật Bot](#cập-nhật-bot)
6. [Liên Hệ & Hỗ Trợ](#liên-hệ--hỗ-trợ)

---

## Yêu Cầu Hệ Thống

Trước khi chạy bot, hãy đảm bảo bạn đã cài đặt:

* **Node.js** (Phiên bản: `22.11.0`)
* **npm** (Phiên bản: `10.9.0`)
* **Git**
* **Docker** *(Không bắt buộc)*

📥 **Node.js & npm:** [Tải tại đây](https://t.me/KeoAirDropFreeNe/257/1462)

📥 **Git:** [Tải tại đây](https://t.me/KeoAirDropFreeNe/257/60831)

---

## Cài Đặt Bot

<details>
<summary><strong>🔧 Cài Đặt Qua Git</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 Cài Đặt Thủ Công</strong></summary>

1. Tải xuống và giải nén bot thủ công.
2. Chạy lại lệnh `npm install` giống như ở trên.

</details>

<details>
<summary><strong>🐳 Cài Đặt Bằng Docker</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 Trên **Windows CMD**, sử dụng `%cd%` thay vì `$(pwd)`

</details>

---

## Cấu Hình Bot

<details open>
<summary><strong>📜 1. <code>configs.json</code> - Cấu Hình Chính</strong></summary>

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

### 🧩 **Giải Thích Cấu Hình**

| **Tên Tham Số**                       | **Kiểu**           | **Mặc Định**          | **Mô Tả**                                                         |
| ------------------------------------- | ------------------ | --------------------- | ----------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | Bật/tắt việc xoay proxy giữa các tài khoản                        |
| `proxyMode`                           | `string`           | `"round"`             | Kiểu phân phối proxy: `"static"` hoặc `"round"`                   |
| `skipInvalidProxy`                    | `boolean`          | `true`                | Bỏ qua tài khoản nếu proxy không hợp lệ                           |
| `proxyRotationInterval`               | `number`           | `2`                   | Thời gian (phút) giữa các lần xoay proxy                          |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | Độ trễ ngẫu nhiên (giây) giữa các tài khoản                       |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | Thời gian (giây) để khởi động lại toàn bộ tài khoản               |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | Số lượng tài khoản chạy song song cùng lúc                        |
| `doTasks`                             | `boolean`          | `true`                | Thực hiện nhiệm vụ tự động                                        |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | Bật chế độ nhập mã giới thiệu tự động                             |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | Danh sách mã giới thiệu (chọn ngẫu nhiên khi chạy)                |
| `tradeSettings.enabled`               | `boolean`          | `true`                | Bật chế độ giao dịch tự động                                      |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | Các cặp token giao dịch                                           |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | Số lượng margin (💎) mỗi giao dịch                                |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | Số giao dịch thực hiện trong một phiên                            |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | Tỷ lệ phần trăm số dư được giữ làm dự phòng (không dùng để trade) |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | Tỷ lệ xác suất thiên về LONG (0.55 = 55% LONG / 45% SHORT)        |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | Số giao dịch có thể mở cùng lúc tối đa                            |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | Bật nhiệm vụ trò chuyện AI tự động                                |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | Số lần trò chuyện AI mỗi phiên                                    |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - Dữ Liệu Người Dùng</strong></summary>

📥 [Xem hướng dẫn từ Telegram](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - Danh Sách Proxy</strong></summary>

📥 [Proxy miễn phí từ Webshare](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - Danh Sách Ví</strong></summary>

📥 [Tạo ví tại đây](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## Chạy Bot

<details open>
<summary><strong>🪟 Chạy Trên Windows (.bat)</strong></summary>

1. Nhấn đúp vào `run.bat`
2. Bot sẽ tự động cập nhật, cài đặt và chạy.

> Nếu gặp lỗi: Nhấn chuột phải → **Run as Administrator**
> Hoặc chạy bằng CMD:

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Chạy Trên Linux/macOS (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Chạy Bằng Docker</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> Khi cần khởi động lại:

```bash
docker start moss-container
```

</details>

---

## Cập Nhật Bot

<details>
<summary><strong>🔄 Nếu Cài Qua Git</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Nếu Sử Dụng Docker</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## Liên Hệ & Hỗ Trợ

* **Ủng hộ mình qua** [Liên kết mở rộng](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - Mã giới thiệu: `EYG3CP8I`
* **Donate:** [Tại đây](https://t.me/KeoAirDropFreeNe/312/27801)
* **Liên hệ công việc:** [@MeoMunDep](https://t.me/MeoMunDep)
* **Nhóm hỗ trợ:** [Tham gia tại đây](https://t.me/KeoAirDropFreeNe)
* **Kênh cập nhật:** [Xem tại đây](https://t.me/KeoAirDropFreeNee)
* **YouTube:** [Xem tại đây](https://www.youtube.com/@keoairdropfreene)
* **Instagram:** [Theo dõi](https://www.instagram.com/meomundep)
* **Tiktok:** [Theo dõi](https://www.tiktok.com/@meomundep)

---

⚠️ **Lưu ý**: Mã nguồn được cung cấp “nguyên trạng” và không có bất kỳ bảo đảm nào. Hãy sử dụng với trách nhiệm của riêng bạn. Việc chia sẻ hoặc bán lại mã nguồn dưới mọi hình thức đều bị nghiêm cấm.

<p align="center">
  <sub>✨ Được tạo bởi <b>@MeoMunDep</b> | ✨ Cảm ơn bạn đã sử dụng bot, chúc bạn kiếm được thật nhiều! 🚀</sub>
</p>
