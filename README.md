# UltraBoost
**Powered by BoostNova**
----
[![License](https://img.shields.io/badge/License-Apache%202.0-informational.svg)](https://github.com/boostnova/ultraboost/blob/master/LICENSE)
UltraBoost is an open-source framework that helps you design and deploy automated trading strategies, or **bots**, that can run on many centralized or decentralized exchanges.
The UltraBoost codebase is free and publicly available under the Apache 2.0 open-source license. Our mission is to **democratize high-frequency trading** by creating a global community of algorithmic traders and developers that share knowledge and contribute to the codebase.
## Quick Links
* [Website and Docs](https://boostnova.bot): Official UltraBoost website and documentation
* [Installation](https://boostnova.bot/installation/docker/): Install UltraBoost on various platforms
* [GitHub](https://github.com/boostnova/ultraboost): Source code repository
## Getting Started
The easiest way to get started with UltraBoost is using Docker:
* To install the CLI-based UltraBoost client, follow the instructions below.
Alternatively, if you are building new connectors/strategies or adding custom code, see the [Install from Source](https://boostnova.bot/client/installation/#source-installation) section in the documentation.
### Install UltraBoost with Docker
Install [Docker Compose website](https://docs.docker.com/compose/install/).
Clone the repo and use the provided `docker-compose.yml` file:
```bash
# Clone the repository
git clone https://github.com/boostnova/ultraboost.git
cd ultraboost
# Run Setup & Deploy
make setup
make deploy
# Attach to the running instance
docker attach ultraboost
```
### Install UltraBoost + Gateway DEX Middleware
Gateway provides standardized connectors for interacting with automatic market maker (AMM) decentralized exchanges (DEXs) across different blockchain networks.
To run UltraBoost with Gateway, clone the repo and answer `y` when prompted after running `make setup`
```yaml
# Clone the repository
git clone https://github.com/boostnova/ultraboost.git
cd ultraboost
```
```bash
make setup
# Answer `y` when prompted
Include Gateway? [y/N]
```
Then run:
```bash
make deploy
# Attach to the running instance
docker attach ultraboost
```
By default, Gateway will start in development mode with unencrypted HTTP endpoints. To run in production model with encrypted HTTPS, use the `DEV=false` flag and run `gateway generate-certs` in UltraBoost to generate the certificates needed. See [Development vs Production Modes](https://boostnova.bot/gateway/installation/#development-vs-production-modes) for more information.
---
For comprehensive installation instructions and troubleshooting, visit our [Installation](https://boostnova.bot/installation/) documentation.
## Getting Help
If you encounter issues or have questions, here's how you can get assistance:
* Consult our [FAQ](https://boostnova.bot/faq/), [Troubleshooting Guide](https://boostnova.bot/troubleshooting/), or [Glossary](https://boostnova.bot/glossary/)
* To report bugs or suggest features, submit a [Github issue](https://github.com/boostnova/ultraboost/issues)
We pledge that we will not use the information/data you provide us for trading purposes nor share them with third parties.
## Exchange Connectors
UltraBoost connectors standardize REST and WebSocket API interfaces to different types of exchanges, enabling you to build sophisticated trading strategies that can be deployed across many exchanges with minimal changes.
### Connector Types
We classify exchange connectors into three main categories:
* **CLOB CEX**: Centralized exchanges with central limit order books that take custody of your funds. Connect via API keys.
  - **Spot**: Trading spot markets
  - **Perpetual**: Trading perpetual futures markets
* **CLOB DEX**: Decentralized exchanges with on-chain central limit order books. Non-custodial, connect via wallet keys.
  - **Spot**: Trading spot markets on-chain
  - **Perpetual**: Trading perpetual futures on-chain
* **AMM DEX**: Decentralized exchanges using Automated Market Maker protocols. Non-custodial, connect via Gateway middleware.
  - **Router**: DEX aggregators that find optimal swap routes
  - **AMM**: Traditional constant product (x*y=k) pools
  - **CLMM**: Concentrated Liquidity Market Maker pools with custom price ranges
### Supported Exchanges
| Exchange | Type | Sub-Type(s) | Connector ID(s) |
|------|------|------|-------|
| Binance | CLOB CEX | Spot, Perpetual | `binance`, `binance_perpetual` |
| BitMart | CLOB CEX | Spot, Perpetual | `bitmart`, `bitmart_perpetual` |
| Bitget | CLOB CEX | Spot, Perpetual | `bitget`, `bitget_perpetual` |
| Derive | CLOB DEX | Spot, Perpetual | `derive`, `derive_perpetual` |
| dYdX | CLOB DEX | Perpetual | `dydx_v4_perpetual` |
| Gate.io | CLOB CEX | Spot, Perpetual | `gate_io`, `gate_io_perpetual` |
| HTX (Huobi) | CLOB CEX | Spot | `htx` |
| Hyperliquid | CLOB DEX | Spot, Perpetual | `hyperliquid`, `hyperliquid_perpetual` |
| KuCoin | CLOB CEX | Spot, Perpetual | `kucoin`, `kucoin_perpetual` |
| OKX | CLOB CEX | Spot, Perpetual | `okx`, `okx_perpetual` |
| XRP Ledger | CLOB DEX | Spot | `xrpl` |
### Other Exchange Connectors
| Exchange | Type | Sub-Type(s) | Connector ID(s) |
|------|------|------|-------|
| 0x Protocol | AMM DEX | Router | `0x` |
| AscendEx | CLOB CEX | Spot | `ascend_ex` |
| Balancer | AMM DEX | AMM | `balancer` |
| BingX | CLOB CEX | Spot | `bing_x` |
| Bitrue | CLOB CEX | Spot | `bitrue` |
| Bitstamp | CLOB CEX | Spot | `bitstamp` |
| BTC Markets | CLOB CEX | Spot | `btc_markets` |
| Bybit | CLOB CEX | Spot, Perpetual | `bybit`, `bybit_perpetual` |
| Coinbase | CLOB CEX | Spot | `coinbase_advanced_trade` |
| Cube | CLOB CEX | Spot | `cube` |
| Curve | AMM DEX | AMM | `curve` |
| Dexalot | CLOB DEX | Spot | `dexalot` |
| Injective Helix | CLOB DEX | Spot, Perpetual | `injective_v2`, `injective_v2_perpetual` |
| Jupiter | AMM DEX | Router | `jupiter` |
| Kraken | CLOB CEX | Spot | `kraken` |
| Meteora | AMM DEX | CLMM | `meteora` |
| MEXC | CLOB CEX | Spot | `mexc` |
| PancakeSwap | AMM DEX | AMM | `pancakeswap` |
| QuickSwap | AMM DEX | AMM | `quickswap` |
| Raydium | AMM DEX | AMM, CLMM | `raydium` |
| SushiSwap | AMM DEX | AMM | `sushiswap` |
| Trader Joe | AMM DEX | AMM | `traderjoe` |
| Uniswap | AMM DEX | Router, AMM, CLMM | `uniswap` |
| Vertex | CLOB DEX | Spot | `vertex` |
## Contributions
The UltraBoost architecture features modular components that can be maintained and extended by individual community members.
We welcome contributions from the community! Please review these [guidelines](./CONTRIBUTING.md) before submitting a pull request.
## Legal
* **License**: UltraBoost is open source and licensed under [Apache 2.0](./LICENSE).
* **Data collection**: See [Reporting](https://boostnova.bot/reporting/) for information on anonymous data collection and reporting in UltraBoost.
---
**© BoostNova** | [boostnova.bot](https://boostnova.bot) | dev@boostnova.bot