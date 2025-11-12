### 🚀 Guia de Configuração do Bot moss

Bem-vindo ao guia de configuração do bot! Siga os passos abaixo para instalar e configurar o bot corretamente. Este guia foi feito para novos usuários, com explicações claras em cada etapa.

📱 **Para usuários móveis (Termux):** [Veja o guia aqui](https://github.com/MeoMunDep/Guides-for-using-my-script-on-termux)

---

## Índice

1. [Requisitos do Sistema](#requisitos-do-sistema)
2. [Instalação do Bot](#instalação-do-bot)
3. [Configuração do Bot](#configuração-do-bot)
4. [Executando o Bot](#executando-o-bot)
5. [Atualizando o Bot](#atualizando-o-bot)
6. [Contato & Suporte](#contato--suporte)

---

## Requisitos do Sistema

Antes de executar o bot, certifique-se de que você instalou:

* **Node.js** (Versão: `22.11.0`)
* **npm** (Versão: `10.9.0`)
* **Git**
* **Docker** *(Opcional)*

📥 **Node.js & npm:** [Baixar](https://t.me/KeoAirDropFreeNe/257/1462)
📥 **Git:** [Baixar](https://t.me/KeoAirDropFreeNe/257/60831)

---

## Instalação do Bot

<details>
<summary><strong>🔧 Instalar via Git</strong></summary>

```bash
git clone https://github.com/MeoMunDep/moss.git
cd moss
npm install --no-audit --no-fund --prefer-offline --force user-agents axios meo-forkcy-colors meo-forkcy-utils meo-forkcy-proxy meo-forkcy-logger
```

</details>

<details>
<summary><strong>🧰 Instalação Manual</strong></summary>

1. Baixe e extraia o bot manualmente.
2. Execute o mesmo comando `npm install` mencionado acima.

</details>

<details>
<summary><strong>🐳 Instalar via Docker</strong></summary>

```bash
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> 💡 No **Windows CMD**, use `%cd%` em vez de `$(pwd)`

</details>

---

## Configuração do Bot

<details open>
<summary><strong>📜 1. <code>configs.json</code> - Configuração Principal</strong></summary>

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

### 🧩 **Parâmetros de Configuração**

| **Nome do Parâmetro**                 | **Tipo**           | **Padrão**            | **Descrição**                                                              |
| ------------------------------------- | ------------------ | --------------------- | -------------------------------------------------------------------------- |
| `rotateProxy`                         | `boolean`          | `false`               | Ativa rotação de proxy entre contas                                        |
| `proxyMode`                           | `string`           | `"round"`             | Modo de atribuição de proxy — pode ser `"static"` ou `"round"`             |
| `skipInvalidProxy`                    | `boolean`          | `true`                | Pula contas com proxy inválido                                             |
| `proxyRotationInterval`               | `number`           | `2`                   | Minutos entre rotações de proxy                                            |
| `delayEachAccount`                    | `[number, number]` | `[1, 1]`              | Intervalo aleatório (segundos) entre execuções das contas                  |
| `timeToRestartAllAccounts`            | `number`           | `300`                 | Tempo (segundos) antes de reiniciar todas as contas                        |
| `howManyAccountsRunInOneTime`         | `number`           | `1`                   | Quantidade de contas rodando em paralelo                                   |
| `doTasks`                             | `boolean`          | `true`                | Se deve executar as tarefas principais                                     |
| `bindReferralCode.enabled`            | `boolean`          | `true`                | Ativa a vinculação automática dos códigos de indicação                     |
| `bindReferralCode.codes`              | `string[]`         | `["EYG3CP8I"]`        | Lista de códigos de indicação para atribuição aleatória                    |
| `tradeSettings.enabled`               | `boolean`          | `true`                | Ativa automação de trade contínuo                                          |
| `tradeSettings.pairs`                 | `string[]`         | `["BTC","ETH","SOL"]` | Pares de tokens para trade                                                 |
| `tradeSettings.marginAmount`          | `[number, number]` | `[10, 20]`            | Margem aleatória (em 💎 diamantes) por trade                               |
| `tradeSettings.countPerSession`       | `[number, number]` | `[10, 20]`            | Quantidade de trades por sessão                                            |
| `tradeSettings.balanceReservePercent` | `number`           | `10`                  | Percentual do saldo reservado (não usado para trading)                     |
| `tradeSettings.longShortBias`         | `number`           | `0.55`                | Viés de probabilidade para posições LONG (ex: 0.55 = 55% LONG / 45% SHORT) |
| `tradeSettings.maxConcurrentTrades`   | `number`           | `1`                   | Número máximo de trades abertos simultaneamente                            |
| `chatWithAi.enabled`                  | `boolean`          | `true`                | Ativa tarefa de chat com IA                                                |
| `chatWithAi.amount`                   | `[number, number]` | `[10, 20]`            | Número de interações com IA por sessão                                     |

</details>

<details>
<summary><strong>🗂️ 2. <code>datas.txt</code> - Dados do Usuário</strong></summary>

📥 [Guia do Telegram](https://t.me/KeoAirDropFreeNee/2027)

```txt
ey...
ey...
ey...
```

</details>

<details>
<summary><strong>🌐 3. <code>proxies.txt</code> - Lista de Proxies</strong></summary>

📥 [Proxy gratuito do Webshare](https://www.webshare.io/?referral_code=4l5kb3glsce7)

```txt
host:port
http://host:port
socks5://user:pass@host:port
...
```

</details>

<details>
<summary><strong>💼 4. <code>wallets.txt</code> - Lista de Carteiras</strong></summary>

📥 [Gere carteiras aqui](https://github.com/MeoMunDep/Automatic-Ultimate-Create-Wallets-for-Airdrop)

```txt
0xabc123...
0xdef456...
...
```

</details>

---

## Executando o Bot

<details open>
<summary><strong>🪟 Rodar no Windows (.bat)</strong></summary>

1. Dê um duplo clique em `run.bat`
2. Ele atualiza automaticamente, instala dependências e executa o bot.

> Se falhar, clique com o botão direito → **Executar como Administrador**
> Ou execute pelo CMD:

```cmd
run.bat
```

</details>

<details>
<summary><strong>🐧 Rodar no Linux/macOS (.sh)</strong></summary>

```bash
chmod +x run.sh
./run.sh
```

</details>

<details>
<summary><strong>🐳 Rodar com Docker</strong></summary>

```bash
docker stop moss-container 2>/dev/null && docker rm moss-container 2>/dev/null
docker build -t moss-image .
docker run -d --name moss-container -v $(pwd)/logs:/app/logs moss-image
```

> Para reiniciar depois:

```bash
docker start moss-container
```

</details>

---

## Atualizando o Bot

<details>
<summary><strong>🔄 Se instalado via Git</strong></summary>

```bash
cd moss
git pull origin main
npm install
```

</details>

<details>
<summary><strong>🐳 Se estiver usando Docker</strong></summary>

```bash
docker stop moss-container
docker rm moss-container
docker build -t moss-image .
docker run -d --name moss-container moss-image
```

</details>

---

## Contato & Suporte

* **Apoie-me via** [Link da Extensão](https://chromewebstore.google.com/detail/moss/ajlhmclpjddfebgfpahnlodliljdnbie) - Código de Indicação: `EYG3CP8I`
* **Doações:** [Doe aqui](https://t.me/KeoAirDropFreeNe/312/27801)
* **Contato (Trabalho):** [@MeoMunDep](https://t.me/MeoMunDep)
* **Grupo de Suporte:** [Participe aqui](https://t.me/KeoAirDropFreeNe)
* **Canal de Atualizações:** [Ver canal](https://t.me/KeoAirDropFreeNee)
* **YouTube:** [Assista aqui](https://www.youtube.com/@keoairdropfreene)
* **Instagram:** [Siga](https://www.instagram.com/meomundep)
* **Tiktok:** [Siga](https://www.tiktok.com/@meomundep)

---

⚠️ **Aviso Legal:** Este código é fornecido "como está", sem nenhuma garantia. Use por sua conta e risco. Você é o único responsável por quaisquer consequências decorrentes do uso. A redistribuição ou venda deste código em qualquer forma é estritamente proibida.

<p align="center">
  <sub>✨ Criado por <b>@MeoMunDep</b> | ✨ Obrigado por usar o bot, espero que ganhe com meus scripts! Boa sorte! 🚀</sub>
</p>
