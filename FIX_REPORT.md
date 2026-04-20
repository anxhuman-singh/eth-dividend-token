
### What `Token.sol` adds (the real behavior)

`Token.sol` adds the actual working token logic:

- `allowance/approve/transfer/transferFrom`: keeps track of who is allowed to spend tokens on someone else’s behalf, and moves balances.
- `mint`: lets a user send ETH to the contract and receive the same amount of tokens.
- `burn`: destroys the caller’s tokens and sends the same amount of ETH out to a destination address.
- Holder tracking (`holders`, `isHolder`, `_addHolder`, `_removeHolder`): keeps a list of addresses that currently hold tokens, so dividends can be split.
- Dividends (`recordDividend`, `dividends`, `getWithdrawableDividend`, `withdrawDividend`): lets someone deposit ETH as a “dividend pool”, splits it proportionally across current holders, and lets holders withdraw later.