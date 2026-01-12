# Uniswap V3 Protocol

A simplified repository containing the core and periphery smart contracts for the Uniswap V3 protocol.

## Overview

This project integrates the fundamental logic of the Uniswap V3 automated market maker (AMM) with its user-facing interfaces:

- **Core (`contracts/`)**: Implements the base protocol logic, including the `UniswapV3Factory` and `UniswapV3Pool`.
- **Periphery (`contracts-periphery/`)**: Provides optimized interfaces for trading and liquidity management, including the `SwapRouter` and `NonfungiblePositionManager` (Fluxion Positions NFT).

## Key Features

- **Concentrated Liquidity**: Efficient capital allocation within specific price ranges.
- **Customizable Fees**: Multiple fee tiers for various asset pairs.
- **NFT Positions**: Liquidity positions represented as ERC-721 tokens.

## Resources

- [Official Documentation](https://docs.uniswap.org/)
- [Fluxion Network Docs](https://hospitable-shaker-7f9.notion.site/Fluxion-Network-All-in-One-Doc-2a7bf5c396018023b5deffbe5065e163)
- [Original Core Repository](https://github.com/Uniswap/uniswap-v3-core)
- [Original Periphery Repository](https://github.com/Uniswap/uniswap-v3-periphery)

## License

GPL-3.0-or-later. See individual files for details.
