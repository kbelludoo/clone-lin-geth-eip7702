# clone-lin-geth-eip7702

LIN clone of go-ethereum `makeCallVariantGasCallEIP7702` / `ParseDelegation` (tag `v1.16.9`, LGPL-3.0).

This repository holds **only the LIN kernel**. Auditable proofs live in [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open):

- kernel (also mirrored): `src/lin_geth_eip7702.lin`
- harness: `test/prove_geth_eip7702_external.py`
- evidence: `examples/geth_eip7702/`
- event: `docs/events/EVENT_GETH_EIP7702_CLONE_LIN.rulel`

Class: **EXPERIMENTAL** (real Pectra 7702 addends, i64-scale). Not a Geth node. Not uint256 / mainnet parity.

Commercial hook (honest): a fee estimator that prices a 7702 delegated CALL as a 2929 CALL is wrong. The extra `100` (warm target) or `2600` (full cold, not 2500) is charged **before** EIP-150 63/64, so a 64000-gas 63/64-bound CALL is **+2 / +41**, while a requested-bound CALL adds the full 2600.

Upstream: [ethereum/go-ethereum](https://github.com/ethereum/go-ethereum) commit `95665d5703e1023995a0ff93e4ce9eb77e8a59bd`
`core/vm/operations_acl.go` blob `085b018e4c42bf0185da790518ea1d1ee891b682` sha256 `213f7846ed039c8ab293eb9511383897497f52c971da014317d3e1b5b5dc5330`
`core/types/tx_setcode.go` blob `f2281d4ae7662b9ab3def885e4e460867f1d25cd` sha256 `b9ba5d2fbbfa5a1a46e9edd7d00cbb6f0b651599da555744ece0f071f99273d6`
