# 🌐 NetPractice - TCP/IP Network Configuration Training

> **A hands-on networking project to master TCP/IP addressing and small-scale network configuration through 10 progressively challenging levels.**

## 📋 Table of Contents

- [About](#about)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Levels Overview](#levels-overview)
- [Key Concepts](#key-concepts)
- [Commands & Workflow](#commands--workflow)
- [Troubleshooting](#troubleshooting)
- [Deployment](#deployment)
- [Contributing](#contributing)

## 🎯 About

NetPractice is a comprehensive networking training project designed to teach TCP/IP addressing fundamentals through practical exercises. You'll configure small-scale networks by solving 10 progressively challenging levels, each presenting a non-functional network diagram that needs proper configuration.

### 🚀 What You'll Learn

- **TCP/IP Addressing**: Subnetting, CIDR notation, and IP allocation
- **Network Routing**: Default routes, static routes, and routing tables
- **Subnet Masks**: Understanding network boundaries and host ranges
- **Network Troubleshooting**: Reading logs and diagnosing connectivity issues
- **Router Configuration**: Setting up routing between different network segments

## 📚 Prerequisites

### Knowledge Requirements
- Basic understanding of computer networks
- Familiarity with IP addresses and subnetting concepts
- Command line basics (helpful but not required)

### System Requirements
- Modern web browser (Chrome, Firefox, Safari, or Edge)
- Git (for version control and submission)
- Text editor or IDE for viewing configuration files

## 🛠 Installation

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd net_practice
```

### 2. Download the Training Interface
According to the project instructions:
1. Download the NetPractice file from your project page
2. Extract the files to any folder
3. Open the `index.html` file in your web browser

### 3. Verify Installation
```bash
# Check that you have all level files
ls level*.json
# Should show: level1.json level2.json ... level10.json
```

## 🎮 Usage

### Starting the Training Interface

1. **Open the Interface**: Launch `index.html` in your web browser
2. **Choose Practice Mode**:
   - Enter your login for personalized practice
   - Leave empty for 'correction' version
3. **Select Level**: Start with Level 1 and progress sequentially

### Working Through Levels

Each level presents:
- 🎯 **Goal**: Specific networking objective to achieve
- 🖼️ **Network Diagram**: Visual representation of the network
- ⚙️ **Configurable Fields**: Unshaded areas you can modify
- 📊 **Logs**: Real-time feedback on your configuration

### Interface Controls

| Button | Function |
|--------|----------|
| `[Check again]` | Validate your current configuration |
| `[Get my config]` | Download your solution as JSON |
| `[Next Level]` | Proceed after successful completion |

## 📁 Project Structure

```
net_practice/
├── README.md           # This documentation
├── level1.json         # Level 1 configuration
├── level2.json         # Level 2 configuration
├── ...                 # Levels 3-9
└── level10.json        # Level 10 configuration
```

### Configuration File Format

Each `levelX.json` contains:
```json
{
  "routes": {
    "device_route_id": {
      "route": "network/prefix",
      "gate": "gateway_ip"
    }
  },
  "ifs": {
    "interface_id": {
      "ip": "ip_address",
      "mask": "subnet_mask"
    }
  }
}
```

## 🎓 Levels Overview

| Level | Difficulty | Focus Area |
|-------|------------|------------|
| 1-2   | 🟢 Beginner | Basic IP assignment and subnet masks |
| 3-4   | 🟡 Easy | Simple routing between networks |
| 5-6   | 🟠 Intermediate | Complex subnetting and VLSM |
| 7-8   | 🔴 Advanced | Multi-router configurations |
| 9-10  | 🟣 Expert | Complex routing scenarios |

### ⭐ Level Progression Tips

1. **Level 1-2**: Focus on understanding IP addresses and subnet masks
2. **Level 3-4**: Learn basic routing concepts and default gateways
3. **Level 5-6**: Master subnetting and variable-length subnet masks
4. **Level 7-8**: Configure complex multi-router topologies
5. **Level 9-10**: Solve advanced routing and addressing challenges

## 🧠 Key Concepts

### IP Addressing
```
192.168.1.0/24
│       │  │ └─ CIDR notation (24 bits for network)
│       │  └─── Network address
│       └────── Private IP range
└─────────────── IPv4 address format
```

### Subnet Masks
| CIDR | Subnet Mask | Hosts | Use Case |
|------|-------------|-------|----------|
| /24  | 255.255.255.0 | 254 | Standard LAN |
| /25  | 255.255.255.128 | 126 | Small office |
| /26  | 255.255.255.192 | 62 | Department |
| /27  | 255.255.255.224 | 30 | Small team |
| /30  | 255.255.255.252 | 2 | Point-to-point |

### Routing Fundamentals
- **Default Route**: `0.0.0.0/0` - catches all unmatched traffic
- **Static Route**: Manually configured path to specific networks
- **Gateway**: Router interface that forwards traffic between networks

## ⚡ Commands & Workflow

### Basic Workflow
```bash
# 1. Start working on a level
# Open index.html → Select level → Configure network

# 2. Export your solution
# Click [Get my config] → Save as levelX.json

# 3. Commit your progress
git add levelX.json
git commit -m "Complete level X: [brief description]"

# 4. Push to repository
git push origin main
```

### Validation Commands
```bash
# Check JSON syntax
python -m json.tool level1.json

# View configuration structure
cat level1.json | jq '.'

# Compare levels
diff level1.json level2.json
```

### Development Helpers
```bash
# Create backup before major changes
cp level5.json level5.json.backup

# Quick level status check
for f in level*.json; do echo "$f: $(wc -c < "$f") bytes"; done
```

## 🔧 Troubleshooting

### Common Issues

#### ❌ "Network not reachable"
- **Cause**: Incorrect routing configuration
- **Solution**: Check default routes and gateway addresses
- **Debug**: Verify that all networks have paths to destinations

#### ❌ "IP conflict detected"
- **Cause**: Duplicate IP addresses in same subnet
- **Solution**: Assign unique IPs within each network segment
- **Debug**: List all IP assignments and check for duplicates

#### ❌ "Subnet mask mismatch"
- **Cause**: Inconsistent masks within same network
- **Solution**: Ensure all devices in same network use same mask
- **Debug**: Compare mask values across connected interfaces

### Debugging Strategies

1. **Start Simple**: Configure basic connectivity first
2. **Check Logs**: Use browser console and NetPractice logs
3. **Verify Subnets**: Ensure IPs are in correct network ranges
4. **Test Incrementally**: Add one route/interface at a time
5. **Use Default Routes**: Often simpler than specific routes

### Log Analysis
```
✅ Host A can reach Host B
❌ No route to network 192.168.2.0/24
❌ Interface mismatch: expected /24, got /25
```

## 🚀 Deployment

### Submission Requirements

1. **Complete All Levels**: Solve levels 1-10 successfully
2. **Export Configurations**: Use `[Get my config]` for each level
3. **Organize Files**: Ensure proper naming (`level1.json`, `level2.json`, etc.)
4. **Git Repository**: Submit via your assigned Git repository

## 📖 Additional Resources

### Learning Materials
- **Subnetting Practice**: [SubnetMentor](https://subnetmentor.com)
- **CIDR Calculator**: [CIDR.xyz](https://cidr.xyz)
- **Routing Concepts**: Cisco Networking Academy
- **TCP/IP Guide**: [The TCP/IP Guide](http://tcpipguide.com)

### Quick Reference
- **RFC 1918**: Private IP address ranges
- **RFC 950**: Internet Standard Subnetting Procedure
- **IPv4 Calculator**: For subnet planning and validation

If you encounter issues:

1. **Check the logs** in the NetPractice interface
2. **Review your subnet calculations** for mathematical errors
3. **Verify routing paths** step by step
4. **Compare with working levels** to identify patterns

**Good luck with your networking journey! 🎉**

> *Remember: Networking mastery comes through practice. Take your time with each level and understand the underlying concepts rather than just finding solutions.*
