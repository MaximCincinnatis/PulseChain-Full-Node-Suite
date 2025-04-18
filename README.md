# Blockchain Node Suite - PulseChain & Ethereum

A professional-grade node installation suite that supports both PulseChain and Ethereum networks. Choose your preferred network and installation method during setup.

## Quick Start

```bash
# Clone the repository
git clone https://github.com/MaximCincinnatis/PulseChain-Ethereum-Node-Suite.git
cd PulseChain-Ethereum-Node-Suite

# Make the setup script executable
chmod +x setup.sh

# Run the setup script
./setup.sh
```

The setup script will guide you through the installation process:
1. Check system requirements
2. Choose your installation method (Docker Compose or Traditional)
3. Select your preferred network (PulseChain or Ethereum)
4. Configure your node settings
5. Select your operation mode

## System Requirements

- CPU: 4+ cores (8+ recommended)
- RAM: 16GB minimum (32GB recommended)
- Storage: 2TB+ SSD/NVMe (4TB+ for archive nodes)
- Internet: 25+ Mbps connection
- Operating System: Ubuntu 20.04+ / Debian 11+ / Windows 10/11 with WSL2

## Operation Modes

The node supports four operation modes that can be selected during setup or changed later:

### LOCAL_INTENSIVE
- Optimized for unrestricted local access
- Maximum performance for indexing and RPC operations
- No rate limiting or authentication
- Suitable for development and local indexing
- Uses up to 70% of system memory for caching
- Unlimited API method access
- Automatic system tuning for maximum performance

### LOCAL_STANDARD
- Balanced local access with basic restrictions
- Standard performance settings
- Basic rate limiting (1000 requests/minute)
- Limited API methods
- Uses 50% of system memory for caching
- Suitable for general local use

### PUBLIC_SECURE
- Enhanced security for public access
- Rate limiting (100 requests/minute)
- Authentication enabled
- Restricted API methods
- Uses 40% of system memory for caching
- Suitable for production RPC endpoints

### PUBLIC_ARCHIVE
- Optimized for archive node operation
- Strict rate limiting (50 requests/minute)
- Full historical data access
- Uses 60% of system memory for caching
- Suitable for public archive services

## Local Machine Access

The node includes comprehensive local machine connection settings:

### Connection Endpoints
- HTTP RPC: http://[API_ADDR]:8545
- WebSocket: ws://[API_ADDR]:8546
- Configurable API methods
- Cross-machine access support

### Access Controls
- Network range restrictions
- IP whitelisting
- Rate limiting configuration
- Authentication options

### Performance Settings
- Configurable connection limits
- Cache size optimization
- Indexing options
- Mempool monitoring

View your local connection settings anytime:
```bash
./setup.sh config
# Select option 2: Show local machine connection settings
```

## Enhanced Features

### Backup System
- Encrypted backup support with OpenSSL
- Configurable retention policies
- Backup verification and integrity checks
- Remote backup capabilities
- Space management and cleanup

### Configuration Management
- Centralized JSON-based configuration
- User-friendly configuration menu
- Dynamic resource allocation
- Operation mode switching
- Health monitoring and alerts

### Mempool Monitoring
- Detailed transaction tracking
- Gas price analysis
- Custom metrics collection
- Alert system for anomalies

## Installation Methods

### Docker Compose (Recommended)
- Simplified installation and management
- Automatic updates and dependency handling
- Built-in monitoring with Grafana/Prometheus
- Easy backup and restore

### Traditional Installation
- Direct system installation
- Manual control over all components
- Lower resource overhead
- Advanced customization options

## Network Support

### PulseChain
- Chain ID: 943
- Native token: PLS
- Block time: 2 seconds
- Consensus: Proof of Stake

### Ethereum
- Chain ID: 1
- Native token: ETH
- Block time: 12 seconds
- Consensus: Proof of Stake

## Client Options

### Execution Clients
- Geth (Recommended)
- Nethermind

### Consensus Clients
- Prysm (Recommended)
- Lighthouse

## Monitoring & Management

Access your node's dashboard at http://localhost:3000 after installation.
- View sync status
- Monitor system resources
- Check client health
- View network statistics
- Track mempool metrics
- Monitor backup status

## Configuration

The setup process creates a comprehensive configuration file that can be managed through the configuration menu:
```bash
./setup.sh config
```

Available configuration options:
- Network selection
- Operation mode
- Client choices
- Port configurations
- Resource limits
- Monitoring options
- Backup settings
- Access controls
- Performance tuning

## Troubleshooting

If you encounter issues:
1. Check the logs: `docker-compose logs -f` (Docker) or `journalctl -u nodename` (Traditional)
2. Verify system requirements
3. Ensure ports are open (8545, 8546, 5052, 3000)
4. Check disk space and permissions
5. Review operation mode settings
6. Validate configuration file

## Support

- GitHub Issues: Report bugs and request features
- Documentation: Detailed guides in the `docs` directory
- Community: Join our Discord for support

## Contributing

We welcome contributions! Please see `CONTRIBUTING.md` for guidelines.

## Security

For security concerns, please see `SECURITY.md`.

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

## ⚠️ ALPHA RELEASE WARNING (v0.1.2) ⚠️

**This is an ALPHA release intended for testing and development purposes only.**

> This software is provided "as is" without warranty of any kind. Use at your own risk and always back up important data before testing.

This package has been specifically modified to **remove all validator functionality**. It cannot be used for validation or staking.

## ⚠️ Important Note on Network Selection

**You must choose EITHER PulseChain OR Ethereum for your node installation. Running both networks simultaneously is not supported.**

## 📋 Quick Summary

* **Purpose**: Setup and manage EITHER a PulseChain OR Ethereum full node (without validator functionality)
* **Network Choice**: Must select one network during installation - cannot run both simultaneously
* **Status**: Alpha release - may contain bugs or incomplete features
* **Recommended for**: Testing, development, and RPC endpoint provisioning
* **Not recommended for**: Production environments without thorough testing
* **Key components**: 
  - Execution clients (choose one network): 
    * PulseChain: Geth/Erigon
    * OR
    * Ethereum: Geth/Erigon
  - Consensus clients (choose one network):
    * PulseChain: Lighthouse/Prysm
    * OR
    * Ethereum: Lighthouse/Prysm
  - Monitoring: Prometheus/Grafana
* **Management**: Interactive menu system for node operations
* **Network Selection**: One-time choice between PulseChain and Ethereum
* **Network Optimization**: Switchable modes for local or public RPC usage
* **Robust Configuration**: JSON-based central configuration system for easy customization
* **Sync Recovery**: Advanced recovery mechanisms for blockchain synchronization issues

## 🏗️ System Architecture

The Node Suite follows a modular design with these key components:

1. **Main Setup Scripts**: 
   - `setup.sh` - Unified setup script that handles both networks
   - `setup_traditional.sh` - Traditional installation handler
   - `start-with-docker-compose.sh` - Docker Compose installation handler
2. **Helper Scripts**: Various scripts in the `helper/` directory provide specialized functionality
3. **Centralized Configuration**: JSON-based config system for easy management
4. **Menu Interface**: User-friendly management UI with network-specific options
5. **Monitoring Stack**: Prometheus and Grafana with custom dashboards
6. **Recovery Subsystems**: Smart restart and sync recovery mechanisms
7. **Health Management**: Automated resource monitoring with protective actions

This architecture ensures reliability through error detection, recovery mechanisms, and comprehensive logging throughout all operations.

## 🛠️ What This Package Does

* **Network Support**: 
  - Full PulseChain node setup and management
  - Full Ethereum node setup and management
  - Easy switching between networks
* **System Preparation**: Installs dependencies (Docker, system packages) and optimizes performance
* **Node Deployment**: Sets up execution and consensus clients as Docker containers
* **Configuration Management**: Manages node settings through a centralized system
* **Monitoring**: Deploys Prometheus and Grafana for performance monitoring
* **Health Management**: Checks node health with protection mechanisms for disk space, CPU, and memory
* **Failure Recovery**: Implements smart restart functionality for high availability
* **Sync Recovery**: Automatically detects and repairs blockchain synchronization issues
* **User Interface**: Provides intuitive menu system for all operations
* **Network Tuning**: Automatically optimizes network settings based on your usage scenario

## ❌ What This Package Does NOT Do

* **No Validator Functionality**: Cannot be used for staking or validation on either network
* **No Key Management**: Does not handle validator keys or deposits
* **No Staking Rewards**: Cannot earn rewards from validating blocks
* **No Validator Monitoring**: No validator performance metrics

## 💻 System Requirements

### General Requirements
* Ubuntu 20.04 LTS or newer
* At least 16GB RAM (32GB recommended)
* Stable internet connection (10Mbps+ upload/download)
* Modern CPU with 4+ cores

### Storage Requirements
* PulseChain Full Node: Minimum 2TB SSD (NVMe SSD recommended)
* Ethereum Full Node: Minimum 4TB SSD (NVMe SSD recommended)
* Archive Node (either network): Additional storage required

## 📥 Installation Options

### Option 1: Docker Compose (Recommended)

The setup script will automatically install Docker and Docker Compose if they're not present.

```bash
# One-command installation
curl -s https://raw.githubusercontent.com/MaximCincinnatis/PulseChain-Ethereum-Node-Suite/main/start-with-docker-compose.sh | sudo bash
```

Or if you prefer step by step:

```bash
# Clone the repository
git clone https://github.com/MaximCincinnatis/PulseChain-Ethereum-Node-Suite.git
cd PulseChain-Ethereum-Node-Suite

# Start the setup (will install Docker if needed)
./start-with-docker-compose.sh
```

The script will:
1. Install Docker and Docker Compose if not present
2. Guide you through network selection (PulseChain or Ethereum)
3. Set up your chosen client configuration
4. Start all services automatically

### Option 2: Traditional Installation

```bash
# One-command installation
curl -s https://raw.githubusercontent.com/MaximCincinnatis/PulseChain-Ethereum-Node-Suite/main/setup.sh | sudo bash
```

Or manually:

1. **Clone and Enter Directory**:
   ```bash
   git clone https://github.com/MaximCincinnatis/PulseChain-Ethereum-Node-Suite.git
   cd PulseChain-Ethereum-Node-Suite
   ```

2. **Run Setup**:
   ```bash
   ./setup.sh
   ```

The setup script will:
1. Install all required dependencies
2. Guide you through network selection
3. Configure your chosen clients
4. Set up monitoring

## 🔍 Key Features Explained

### 🧰 Node Management via `plsmenu`

The `plsmenu` command provides a central interface for all node operations:

```bash
plsmenu
```

This comprehensive menu system allows you to:
* Start/stop/restart nodes
* View detailed logs
* Update Docker images
* Monitor node status
* Configure client settings
* Manage system resources
* Recover from synchronization issues

### 🐳 Docker Container Management

#### Viewing Running Containers
```bash
docker ps
```

#### Viewing Logs
```bash
# View logs for execution client
docker logs -f --tail=50 execution

# View logs for consensus client
docker logs -f --tail=50 beacon
```

#### Stopping Containers Safely
```bash
cd /blockchain/helper
./stop_docker.sh
```

#### Starting Containers
```bash
cd /blockchain
./start_execution.sh
./start_consensus.sh
```

### ⚙️ Configuration Management

The node uses a centralized JSON configuration system that makes customization easy and consistent:

```bash
# View current configuration
cd /blockchain
./config.sh
```

This will show a menu that allows you to:
1. Show current configuration
2. Save configuration
3. Create default configuration

All settings are stored in `/blockchain/node_config.json` and can be manually edited or updated through the provided functions.

See the [Advanced Configuration Guide](docs/advanced_configuration.md) for detailed information about all available options.

### 🔄 Recovery Mechanisms

#### Smart Restart System

The smart restart system (`smart_restart.sh`) provides:
* Intelligent container management with proper shutdown sequences
* Visual progress indicators during operations
* Automatic detection of container status
* Proper error handling and logging

#### Sync Recovery Tool

The sync recovery system automatically detects and fixes blockchain synchronization issues:

```bash
# Run sync recovery tool
cd /blockchain/helper
./sync_recovery.sh --recover
```

This sophisticated tool:
- Detects synchronization problems using multiple indicators
- Diagnoses common issues (corrupt database, network problems)
- Performs appropriate recovery steps based on specific conditions
- Creates detailed logs of the recovery process
- Implements protections against repeated recovery attempts

You can also access this feature through the Info & Management menu in `plsmenu`.

### 📊 Monitoring with Prometheus & Grafana

After setup, access Grafana at:
```
http://YOUR_SERVER_IP:3000
```

Default login:
* Username: `admin`
* Password: `admin`

The monitoring system includes:
* Node performance metrics
* Blockchain synchronization status
* System resource utilization (CPU, memory, disk)
* Network connection statistics
* Customizable dashboards and alerts

### 🌐 Network Configuration

The node includes specialized network optimization with two modes:

#### Local Mode (Default)
```bash
# Switch to local mode
cd /blockchain/helper
./network_config.sh local
```
* Optimized for high-throughput between your machine and VMs
* Perfect for personal use, development, and testing
* Configured for maximum data transfer performance

#### Public Mode
```bash
# Switch to public mode
cd /blockchain/helper
./network_config.sh public
```
* Optimized for handling many external connections
* Ideal when exposing your node as a public RPC endpoint
* Includes protections against connection floods

You can also access network configuration through the menu:
```bash
plsmenu
# Navigate to: System Menu > Network Configuration
```

### 💽 VirtualBox Integration

The node includes enhanced VirtualBox Guest Additions support for better VM integration:

#### Automatic Installation

During setup, the script will:
- Detect if running in VirtualBox
- Download and install the correct Guest Additions version
- Configure clipboard sharing between host and VM
- Set up persistent clipboard service that survives reboots

#### Clipboard Management

Manage clipboard functionality through the menu:
```bash
plsmenu
# Navigate to: System Menu > VirtualBox Clipboard
```

This menu provides options to:
- Check clipboard functionality status
- Restart clipboard sharing if not working
- Test clipboard with sample text
- Install/update clipboard service

If copy-paste stops working after a reboot, use this menu to quickly restore functionality.

## 🔄 Updating the Node

Update Docker images using:
```bash
cd /blockchain/helper
sudo ./update_docker.sh
```

Or via the menu:
```bash
plsmenu
# Navigate to: Clients-Menu > Update all Clients
```

## 🚑 Troubleshooting Guide

### Common Issues and Solutions

| Issue | Possible Causes | Solution |
|-------|-----------------|----------|
| **Container not starting** | Disk space, port conflicts, database corruption | Check logs with `docker logs execution`, verify disk space, use recovery tool |
| **Sync issues** | Network problems, outdated software, database corruption | Run `./sync_recovery.sh --diagnose`, check firewall settings |
| **High resource usage** | Normal during initial sync, inefficient configuration | Monitor with Grafana, adjust client parameters in configuration |
| **Menu not working** | Permission issues, missing dependencies | Ensure helper scripts have execution permissions (`chmod +x`) |
| **Out of disk space** | Chain growth, logs accumulation | Use disk cleanup tools, consider pruned node option |
| **Poor performance** | Hardware limitations, network congestion | Check system resources, switch network configuration mode |

For additional troubleshooting assistance, check the `plsmenu` > Info & Management section, which includes diagnostic tools.

## 📚 Additional Resources

* PulseChain website: https://pulsechain.com/
* PulseChain GitLab: https://gitlab.com/pulsechaincom
* Checkpoint: https://checkpoint.pulsechain.com/
* Pulsedev Telegram: https://t.me/PulseDEV

## 📝 Release Notes

This alpha release (v0.1.2) represents the initial development version with:
* Core node functionality
* Monitoring capabilities
* Management tools
* Non-validator configuration
* Robust configuration and sync recovery

Expect future updates to improve stability, performance, and add features.

## ⚠️ Known Limitations

* Limited testing in production environments
* Some features may be incomplete
* Documentation is still developing
* Performance optimizations pending

## 📣 Feedback and Contributions

Feedback on this alpha release is welcome. Please report issues or suggestions through GitHub issues.

## 🐳 Docker Compose Management

### Basic Commands

```bash
# Start all services
docker-compose up -d

# Stop all services
docker-compose down

# View logs
docker-compose logs -f

# View specific service logs
docker-compose logs -f execution  # For execution client
docker-compose logs -f consensus  # For consensus client

# Check service status
docker-compose ps

# Restart specific service
docker-compose restart execution  # For execution client
docker-compose restart consensus  # For consensus client
```

### Configuration

The setup uses two main configuration files:

1. `.env`: Environment variables for customizing your setup
   ```ini
   # Network Selection
   NETWORK=pulsechain  # or ethereum

   # Client Selection
   EXECUTION_CLIENT=geth  # or erigon
   CONSENSUS_CLIENT=lighthouse  # or prysm

   # Resource Limits
   EXECUTION_CPU_LIMIT=4
   EXECUTION_MEMORY_LIMIT=8G
   ```

2. `docker-compose.yml`: Service definitions and container configurations

### Data Directories

Docker Compose setup uses the following directory structure:
```
PulseChain-Ethereum-Node-Suite/
├── data/                  # Main data directory
│   ├── execution/        # Execution client data
│   ├── consensus/        # Consensus client data
│   └── monitoring/       # Monitoring data
│       ├── prometheus/
│       └── grafana/
├── config/               # Client configurations
├── helper/              # Helper scripts
│   ├── updates/        # Update management
│   └── troubleshoot.sh # Troubleshooting tools
├── docs/                # Documentation
├── setup.sh            # Main setup script
├── setup_traditional.sh # Traditional installation
├── start-with-docker-compose.sh # Docker installation
├── docker-compose.yml  # Docker services config
└── .env.example       # Environment template
```

### Monitoring

The Docker Compose setup includes:
- Prometheus for metrics collection
- Grafana for visualization
- Pre-configured dashboards for node monitoring

Access the monitoring dashboard at http://localhost:3000 with:
- Username: admin
- Password: admin
