---
kip: 6
title: "gasleft" Host Function for pWASM
author: Nikolay Volf (@NikVolf)
discussions-to: -
status: Draft
type: Standards Track
category: Core
created: 2018-08-17
---

# GASLEFT Host Function for pWASM

## Motivation

For default calls with no gas costs specifed downstream, user code now cannot infer how much gas left in the current context of execution. Proposed "gasleft" extern will allow this. 

## Specification

After `9200000`, allow a new function to be imported from module "env" with the name "gasleft".

```
fn gasleft() -> i64;
```

This function will return gas left in the current execution context (non-adjusted for Wasm, since the following call destination might be EVM or Wasm)   

## Implementation

To be added.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
