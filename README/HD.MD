### 🚀 moss बॉट सेटअप गाइड

बॉट सेटअप गाइड में आपका स्वागत है! सही तरीके से बॉट इंस्टॉल और कॉन्फ़िगर करने के लिए नीचे दिए गए चरणों का पालन करें। यह गाइड नए उपयोगकर्ताओं के लिए डिजाइन किया गया है, जिसमें हर चरण को स्पष्ट रूप से समझाया गया है।

📱 **मोबाइल उपयोगकर्ताओं के लिए (Termux):** [यहाँ गाइड देखें](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## विषय सूची

1. [सिस्टम आवश्यकताएँ](#सिस्टम-आवश्यकताएँ)
2. [बॉट इंस्टॉल करना](#बॉट-इंस्टॉल-करना)
3. [बॉट कॉन्फ़िगरेशन](#बॉट-कॉन्फ़िगरेशन)
4. [बॉट चलाना](#बॉट-चलाना)
5. [बॉट अपडेट करना](#बॉट-अपडेट-करना)
6. [संपर्क और समर्थन](#संपर्क-और-समर्थन)

---

## सिस्टम आवश्यकताएँ

बॉट चलाने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित इंस्टॉल हों:

* **Node.js** (संस्करण: `22.11.0`)
* **npm** (संस्करण: `10.9.0`)
* **Git**
* **Docker** *(वैकल्पिक)*

📥 **Node.js & npm:** [डाउनलोड करें](https://t.me/KeoAirDropFreeNe/257/1462)
📥 **Git:** [डाउनलोड करें](https://t.me/KeoAirDropFreeNe/257/60831)

---

## बॉट इंस्टॉल करना

<details>
<summary><strong>🔧 Git के जरिए इंस्टॉल करें</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 मैनुअल इंस्टॉलेशन</strong></summary>

1. बॉट को मैनुअली डाउनलोड और एक्सट्रैक्ट करें।
2. ऊपर दिए गए `npm install` कमांड को चलाएं।

</details>

<details>
<summary><strong>🐳 Docker के जरिए इंस्टॉल करें</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 **Windows CMD** में `$(pwd)` की जगह `%cd%` का उपयोग करें

</details>

---

## बॉट कॉन्फ़िगरेशन

<details open>
<summary><strong>📜 1. <code>configs.json</code> - मुख्य कॉन्फ़िगरेशन</strong></summary>

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

### 🧩 **कॉन्फ़िगरेशन पैरामीटर**

| **पैरामीटर नाम**                      | **प्रकार**         | **डिफ़ॉल्ट**          | **विवरण**                                                             |
| ------------------------------------- | ------------------ | --------------------- | --------------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | क्या अकाउंट्स के बीच प्रॉक्सी घुमाएं                                  |
| `proxyMode`                           | `string`           | `"round"`             | प्रॉक्सी असाइनमेंट मोड — `"static"` या `"round"`                      |
| `skipInvalidProxy`                    | `boolean`          | `true`                | यदि प्रॉक्सी अमान्य है तो अकाउंट छोड़ें                               |
| `proxyRotationInterval`               | `number`           | `2`                   | प्रॉक्सी रोटेशन के बीच का समय (मिनट में)                              |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | अकाउंट चलाने के बीच यादृच्छिक देरी (सेकंड में)                        |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | सभी अकाउंट्स को रीस्टार्ट करने से पहले का समय (सेकंड में)             |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | एक साथ कितने अकाउंट चलाएं                                             |
| `doTasks`                             | `boolean`          | `true`                | मुख्य स्वचालन कार्य करें या नहीं                                      |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | रिफरल कोड ऑटो-बाइंडिंग चालू करें                                      |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | बाइंड करने के लिए रिफरल कोड की सूची                                   |
| `tradeSettings.enabled`               | `boolean`          | `true`                | ट्रेडिंग ऑटोमेशन चालू करें                                            |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | ट्रेडिंग के लिए टोकन पेयर्स                                           |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | प्रत्येक ट्रेड के लिए यादृच्छिक मार्जिन (💎 डायमंड में)               |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | प्रत्येक ट्रेडिंग सत्र में ट्रेड की संख्या                            |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | रिजर्व के रूप में रखने के लिए बैलेंस का प्रतिशत (ट्रेड के लिए नहीं)   |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | LONG पोजीशन के लिए संभाव्यता पूर्वाग्रह (0.55 = 55% LONG / 45% SHORT) |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | एक साथ अधिकतम खुली ट्रेड्स की संख्या                                  |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | AI चैट टास्क सक्षम करें                                               |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | प्रति सत्र AI चैट इंटरैक्शन की संख्या                                 |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - उपयोगकर्ता डेटा</strong></summary>

📥 [Telegram गाइड](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - प्रॉक्सी सूची</strong></summary>

📥 [Webshare मुफ्त प्रॉक्सी](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - वॉलेट सूची</strong></summary>

📥 [यहाँ वॉलेट बनाएं](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## बॉट चलाना

<details open>
<summary><strong>🪟 Windows पर चलाएं (.bat)</strong></summary>

1. `run.bat` पर डबल-क्लिक करें
2. यह अपने आप अपडेट होगा, डिपेंडेंसी इंस्टॉल करेगा और बॉट रन करेगा।

> अगर विफल हो तो राइट-क्लिक करें → **Run as Administrator**
> या CMD से चलाएं:

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Linux/macOS पर चलाएं (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Docker के साथ चलाएं</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> बाद में रीस्टार्ट करें:

```bash
docker start moss-container
```

</details>

---

## बॉट अपडेट करें

<details>
<summary><strong>🔄 Git से इंस्टॉल किए गए बॉट के लिए</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Docker उपयोगकर्ताओं के लिए</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## संपर्क और समर्थन

* **मदद करें:** [एक्सटेंशन लिंक](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - रेफरल कोड: `EYG3CP8I`
* **डोनेट करें:** [यहाँ डोनेट करें](https://t.me/KeoAirDropFreeNe/312/27801)
* **संपर्क (काम):** [@MeoMunDep](https://t.me/MeoMunDep)
* **सपोर्ट ग्रुप:** [यहाँ जुड़ें](https://t.me/KeoAirDropFreeNe)
* **अपडेट चैनल:** [देखें](https://t.me/KeoAirDropFreeNee)
* **YouTube:** [देखें](https://www.youtube.com/@keoairdropfreene)
* **Instagram:** [फॉलो करें](https://www.instagram.com/meomundep)
* **Tiktok:** [फॉलो करें](https://www.tiktok.com/@meomundep)

---

⚠️ **अस्वीकरण:** यह कोड "जैसा है" प्रदान किया गया है, कोई गारंटी नहीं दी जाती। उपयोग करने पर आप स्वयं जिम्मेदार होंगे। इस कोड को किसी भी रूप में पुनर्वितरित या बेचना सख्त मना है।

<p align="center">
  <sub>✨ बनाया गया <b>@MeoMunDep</b> द्वारा | ✨ बॉट का उपयोग करने के लिए धन्यवाद, मेरी स्क्रिप्ट से लाभ मिले! शुभकामनाएँ! 🚀</sub>
</p>
