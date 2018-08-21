---
kip: 4
title: create2 Host Function for pWASM
author: Wei Tang (@sorpaas)
discussions-to: https://github.com/kovan-testnet/KIPs/issues/5
status: Draft
type: Standards Track
category: Core
created: 2018-07-18
---

# create2 Host Function for pWASM

## Motivation

In current Kovan testnet, the `create` host function allows new contracts to be created from existing contracts. A new contract's addressed is calculated as the Keccak256 hash of 20-byte sender and 32-byte init code hash. The issue with this is that in a contract's whole lifetime, it will not be able to deploy mutliple new contracts with the same init code. This KIP proposes to add a new host function `create2` that calculates the new contract's address from combination of sender, salt, and code hash.

## Specification

After `FORK_BLOCK`, allow a new function to be imported via `env`.

```
fn create2(endowment: *const u8, salt: *const u8, code_ptr: *const u8, code_len: u32, result_ptr: *mut u8) -> i32;
```

This function is the same as `create`, except that the contract creation address is changed to:

* Read a 32-byte value located in memory at `salt`.
* Calculate the contract address as `keccak256(sender_address + salt + code_hash)`.

## Implementation

To be added.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
