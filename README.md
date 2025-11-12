### 🚀 moss Bot Setup Guide

Welcome to the bot setup guide! Follow the steps below to install and configure the bot correctly. This guide is designed for new users, with clear explanations for each step.

📱 **For Mobile Users (Termux):** [View the guide here](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## Table of Contents

1. [System Requirements](#system-requirements)
2. [Installing the Bot](#installing-the-bot)
3. [Bot Configuration](#bot-configuration)
4. [Running the Bot](#running-the-bot)
5. [Updating the Bot](#updating-the-bot)
6. [Contact & Support](#contact--support)

---

## System Requirements

Before running the bot, make sure you have installed:

- **Node.js** (Version: `22.11.0`)
- **npm** (Version: `10.9.0`)
- **Git**
- **Docker** _(Optional)_

📥 **Node.js & npm:** [Download](https://t.me/KeoAirDropFreeNe/257/1462)

📥 **Git:** [Download](https://t.me/KeoAirDropFreeNe/257/60831)

---

## Installing the Bot

<details>
<summary><strong>🔧 Install via Git</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 Manual Installation</strong></summary>

1. Download and extract the bot manually.
2. Run the same `npm install` command as above.

</details>

<details>
<summary><strong>🐳 Install via Docker</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 On **Windows CMD**, use `%cd%` instead of `$(pwd)`

</details>

---

## Bot Configuration

<details open>
<summary><strong>📜 1. <code>configs.json</code> - Main Configuration</strong></summary>

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



### 🧩 **Configuration Parameters**

| **Parameter Name**                    | **Type**           | **Default**           | **Description**                                                            |
| ------------------------------------- | ------------------ | --------------------- | -------------------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | Enable proxy rotation between accounts                                     |
| `proxyMode`                           | `string`           | `"round"`             | Proxy assignment mode — can be `"static"` or `"round"`                     |
| `skipInvalidProxy`                    | `boolean`          | `true`                | Skip account if its proxy is invalid                                       |
| `proxyRotationInterval`               | `number`           | `2`                   | Minutes between proxy rotations                                            |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | Random delay range (in seconds) between account runs                       |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | Time (in seconds) before restarting all accounts                           |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | Number of accounts to run in parallel                                      |
| `doTasks`                             | `boolean`          | `true`                | Whether to perform main automation tasks                                   |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | Enable automatic referral code binding                                     |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | List of referral codes to randomly assign                                  |
| `tradeSettings.enabled`               | `boolean`          | `true`                | Enable perpetual trading automation                                        |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | Token pairs to trade on                                                    |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | Random margin (in 💎 diamonds) per trade                                   |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | Number of trades to perform each trading session                           |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | Percent of balance to keep as reserve (not used for trading)               |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | Probability bias toward LONG positions (e.g., 0.55 = 55% LONG / 45% SHORT) |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | Maximum number of trades to open simultaneously                            |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | Enable AI chat task                                                        |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | Number of AI chat interactions per session                                 |


</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - User Data</strong></summary>

📥 [Guide from Telegram](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - Proxy List</strong></summary>

📥 [Free proxy from Webshare](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - Wallet List</strong></summary>

📥 [Generate wallets here](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## Running the Bot

<details open>
<summary><strong>🪟 Run on Windows (.bat)</strong></summary>

1. Double-click `run.bat`
2. It auto-updates, installs dependencies, and runs the bot.

> If it fails, right-click → **Run as Administrator**
> Or run from CMD:

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Run on Linux/macOS (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Run with Docker</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> Later restart:

```bash
docker start moss-container
```

</details>

---

## Updating the Bot

<details>
<summary><strong>🔄 If installed via Git</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 If using Docker</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## Contact & Support

- **Support me via** [Extension Link](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - Referral Code: `EYG3CP8I`
- **Donate:** [Donate Here](https://t.me/KeoAirDropFreeNe/312/27801)
- **Contact (Work):** [@MeoMunDep](https://t.me/MeoMunDep)
- **Support Group:** [Join here](https://t.me/KeoAirDropFreeNe)
- **Updates Channel:** [View channel](https://t.me/KeoAirDropFreeNee)
- **YouTube:** [Watch here](https://www.youtube.com/@keoairdropfreene)
- **Instagram:** [Follow](https://www.instagram.com/meomundep)
- **Tiktok:** [Follow](https://www.tiktok.com/@meomundep)

---

⚠️ **Disclaimer**: This code is provided "as is" without any warranties. Use it at your own risk. You are solely responsible for any consequences arising from its use. Redistribution or sale of this code in any form is strictly prohibited.

<p align="center">
  <sub>✨ Created by <b>@MeoMunDep</b> | ✨ Thank you for using the bot, hope you earn from my scripts! Good luck! 🚀
</sub>
</p>
