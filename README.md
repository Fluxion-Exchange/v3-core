# Uniswap V3 Core Contracts

## Overview

Uniswap V3 Core is the foundational smart contract system for the Uniswap V3 automated market maker (AMM) protocol. This repository contains the core Solidity contracts that implement the decentralized exchange functionality, enabling permissionless token swaps with concentrated liquidity positions.

The core contracts provide the essential building blocks for Uniswap V3, including factory deployment, pool management, and mathematical libraries for price calculations and liquidity management.

## Key Features

- **Concentrated Liquidity**: Liquidity providers can allocate capital within specific price ranges, improving capital efficiency
- **Customizable Fees**: Pools support different fee tiers (0.01%, 0.05%, 0.30%, 1.00%) for various trading pairs
- **Non-Fungible Liquidity Positions**: LP positions are represented as ERC-721 tokens
- **Flash Swaps**: Enable arbitrage and liquidation without upfront capital
- **Optimized Gas Usage**: Efficient data structures and algorithms minimize transaction costs

## Architecture

### Core Contracts

#### UniswapV3Factory.sol
The factory contract responsible for:
- Deploying new Uniswap V3 pools
- Managing pool parameters (fee tiers, tick spacing)
- Maintaining a registry of all deployed pools

#### UniswapV3Pool.sol
The main pool contract that handles:
- Liquidity provision and removal
- Token swaps
- Price oracle functionality
- Fee collection and distribution

#### UniswapV3PoolDeployer.sol
Utility contract for deterministic pool deployment addresses.

#### NoDelegateCall.sol
Security modifier to prevent delegatecall attacks.

### Interfaces

The `contracts/interfaces/` directory contains all public interfaces:

- **Pool Interfaces**: Define core pool functionality (`IUniswapV3Pool.sol`, `IUniswapV3PoolActions.sol`, etc.)
- **Factory Interface**: `IUniswapV3Factory.sol`
- **Callback Interfaces**: For flash loans, mints, and swaps
- **ERC20 Minimal**: Simplified ERC20 interface for token interactions

### Libraries

The `contracts/libraries/` directory includes mathematical and utility libraries:

- **Math Libraries**: `FullMath.sol`, `SqrtPriceMath.sol`, `SwapMath.sol` for precise calculations
- **Position Management**: `Position.sol` for liquidity position tracking
- **Tick System**: `Tick.sol`, `TickBitmap.sol`, `TickMath.sol` for price range management
- **Safety Libraries**: `SafeCast.sol`, `LowGasSafeMath.sol` for secure operations

## Usage

### Deploying a Pool

1. Deploy the `UniswapV3Factory` contract
2. Call `createPool(tokenA, tokenB, fee)` to deploy a new pool
3. Initialize the pool with `initialize(sqrtPriceX96)`

### Adding Liquidity

1. Mint a position by calling `mint()` on the pool contract
2. Specify tick range and liquidity amount
3. Receive an ERC-721 NFT representing the position

### Swapping Tokens

Call `swap()` on the pool contract with:
- ZeroForOne: direction of swap
- AmountSpecified: input/output amount
- SqrtPriceLimitX96: price limit

## Security Considerations

- All contracts have been audited by Trail of Bits and ABDK
- Use only with tokens that follow ERC-20 standards (no fee-on-transfer)
- Monitor for reentrancy and flash loan vulnerabilities
- Test thoroughly on testnets before mainnet deployment

## Development

This repository contains only the core contracts. For a full development environment including tests and tooling, see the [original Uniswap V3 Core repository](https://github.com/Uniswap/uniswap-v3-core).

### Prerequisites

- Solidity ^0.7.6
- Compatible EVM (Ethereum mainnet or testnets)

### Building

```bash
# Compile contracts
solc contracts/*.sol --bin --abi --optimize -o build/
```

## Contributing

This is a minimal core contracts repository. For contributions to the full Uniswap V3 ecosystem, please refer to the main Uniswap repositories.

## License

This software is licensed under the GPL-3.0-or-later license. See individual contract files for specific licensing.

## Resources

- [Uniswap V3 Documentation](https://docs.uniswap.org/)
- [Original Repository](https://github.com/Uniswap/uniswap-v3-core)
- [Fluxion Network Documentation](https://hospitable-shaker-7f9.notion.site/Fluxion-Network-All-in-One-Doc-2a7bf5c396018023b5deffbe5065e163?source=copy_link) - Referenced for comprehensive documentation structure
