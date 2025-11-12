### 🚀 Руководство по настройке бота moss

Добро пожаловать в руководство по настройке бота! Следуйте приведённым ниже шагам, чтобы правильно установить и настроить бота. Это руководство предназначено для новых пользователей с подробным объяснением каждого шага.

📱 **Для мобильных пользователей (Termux):** [Смотреть руководство здесь](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## Содержание

1. [Системные требования](#системные-требования)
2. [Установка бота](#установка-бота)
3. [Настройка бота](#настройка-бота)
4. [Запуск бота](#запуск-бота)
5. [Обновление бота](#обновление-бота)
6. [Контакты и поддержка](#контакты-и-поддержка)

---

## Системные требования

Перед запуском бота убедитесь, что у вас установлены:

* **Node.js** (версия: `22.11.0`)
* **npm** (версия: `10.9.0`)
* **Git**
* **Docker** *(необязательно)*

📥 **Node.js & npm:** [Скачать](https://t.me/KeoAirDropFreeNe/257/1462)
📥 **Git:** [Скачать](https://t.me/KeoAirDropFreeNe/257/60831)

---

## Установка бота

<details>
<summary><strong>🔧 Установка через Git</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 Ручная установка</strong></summary>

1. Скачайте и распакуйте бота вручную.
2. Выполните ту же команду `npm install`, что и выше.

</details>

<details>
<summary><strong>🐳 Установка через Docker</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 В **Windows CMD** используйте `%cd%` вместо `$(pwd)`

</details>

---

## Настройка бота

<details open>
<summary><strong>📜 1. <code>configs.json</code> - Основная конфигурация</strong></summary>

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

### 🧩 **Параметры конфигурации**

| **Название параметра**                | **Тип**            | **По умолчанию**      | **Описание**                                                                  |
| ------------------------------------- | ------------------ | --------------------- | ----------------------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | Включить ротацию прокси между аккаунтами                                      |
| `proxyMode`                           | `string`           | `"round"`             | Режим назначения прокси — `"static"` или `"round"`                            |
| `skipInvalidProxy`                    | `boolean`          | `true`                | Пропускать аккаунты с недействительным прокси                                 |
| `proxyRotationInterval`               | `number`           | `2`                   | Интервал ротации прокси в минутах                                             |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | Случайная задержка между запуском аккаунтов в секундах                        |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | Время (в секундах) перед перезапуском всех аккаунтов                          |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | Количество аккаунтов, запускаемых одновременно                                |
| `doTasks`                             | `boolean`          | `true`                | Выполнять основные задачи                                                     |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | Включить автоматическое привязывание реферальных кодов                        |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | Список реферальных кодов для рандомного назначения                            |
| `tradeSettings.enabled`               | `boolean`          | `true`                | Включить автоматическую торговлю                                              |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | Торговые пары                                                                 |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | Случайный размер маржи (в 💎 алмазах) на сделку                               |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | Количество сделок за сессию                                                   |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | Процент баланса, резервируемый и не используемый для торговли                 |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | Вероятностное смещение в сторону LONG (например, 0.55 = 55% LONG / 45% SHORT) |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | Максимальное количество одновременно открытых сделок                          |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | Включить чат с ИИ                                                             |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | Количество взаимодействий с ИИ за сессию                                      |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - Пользовательские данные</strong></summary>

📥 [Руководство из Telegram](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - Список прокси</strong></summary>

📥 [Бесплатные прокси с Webshare](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - Список кошельков</strong></summary>

📥 [Создать кошельки здесь](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## Запуск бота

<details open>
<summary><strong>🪟 Запуск в Windows (.bat)</strong></summary>

1. Дважды щёлкните по `run.bat`
2. Бот автоматически обновится, установит зависимости и запустится.

> Если возникнут ошибки, запустите с правами администратора (ПКМ → **Run as Administrator**)
> Или из CMD:

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Запуск в Linux/macOS (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Запуск с Docker</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> Для последующего перезапуска:

```bash
docker start moss-container
```

</details>

---

## Обновление бота

<details>
<summary><strong>🔄 Если установлен через Git</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Если используете Docker</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## Контакты и поддержка

* **Поддержать меня через** [Ссылка на расширение](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - Реферальный код: `EYG3CP8I`
* **Пожертвования:** [Сделать пожертвование](https://t.me/KeoAirDropFreeNe/312/27801)
* **Контакт (работа):** [@MeoMunDep](https://t.me/MeoMunDep)
* **Группа поддержки:** [Присоединиться](https://t.me/KeoAirDropFreeNe)
* **Канал обновлений:** [Посмотреть](https://t.me/KeoAirDropFreeNee)
* **YouTube:** [Смотреть](https://www.youtube.com/@keoairdropfreene)
* **Instagram:** [Подписаться](https://www.instagram.com/meomundep)
* **Tiktok:** [Подписаться](https://www.tiktok.com/@meomundep)

---

⚠️ **Отказ от ответственности:** Этот код предоставляется «как есть» без каких-либо гарантий. Использование — на ваш страх и риск. Вы несёте полную ответственность за последствия использования. Перераспространение или продажа этого кода в любой форме строго запрещены.

<p align="center">
  <sub>✨ Создано <b>@MeoMunDep</b> | ✨ Спасибо за использование бота, надеюсь, вы заработаете на моих скриптах! Удачи! 🚀</sub>
</p>
