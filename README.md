# Soroban Project

## Project Structure

```❯ tree
 .
├──  Cargo.lock
├──  Cargo.toml
├──  contracts
│   ├──  contract_a
│   │   ├──  Cargo.toml
│   │   ├──  Makefile
│   │   └── 󱧼 src
│   └──  contract_b
│       ├──  Cargo.toml
│       ├──  Makefile
│       ├── 󱧼 src
│       └──  test_snapshots
├──  README.md
└──  target
    ├──  CACHEDIR.TAG
    ├──  debug
    │   ├──  build
    │   ├──  deps
    │   ├──  examples
    │   └──  incremental
    ├──  release
    │   ├──  build
    │   ├──  deps
    │   ├──  examples
    │   └──  incremental
    └──  wasm32-unknown-unknown
        ├──  CACHEDIR.TAG
        └──  release
```

```
❯ stellar contract deploy \
    --wasm ../target/wasm32-unknown-unknown/release/contract_a.wasm \
    --source-account alice \
    --network testnet
ℹ️ Skipping install because wasm already installed
ℹ️ Using wasm hash 2536f851f7d0a23e445217109cb48b7d1c15b4a4982b94cea3896469a1609f6c
ℹ️ Simulating deploy transaction…
🌎 Submitting deploy transaction…
ℹ️ Transaction hash is a7fe9e129d67c824b9ac1fe16131be4d51bcc3a70ed207b6742488ab566026e7
🔗 https://stellar.expert/explorer/testnet/tx/a7fe9e129d67c824b9ac1fe16131be4d51bcc3a70ed207b6742488ab566026e7
ℹ️ Signing transaction: a7fe9e129d67c824b9ac1fe16131be4d51bcc3a70ed207b6742488ab566026e7
🔗 https://stellar.expert/explorer/testnet/contract/CBQDCYTDXK7DQMVPOCEV6A5ZPJ2OOJS23C7BBTHO6ZVD4XLF6RBBYRNT
✅ Deployed!
CBQDCYTDXK7DQMVPOCEV6A5ZPJ2OOJS23C7BBTHO6ZVD4XLF6RBBYRNT
❯ stellar contract deploy \
    --wasm ../target/wasm32-unknown-unknown/release/contract_b.wasm \
    --source-account alice \
    --network testnet
ℹ️ Skipping install because wasm already installed
ℹ️ Using wasm hash 0266d88d5e2731c692bfcffcae7f4a9718b8baec3c056de0f7463090813c5768
ℹ️ Simulating deploy transaction…
🌎 Submitting deploy transaction…
ℹ️ Transaction hash is c18a03274b6caaa707dbfe9db57e8db66a5ab7b3ce96146d4ca7f7142b979062
🔗 https://stellar.expert/explorer/testnet/tx/c18a03274b6caaa707dbfe9db57e8db66a5ab7b3ce96146d4ca7f7142b979062
ℹ️ Signing transaction: c18a03274b6caaa707dbfe9db57e8db66a5ab7b3ce96146d4ca7f7142b979062
🔗 https://stellar.expert/explorer/testnet/contract/CABHUYMZYHPVBW3UD7LA7DOUXWDXPHKMR3STYU3KTW6FJDTJPPUJZCXX
✅ Deployed!
CABHUYMZYHPVBW3UD7LA7DOUXWDXPHKMR3STYU3KTW6FJDTJPPUJZCXX
dev@dev ~/rust/cross_contract/contracts main 7s
```

```
stellar contract invoke \
    --id CABHUYMZYHPVBW3UD7LA7DOUXWDXPHKMR3STYU3KTW6FJDTJPPUJZCXX \
    --network testnet \
    --source-account alice \
    --send=yes \
    -- \
    add_with \
    --contract CBQDCYTDXK7DQMVPOCEV6A5ZPJ2OOJS23C7BBTHO6ZVD4XLF6RBBYRNT \
    --x 5 \
    --y 7
```

```
❯ stellar contract invoke \
    --id CABHUYMZYHPVBW3UD7LA7DOUXWDXPHKMR3STYU3KTW6FJDTJPPUJZCXX \
    --network testnet \
    --source-account alice \
    --send=yes \
    -- \
    add_with \
    --contract CBQDCYTDXK7DQMVPOCEV6A5ZPJ2OOJS23C7BBTHO6ZVD4XLF6RBBYRNT \
    --x 5 \
    --y 7
ℹ️ Signing transaction: d294ec580c5705d9ef5b8f22784bdb098275b6f003484ab83e84c5246779ce32
12
```
