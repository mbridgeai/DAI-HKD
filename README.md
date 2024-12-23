# HKD Stable Token (HKDST)

HKDST is a decentralized stablecoin pegged to the Hong Kong Dollar (HKD) and backed by DAI. It provides a trustless and transparent way to transact in HKD on the blockchain, with dynamic price adjustments based on Chainlink oracle feeds.

## Features

- 🔗 Fully decentralized stablecoin pegged to HKD
- 💱 Dynamic price adjustment using Chainlink oracles
- 🏦 Backed by DAI with transparent, on-chain reserves
- 🔒 Secure minting and redemption mechanisms
- 🤝 No centralized intervention required

## Technical Architecture

### Smart Contracts

The core smart contract (`HKDStableToken.sol`) inherits from:
- `ERC20`: Standard token implementation
- `Ownable`: Access control for admin functions
- `ReentrancyGuard`: Protection against reentrancy attacks

### Prerequisites

- Node.js >= 14
- Hardhat
- OpenZeppelin Contracts
- Chainlink Contracts

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/hkdst.git
cd hkdst
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file:
```
PRIVATE_KEY=your_private_key
INFURA_API_KEY=your_infura_key
ETHERSCAN_API_KEY=your_etherscan_key
```

### Contract Deployment

1. Compile the contracts:
```bash
npx hardhat compile
```

2. Deploy to network:
```bash
npx hardhat run scripts/deploy.js --network <network_name>
```

Replace `<network_name>` with your target network (mainnet, goerli, etc.).

## Usage

### Minting HKDST

To mint HKDST tokens:

1. Approve DAI spending:
```solidity
dai.approve(hkdstAddress, amount);
```

2. Mint HKDST:
```solidity
hkdst.mint(daiAmount);
```

### Redeeming HKDST

To redeem HKDST for DAI:

```solidity
hkdst.redeem(hkdstAmount);
```

### Price Feeds

The contract uses Chainlink price feeds for HKD/USD rates. Current oracle addresses:
- Mainnet: `0x...` (TBD)
- Goerli: `0x...` (TBD)

## Smart Contract Interface

### Core Functions

```solidity
function mint(uint256 daiAmount) external
function redeem(uint256 hkdstAmount) external
function getLatestHKDUSDPrice() public view returns (uint256)
function calculateHKDSTAmount(uint256 daiAmount) public view returns (uint256)
function calculateDAIAmount(uint256 hkdstAmount) public view returns (uint256)
```

### Admin Functions

```solidity
function withdrawExcessReserves(uint256 amount) external onlyOwner
```

## Testing

Run the test suite:

```bash
npx hardhat test
```

## Security

- Smart contract audited by [Audit Firm] (Report: TBD)
- All functions include reentrancy protection
- Real-time price feeds from Chainlink ensure accurate pegging
- Reserve ratio maintained and verified on-chain

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Contact

- Website: [hkdst.io](https://hkdst.io)
- Twitter: [@hkdst](https://twitter.com/hkdst)
- Email: contact@hkdst.io

## Acknowledgments

- OpenZeppelin for secure smart contract implementations
- Chainlink for reliable price feeds
- MakerDAO for DAI implementation
