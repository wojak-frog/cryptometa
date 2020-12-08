# cryptometa

> Public repository used by ViewBlock to display token information and compute score

#### How to add/update your token

- Fork the repo
- Create a folder in the appropriate chain folder named after your contract address
- Your image must be either SVG or PNG 256x256 (max 100kb) and named `logo.<extension>`
- Add information of your project using the following spec:

| Param               | Type     | Required   | Points  | Notes                                                     |
| ------------------- | -------- | ---------- | ------- | --------------------------------------------------------- |
| name                | `String` | `true`     |         |                                                           |
| symbol              | `String` | `true`     |         |                                                           |
| web                 | `String` | `false`    | 5       |                                                           |
| decimals            | `Number` | `false`    |         |                                                           |
| supply              | `Number` | `false`    |         |                                                           |
| email               | `String` | `false`    |         | Email of the team                                         |
| whitepaper          | `String` | `false`    | 10      | Link to the WP                                            |
| holders             | `Bool`   | `false`    | 10      | Only specify if more than 1000 holders without airdrops   |
| publicTeam          | `Bool`   | `false`    | 20      |                                                           |
| product             | `Bool`   | `false`    | 30      | Usable product on mainnet with users giving token utility |
| links.research      | `String` | `false`    | 10      | Either binance research, TokenData or the like            |
| links.github        | `String` | `false`    | 10      |                                                           |
| links.linkedin      | `String` | `false`    | 10      |                                                           |
| links.twitter       | `String` | `false`    | 5       |                                                           |
| links.medium        | `String` | `false`    |         |                                                           |
| links.facebook      | `String` | `false`    |         |                                                           |
| links.reddit        | `String` | `false`    |         |                                                           |
| links.coinmarketcap | `String` | `false`    |         |                                                           |
| links.youtube       | `String` | `false`    |         |                                                           |
| links.telegram      | `String` | `false`    |         |                                                           |
| links.instagram     | `String` | `false`    |         |                                                           |

- Create and submit a PR

#### Usage

```
yarn add cryptometa
```

| Param               | Type             | Required | Example                                                 |
| ------------------- | ---------------- | -------- | ------------------------------------------------------- |
| payload             | `String`/`Array` | `true`   | `ETH`, `BNB.AVA-645`, `zilliqa.zil14x...`               |
| select              | `String`         | `false`  | `logo score name symbol`                                |

```js
const meta = require('cryptometa')

const exOne = await meta('ETH')
const exTwo = await meta(['BNB.AVA-645', 'ETH'], 'logo')
```

Use the server entry point if you do not mind loading all the token data once.
It is cached for 30 minutes but can grow big, thus it's exclusion from the bundle.

```js
const meta = require('cryptometa/src/server')
```
