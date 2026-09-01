# Guillotrise blockchain information

Snapshot taken on 2026-09-01 at Ethereum block `25,880,017`.

## Canonical token identity

| Field | On-chain value |
| --- | --- |
| Network | Ethereum Mainnet |
| Chain ID | `1` |
| Contract | `0x9b073d8252f5e600952de2a4e8d81021598ae580` |
| Name | `Guillotrise` |
| Symbol | `Guill` |
| Decimals | `18` |
| ERC standard | ERC-20 |
| Initial raw supply | `10000000000000000000000000000000` |
| Initial display supply | `10,000,000,000,000 Guill` |
| Current display supply | `10,000,000,000,000 Guill` |
| Zero-address balance | `0 Guill` |
| Proxy | No |

The symbol is case-sensitive: the contract returns `Guill`, not `GUILL`.

## Deployment

| Field | Value |
| --- | --- |
| Block | `16027026` |
| Timestamp | `2022-11-22T17:26:47Z` |
| Transaction | `0x381272314139ee47a484b03bb9e0f26db753d33a2093fed92ee41c14cc6655f0` |
| Deployer | `0x9674F709F20699a92AeDce7C3aC3ce6a19568Aec` |

The constructor assigned the complete initial supply to the deployer.

## Verification and build information

Sourcify currently reports a verified `match` for both creation and runtime bytecode. It is not recorded as an `exact_match`.

| Field | Value |
| --- | --- |
| Sourcify verification date | `2025-06-23T10:23:59Z` |
| Source file | `CodeWithJoe.sol` |
| Contract name | `CodeWithJoe` |
| Language | Solidity |
| Compiler | `0.5.0+commit.1d4f565a` |
| Optimizer | Disabled |
| Proxy detected | No |

## Contract capabilities

The verified ABI exposes the standard ERC-20 balance, allowance, approval, and transfer operations. It also exposes four pure arithmetic helpers and the raw `_totalSupply()` getter.

The deployed contract does **not** expose:

- an owner or administrator role;
- minting;
- pausing;
- blacklisting;
- transfer taxes;
- configurable fees;
- upgrade or proxy controls;
- EIP-2612 permit signatures.

This makes the deployed supply and behavior comparatively simple and immutable. It also means features cannot be added to this address; material feature changes would require a separate contract and a documented migration.

### Burn behavior

The contract has no named `burn()` function. It permits transfers to the zero address, and `totalSupply()` subtracts the zero-address balance from the original supply. A transfer to the zero address therefore functions as an irreversible burn and reduces the reported supply.

### Approval caution

The contract uses the original ERC-20 allowance replacement pattern. When changing an existing non-zero allowance, users should first approve `0`, wait for confirmation, and then approve the new amount. Modern interfaces should enforce this sequence.

## Discovered GUILL/WETH liquidity pools

WETH contract: `0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2`.

| Venue | Pair address | GUILL reserve | WETH reserve |
| --- | --- | ---: | ---: |
| SushiSwap V2 | `0x5bBc66A66DcE972d1F568497879543F44c350bC3` | `0.001877402668914362` | `0.000012045696434311` |
| Uniswap V2 | `0xaB265Daaa54ac1C72ab698518400AA046174a27A` | `0.000706607654619603` | `0.000008242093131876` |
| **Combined** | — | **`0.002584010323533965`** | **`0.000020287789566187`** |

These reserves are dust-sized. Ratios produced by the pools should not be treated as a reliable token price, market capitalization, or executable price for a meaningful trade. Improving liquidity should begin with a documented treasury policy, source-of-funds records, clear pool selection, and public reporting of deposits and LP-token custody.

## Primary evidence

- [Etherscan contract](https://etherscan.io/address/0x9b073d8252f5e600952de2a4e8d81021598ae580)
- [Etherscan token tracker](https://etherscan.io/token/0x9b073d8252f5e600952de2a4e8d81021598ae580)
- [Deployment transaction](https://etherscan.io/tx/0x381272314139ee47a484b03bb9e0f26db753d33a2093fed92ee41c14cc6655f0)
- [Sourcify verification record](https://repo.sourcify.dev/1/0x9b073d8252F5E600952De2A4E8d81021598AE580)
- [SushiSwap pair](https://etherscan.io/address/0x5bbc66a66dce972d1f568497879543f44c350bc3)
- [Uniswap V2 pair](https://etherscan.io/address/0xab265daaa54ac1c72ab698518400aa046174a27a)

## Interpretation status

This is an initial technical snapshot, not a completed security audit. Holder distribution, transfer history, LP-token ownership, source licensing, and bytecode-level security findings remain to be documented.
