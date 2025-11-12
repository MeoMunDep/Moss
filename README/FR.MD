### 🚀 Guide d'installation du bot moss

Bienvenue dans le guide d'installation du bot ! Suivez les étapes ci-dessous pour installer et configurer correctement le bot. Ce guide est conçu pour les nouveaux utilisateurs, avec des explications claires à chaque étape.

📱 **Pour les utilisateurs mobiles (Termux) :** [Voir le guide ici](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## Table des matières

1. [Prérequis système](#prérequis-système)
2. [Installation du bot](#installation-du-bot)
3. [Configuration du bot](#configuration-du-bot)
4. [Lancement du bot](#lancement-du-bot)
5. [Mise à jour du bot](#mise-à-jour-du-bot)
6. [Contact & Support](#contact--support)

---

## Prérequis système

Avant de lancer le bot, assurez-vous d'avoir installé :

* **Node.js** (version : `22.11.0`)
* **npm** (version : `10.9.0`)
* **Git**
* **Docker** *(optionnel)*

📥 **Node.js & npm :** [Télécharger](https://t.me/KeoAirDropFreeNe/257/1462)
📥 **Git :** [Télécharger](https://t.me/KeoAirDropFreeNe/257/60831)

---

## Installation du bot

<details>
<summary><strong>🔧 Installation via Git</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 Installation manuelle</strong></summary>

1. Téléchargez et extrayez le bot manuellement.
2. Lancez la même commande `npm install` que ci-dessus.

</details>

<details>
<summary><strong>🐳 Installation via Docker</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 Sur **Windows CMD**, utilisez `%cd%` à la place de `$(pwd)`

</details>

---

## Configuration du bot

<details open>
<summary><strong>📜 1. <code>configs.json</code> - Configuration principale</strong></summary>

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

### 🧩 **Paramètres de configuration**

| **Nom du paramètre**                  | **Type**           | **Par défaut**        | **Description**                                                        |
| ------------------------------------- | ------------------ | --------------------- | ---------------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | Activer la rotation des proxies entre les comptes                      |
| `proxyMode`                           | `string`           | `"round"`             | Mode d’attribution des proxies — `"static"` ou `"round"`               |
| `skipInvalidProxy`                    | `boolean`          | `true`                | Ignorer les comptes avec proxy invalide                                |
| `proxyRotationInterval`               | `number`           | `2`                   | Minutes entre chaque rotation de proxy                                 |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | Intervalle aléatoire de délai (en secondes) entre les comptes          |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | Temps (en secondes) avant de redémarrer tous les comptes               |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | Nombre de comptes exécutés en parallèle                                |
| `doTasks`                             | `boolean`          | `true`                | Effectuer les tâches principales                                       |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | Activer la liaison automatique des codes de parrainage                 |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | Liste des codes de parrainage à attribuer aléatoirement                |
| `tradeSettings.enabled`               | `boolean`          | `true`                | Activer l’automatisation du trading perpétuel                          |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | Paires de tokens à trader                                              |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | Marge aléatoire (en 💎 diamants) par trade                             |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | Nombre de trades par session                                           |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | Pourcentage du solde à garder en réserve (non utilisé pour le trading) |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | Biais de probabilité vers LONG (ex : 0.55 = 55 % LONG / 45 % SHORT)    |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | Nombre maximal de trades ouverts simultanément                         |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | Activer la tâche de chat avec l’IA                                     |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | Nombre d’interactions de chat IA par session                           |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - Données utilisateurs</strong></summary>

📥 [Guide depuis Telegram](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - Liste des proxies</strong></summary>

📥 [Proxy gratuit depuis Webshare](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - Liste des wallets</strong></summary>

📥 [Générez vos wallets ici](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## Lancement du bot

<details open>
<summary><strong>🪟 Exécution sous Windows (.bat)</strong></summary>

1. Double-cliquez sur `run.bat`
2. Il se mettra à jour automatiquement, installera les dépendances et lancera le bot.

> Si ça échoue, faites un clic droit → **Exécuter en tant qu’administrateur**
> Ou lancez depuis CMD :

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Exécution sous Linux/macOS (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Exécution avec Docker</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> Pour redémarrer plus tard :

```bash
docker start moss-container
```

</details>

---

## Mise à jour du bot

<details>
<summary><strong>🔄 Si installé via Git</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Si vous utilisez Docker</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## Contact & Support

* **Soutenez-moi via** [Lien Extension](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - Code parrain : `EYG3CP8I`
* **Faire un don :** [Faire un don ici](https://t.me/KeoAirDropFreeNe/312/27801)
* **Contact (Travail) :** [@MeoMunDep](https://t.me/MeoMunDep)
* **Groupe de support :** [Rejoindre ici](https://t.me/KeoAirDropFreeNe)
* **Chaîne des mises à jour :** [Voir la chaîne](https://t.me/KeoAirDropFreeNee)
* **YouTube :** [Regarder ici](https://www.youtube.com/@keoairdropfreene)
* **Instagram :** [Suivre](https://www.instagram.com/meomundep)
* **Tiktok :** [Suivre](https://www.tiktok.com/@meomundep)

---

⚠️ **Clause de non-responsabilité :** Ce code est fourni "tel quel" sans aucune garantie. Utilisez-le à vos propres risques. Vous êtes seul responsable de toute conséquence liée à son utilisation. La redistribution ou la vente de ce code sous quelque forme que ce soit est strictement interdite.

<p align="center">
  <sub>✨ Créé par <b>@MeoMunDep</b> | ✨ Merci d’utiliser le bot, j’espère que vous gagnerez grâce à mes scripts ! Bonne chance ! 🚀</sub>
</p>
