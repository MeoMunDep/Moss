### 🚀 moss 机器人安装指南

欢迎来到机器人安装指南！请按照以下步骤正确安装和配置机器人。本指南专为新用户设计，逐步讲解清晰易懂。

📱 **手机用户 (Termux)：** [点击查看指南](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## 目录

1. [系统要求](#系统要求)
2. [安装机器人](#安装机器人)
3. [机器人配置](#机器人配置)
4. [运行机器人](#运行机器人)
5. [更新机器人](#更新机器人)
6. [联系与支持](#联系与支持)

---

## 系统要求

在运行机器人之前，请确保你已安装以下软件：

* **Node.js**（版本：`22.11.0`）
* **npm**（版本：`10.9.0`）
* **Git**
* **Docker** *(可选)*

📥 **Node.js & npm:** [下载地址](https://t.me/KeoAirDropFreeNe/257/1462)
📥 **Git:** [下载地址](https://t.me/KeoAirDropFreeNe/257/60831)

---

## 安装机器人

<details>
<summary><strong>🔧 通过 Git 安装</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 手动安装</strong></summary>

1. 手动下载并解压机器人文件。
2. 运行上面的 `npm install` 命令。

</details>

<details>
<summary><strong>🐳 使用 Docker 安装</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 **Windows CMD 用户请使用** `%cd%` **替代** `$(pwd)`

</details>

---

## 机器人配置

<details open>
<summary><strong>📜 1. <code>configs.json</code> - 主配置文件</strong></summary>

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

### 🧩 **配置参数说明**

| **参数名**                               | **类型**             | **默认值**               | **说明**                          |
| ------------------------------------- | ------------------ | --------------------- | ------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | 是否启用代理轮换                        |
| `proxyMode`                           | `string`           | `"round"`             | 代理分配模式：`"static"` 或 `"round"`   |
| `skipInvalidProxy`                    | `boolean`          | `true`                | 跳过无效代理                          |
| `proxyRotationInterval`               | `number`           | `2`                   | 每隔几分钟轮换代理                       |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | 每个账号运行间的随机延迟（秒）                 |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | 多少秒后重新启动所有账号                    |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | 同时运行的账号数量                       |
| `doTasks`                             | `boolean`          | `true`                | 是否执行主要自动化任务                     |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | 是否启用自动绑定推荐码                     |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | 推荐码列表                           |
| `tradeSettings.enabled`               | `boolean`          | `true`                | 是否启用自动交易功能                      |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | 要交易的币种对                         |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | 每笔交易保证金范围（💎 钻石）                |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | 每轮交易的次数                         |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | 保留余额百分比（不参与交易）                  |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | 多空方向偏好（例如：0.55 = 55%做多 / 45%做空） |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | 同时最多开启的交易数量                     |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | 是否启用 AI 聊天任务                    |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | 每轮 AI 聊天的交互次数                   |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - 用户数据</strong></summary>

📥 [Telegram 指南](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - 代理列表</strong></summary>

📥 [Webshare 免费代理](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - 钱包列表</strong></summary>

📥 [生成钱包](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## 运行机器人

<details open>
<summary><strong>🪟 在 Windows 上运行 (.bat)</strong></summary>

1. 双击 `run.bat`
2. 自动更新、安装依赖并启动机器人。

> 如果运行失败，请右键 → **以管理员身份运行**
> 或在命令行执行：

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 在 Linux/macOS 上运行 (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 使用 Docker 运行</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 之后重启：

```bash
docker start moss-container
```

</details>

---

## 更新机器人

<details>
<summary><strong>🔄 Git 安装用户</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Docker 用户</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## 联系与支持

* **支持我（扩展链接）** [Chrome 扩展](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - 推荐码：`EYG3CP8I`
* **捐赠：** [点击捐赠](https://t.me/KeoAirDropFreeNe/312/27801)
* **工作联系：** [@MeoMunDep](https://t.me/MeoMunDep)
* **支持群组：** [加入群组](https://t.me/KeoAirDropFreeNe)
* **更新频道：** [查看频道](https://t.me/KeoAirDropFreeNee)
* **YouTube：** [观看视频](https://www.youtube.com/@keoairdropfreene)
* **Instagram：** [关注我](https://www.instagram.com/meomundep)
* **Tiktok：** [关注我](https://www.tiktok.com/@meomundep)

---

⚠️ **免责声明：** 此代码以 “原样” 提供，不提供任何担保。使用本脚本即表示您自行承担风险。严禁以任何形式转载或出售本代码。

<p align="center">
  <sub>✨ 由 <b>@MeoMunDep</b> 制作 | 感谢使用本机器人，祝您脚本收益满满！🚀</sub>
</p>
