# ETH Dividend Token

A Solidity-based ERC20 token that wraps ETH and supports on-chain dividend distribution to token holders.

## 🚀 Overview

This project implements a token system where:
- Users deposit ETH to mint tokens (1:1 ratio)
- Tokens can be burned to redeem ETH
- ETH dividends can be distributed proportionally to token holders

The contract maintains an internal list of token holders to enable dividend distribution via iteration.

---

## ⚙️ Features

- 🔁 ETH ↔ Token Conversion
  - `mint()` — deposit ETH and receive tokens
  - `burn()` — burn tokens to redeem ETH

- 💸 Dividend Distribution
  - `recordDividend()` — distribute ETH to holders
  - `withdrawDividend()` — withdraw earned dividends
  - Dividends are stored per user and can be claimed anytime

- 👥 Holder Tracking
  - Dynamic tracking of token holders
  - Ensures accurate dividend distribution

- 🔐 ERC20 Functionality
  - `transfer`
  - `approve`
  - `transferFrom`
  - `allowance`

---

## 🧠 Design Decisions

### 1. Separate Dividend Accounting
Dividends are stored independently from token balances.

Even if tokens are transferred or burned, previously earned dividends remain with the original holder.

---

### 2. Holder List Maintenance
To distribute dividends, the contract maintains:
- an array of holders
- a mapping to prevent duplicates

Holders are:
- added when balance > 0
- removed when balance = 0

---

### 3. Proportional Distribution

share = (user_balance / total_supply) * total_dividend

---

## ⚠️ Limitations

- Dividend distribution uses a loop over all holders
- Gas cost grows linearly with number of holders
- Not suitable for large-scale production use

---

## 🧪 Testing

Run tests using:

```bash
npm install
npm run test
```

All provided test cases pass successfully.

---

## 📁 Project Structure

```
contracts/
  Token.sol
  IERC20.sol
  IMintableToken.sol
  IDividends.sol
  SafeMath.sol

test/
  token.test.js

scripts/
  deploy.js
```

---

## 📌 Key Learnings

- Managing state consistency across mint, transfer, and burn
- Designing dividend systems with correct accounting
- Handling edge cases in smart contract logic
- Understanding ERC20 mechanics in practice

---

## 📬 Feedback

Open to feedback and improvements!