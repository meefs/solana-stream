<p align="center">
  <a href="https://slv.dev/" target="_blank">
    <img src="https://storage.validators.solutions/SolanaStreamSDK.jpg" alt="SolanaStreamSDK" />
  </a>
  <a href="https://twitter.com/intent/follow?screen_name=ValidatorsDAO" target="_blank">
    <img src="https://img.shields.io/twitter/follow/ValidatorsDAO.svg?label=Follow%20@ValidatorsDAO" alt="Follow @ValidatorsDAO" />
  </a>
  <a href="https://www.npmjs.com/package/@validators-dao/solana-stream-sdk">
    <img alt="NPM Version" src="https://img.shields.io/npm/v/@validators-dao/solana-stream-sdk?color=268bd2&label=version&logo=npm">
  </a>
  <a href="https://www.npmjs.com/package/@validators-dao/solana-stream-sdk">
    <img alt="NPM Downloads" src="https://img.shields.io/npm/dt/@validators-dao/solana-stream-sdk?color=cb4b16&label=npm%20downloads">
  </a>
  <a aria-label="License" href="https://github.com/ValidatorsDAO/solana-stream/blob/main/LICENSE.txt">
    <img alt="" src="https://badgen.net/badge/license/Apache/blue">
  </a>
  <a aria-label="Code of Conduct" href="https://github.com/ValidatorsDAO/solana-stream/blob/main/CODE_OF_CONDUCT.md">
    <img alt="" src="https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg">
  </a>
</p>

# @validators-dao/solana-shreds-client

Solana Shreds Client for Scale.

<a href="https://solana.com/">
  <img src="https://storage.slv.dev/PoweredBySolana.svg" alt="Powered By Solana" width="200px" height="95px">
</a>

## Why Rust?

TypeScript alone cannot decode Solana shreds effectively. Therefore, Rust is utilized for efficient decoding, converting the data into JSON format suitable for handling in TypeScript environments.

## Leveraging NAPI instead of WASM

This utility leverages **NAPI (Node-API)** instead of WebAssembly (WASM) to decode Solana shred entry data, providing significant practical advantages.

Node-API - Node.js: https://nodejs.org/api/n-api.html#node-api

### Benefits of Using NAPI:

- **Performance**: NAPI delivers near-native performance by directly interfacing with Rust code through bindings, minimizing overhead compared to WebAssembly.

- **Seamless Integration**: NAPI simplifies the interoperation between Node.js and Rust, enabling straightforward calls and efficient memory management without extensive tooling or additional complexity.

- **Memory Efficiency**: Efficient memory handling with NAPI significantly reduces risks associated with memory leaks or unnecessary garbage collection, common pitfalls when using WASM.

- **Enhanced Debugging and Maintainability**: Debugging native modules built with NAPI offers clearer stack traces and robust debugging capabilities, overcoming the opaque debugging difficulties often encountered with WASM.

- **Wide Compatibility**: Modules built with NAPI are natively compatible across various Node.js versions without requiring extra compilation steps or environment-specific adjustments.

## Installation

```bash
npm install @validators-dao/solana-shreds-client
```

Or using pnpm:

```bash
pnpm add @validators-dao/solana-shreds-client
```

## Usage

### Direct Usage (Node.js ES Modules)

To directly import this package, you'll need to use the Node.js `require` function:

```typescript
import { createRequire } from 'node:module'
const require = createRequire(import.meta.url)
const { ShredsClient } = require('@validators-dao/solana-shreds-client')
```

### Recommended Usage

For TypeScript projects, it's recommended to import directly from [Solana Stream SDK](https://www.npmjs.com/package/@validators-dao/solana-stream-sdk), which exports the decoder in a more convenient way:

```bash
pnpm add @validators-dao/solana-stream-sdk
```

```typescript
import { ShredsClient } from '@validators-dao/solana-stream-sdk'
```

You can find comprehensive usage examples [here](https://github.com/ValidatorsDAO/solana-stream/tree/main/client/shreds-ts).

## Multi-Platform Build

To build binaries for multiple platforms (cross-compilation), you must first install Rust targets for each desired OS and architecture. Execute the following commands once on your machine to enable cross-platform builds:

```
rustup target add x86_64-unknown-linux-gnu      # Linux x64
rustup target add aarch64-unknown-linux-gnu     # Linux ARM64
rustup target add aarch64-apple-darwin          # macOS ARM64 (Apple Silicon)
rustup target add x86_64-apple-darwin           # macOS x64 (Intel)
```

Here's a concise README section in English that clearly states this is for macOS specifically:

### Cross-compilation for Linux (macOS)

On macOS, to cross-compile for Linux targets (`x86_64-unknown-linux-gnu`, `aarch64-unknown-linux-gnu`), you must install the following toolchains:

```bash
brew tap messense/macos-cross-toolchains
brew install x86_64-unknown-linux-gnu aarch64-unknown-linux-gnu zig protobuf
```

### For Windows Users

For now please use WSL2 and follow the Linux instructions.

## Build packages

```bash
pnpm i
pnpm build

// or from the root of the monorepo
pnpm -F @validators-dao/solana-shreds-client build
```

## Repository

This utility is part of the [Solana Stream Monorepo](https://github.com/ValidatorsDAO/solana-stream).

## Support

For support and further questions, please join our [Discord server](https://discord.gg/C7ZQSrCkYR).

## License

Apache-2.0 License. Refer to the [license document](https://www.apache.org/licenses/LICENSE-2.0).

## Code of Conduct

All contributors must adhere to our [Contributor Covenant](https://github.com/ValidatorsDAO/solana-stream/blob/main/CODE_OF_CONDUCT.md).
