# Bliss Autopricer

> [!CAUTION]
> **PROJECT DISCONTINUED — NO LONGER MAINTAINED**
>
> I am no longer developing or maintaining Bliss Autopricer. **No further updates, bug fixes, security patches, compatibility updates, or technical support are planned.**
>
> This repository is retained for reference and for anyone who wishes to fork or continue the project independently. The software is provided **as-is**, and I cannot guarantee that it still works with current versions of TF2Autobot, backpack.tf, Steam, or its dependencies.
>
> **Please do not open issues or pull requests expecting a response, review, or fix from me.** If you wish to continue development, you are welcome to fork the repository in accordance with its licence.

[![npm version](https://img.shields.io/npm/v/pg-promise?label=pg-promise)](https://www.npmjs.com/package/pg-promise)
[![Node.js](https://img.shields.io/badge/node-%3E=22.0.0-brightgreen)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-%3E=12-blue)](https://www.postgresql.org/)
[![ESLint](https://img.shields.io/badge/code_style-ESLint-blueviolet)](https://eslint.org/)
[![Prettier](https://img.shields.io/badge/code_style-Prettier-ff69b4)](https://prettier.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Historical upgrade note (for existing installations):** If you're upgrading from a previous version, you **MUST** re-scan or re-add your bots after installation. The bot configuration system has been completely overhauled to use direct file paths. Run `npm run setup` or use the web interface at `http://localhost:3000/bot-config` to reconfigure your bots.

<div align="center">
  <img src="https://github.com/jack-richards/bptf-autopricer/assets/58331725/203fe808-30ff-4d7d-868c-a3ef6d31497d" alt="Bliss Autopricer Logo" style="width: 280px; height: 320px;">
</div>

Bliss Autopricer was developed as a TF2 item pricing system that uses live backpack.tf listings and Steam Community Market data to generate intelligent, profitable prices for TF2Autobot. This fork was based on [Jack Richards' excellent original autopricer](https://github.com/jack-richards/bptf-autopricer) with significant improvements to reliability, multi-bot support, and pricing intelligence.

## 🚀 Installation (Legacy / Unsupported)

```bash
# 1. Clone and install
git clone https://github.com/TF2-Price-DB/bliss-autopricer.git
cd bliss-autopricer
npm install

# 2. Setup bot configuration (auto-discovers your bots)
npm run setup

# 3. Initialize database
npm run validate-config

# 4. Start the autopricer
npm start
```

If the installation works with your environment, the web interface is available at `http://localhost:3000`. These instructions are preserved for reference and are **not actively tested or supported**.

## ✨ Features Added in This Fork

### 🏆 Major Enhancements Over Jack's Original

- **🤖 Multi-Bot Management**: Seamlessly manage multiple TF2Autobot instances with automatic discovery
- **📊 Enhanced Pricing Intelligence**: Pure backpack.tf + Steam Community Market pricing (no more prices.tf dependency)
- **🔄 Bulletproof WebSocket**: Automatic connection recovery with health monitoring
- **⚡ One-Command Setup**: Intelligent configuration wizard that finds your bots automatically
- **🎯 Advanced Fallback System**: SCM pricing for items with insufficient listing data
- **💾 Configuration Migration**: Automatically upgrades old configurations to the new multi-bot system
- **🔌 WebSocket Relay Support**: Connect through internal relay server for multiple instance deployments

### 🙏 Attribution

**Huge thanks to [Jack Richards](https://github.com/jack-richards)** for creating the original [bptf-autopricer](https://github.com/jack-richards/bptf-autopricer)! This fork builds upon his excellent foundation with enhanced features for modern TF2 trading needs.

## 🎯 Key Features (Historically Implemented)

### Intelligent Pricing System

- **📈 Live Listing Analysis**: Real-time backpack.tf listing data processing
- **💰 Steam Community Market Integration**: SCM fallback pricing for rare/illiquid items
- **🎪 Unusual Support**: Full pricing support for unusual items and special attributes
- **🛡️ Profit Protection**: Configurable margins and sanity checks
- **🔍 Outlier Detection**: Automatic filtering of suspicious listings

### Advanced Bot Management

- **🔍 Auto-Discovery**: Finds all TF2Autobot installations automatically
- **🔄 Easy Switching**: Switch between bots with a single click
- **📊 Unified Dashboard**: Manage all your bots from one interface
- **⚙️ Configuration Backup**: Safe configuration migration and backup

### Reliability & Performance

- **🔌 WebSocket Health Monitoring**: Real-time connection status tracking
- **♻️ Auto-Recovery**: Automatic reconnection when connections fail
- **⚡ Rate Limiting**: Intelligent API request management
- **📦 Batch Processing**: Efficient handling of large item lists

## 📋 Original Requirements (Not Revalidated)

- **Node.js** v22.0.0+ (required for built-in fetch support)
- **PostgreSQL** v12+
- **TF2Autobot** (any recent version)
- **API Keys**: backpack.tf API key and Steam API key

## 📖 Documentation (Unmaintained)

- **[📦 Installation Guide](docs/INSTALLATION.md)** - Complete setup instructions
- **[🤖 Multi-Bot Setup](docs/MULTI-BOT.md)** - Managing multiple bots
- **[⚙️ Configuration Reference](docs/CONFIGURATION.md)** - All configuration options
- **[🔧 Troubleshooting](docs/TROUBLESHOOTING.md)** - Common issues and solutions
- **[📡 API Documentation](docs/API.md)** - REST API and WebSocket usage

## 🏗️ Architecture

### Pricing Logic Flow

1. **Live Listings**: Analyze backpack.tf buy/sell listings from trusted sources
2. **Steam Community Market**: Fallback to SCM prices with configurable margins
3. **Sanity Checks**: Validate prices against configured thresholds
4. **Profit Margins**: Apply buy/sell spreads for profitable trading
5. **TF2Autobot Integration**: Seamless pricelist updates via Socket.IO

### Multi-Bot System

```
Bliss Autopricer
├── Bot Discovery Engine
├── Configuration Manager
├── Pricing Engine
├── WebSocket Manager
└── Web Interface
    ├── Bot Selection
    ├── Price Monitoring
    ├── Configuration
    └── Health Dashboard
```

## 🔧 API Keys Setup

You'll need these API keys for full functionality:

1. **Backpack.tf API Key**: Get from [backpack.tf/api/register](https://backpack.tf/api/register)
2. **Steam API Key**: Get from [steamcommunity.com/dev/apikey](https://steamcommunity.com/dev/apikey)

⚠️ **Important**: Without proper API keys, you may encounter 403 errors. The setup wizard will help you configure these correctly.

## 📊 Web Interface

The web dashboard provides:

- **📋 Pricelist Management**: View and edit item prices
- **🤖 Bot Configuration**: Switch between multiple bots
- **📈 Price Analytics**: Monitor pricing performance
- **🔗 WebSocket Status**: Real-time connection health
- **📊 Trade Statistics**: P&L tracking and analytics

## 🔄 Updating Your Installation

To pull the last available version of this repository (there is no ongoing release or update schedule):

```bash
cd bliss-autopricer
git pull origin
npm install
```

Back up `pricerConfig.json`, `files/`, and your database before making any changes. These instructions are historical and there is no guarantee of compatibility or safe upgrades.

## 🔌 WebSocket Relay Configuration

For deployments with multiple autopricer instances, you can use the [backpack-tf-socket-relay](https://github.com/OliverPerring/backpack-tf-socket-relay) to share a single websocket connection to backpack.tf.

### Setup Relay Mode

1. **Start your relay server** (default port 7789):

   ```bash
   # In your relay server directory
   npm start
   ```

2. **Configure autopricer** via web interface at `/settings` or manually in `config.json`:

   ```json
   {
     "websocketRelay": {
       "enabled": true,
       "protocol": "ws",
       "host": "localhost",
       "port": 7789
     }
   }
   ```

3. **Restart autopricer** to use relay connection

The autopricer will connect to `ws://localhost:7789/relay` when relay mode is enabled.

### Benefits of Relay Mode

- **Multiple Instances**: Run several autopricing instances with one backpack.tf connection
- **Reduced API Load**: Single websocket connection shared across all instances
- **Better Reliability**: Centralized connection management with automatic failover
- **Compliance**: Respects backpack.tf's single connection per API key limitation

## 🤝 Forking and Community Development

I am **not accepting or maintaining feature requests, bug reports, or pull requests** for this project. Anyone interested in carrying it forward is welcome to fork the code and maintain their own version, subject to the MIT licence. A fork is independent and is not endorsed or supported by me.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚡ Support and Maintenance Status

**There is no official support for Bliss Autopricer.** I am no longer monitoring issues, reviewing pull requests, troubleshooting installations, or providing fixes. Existing documentation in the [docs](docs/) directory remains available as a reference only and may be outdated.

If you encounter bugs, security issues, or broken integrations, you will need to resolve them yourself or seek help from others maintaining their own forks.

---

<div align="center">

**Bliss Autopricer — Discontinued / Unmaintained**

*Thanks to everyone who used or contributed to the project, and to [Jack Richards](https://github.com/jack-richards/bptf-autopricer) for the original project.*

</div>
