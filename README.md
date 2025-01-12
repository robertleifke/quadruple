# Quadruple 🐂

![gif](assets/quad_bull.gif)

A bull call spread strategy built as a [Uniswap V4](https://github.com/uniswap/v4-core/) hook that that **quadruples** the returns of any ERC-20 token.

## Overview

Here’s a simple example of a bull call spread position:

- **Underlying:** ETH at $1400 USDC
- **Expiration:** March 1st, 2025
- **Strike Prices:**
  - Long Call (Lower Tick) = $1400 strike (buy)
  - Short Call (Upper Tick) = $1500 strike (sell)
- **Premiums:**
  - Long Call (Borrow LP) = $80 (pays)
  - Short Call (Provide LP) = $60 (recieves)
- **Number of Contracts:** 1 contract (e.g. 1 ETH)
- **Net Debit (Cost):** $80 - $60 = $20

If ETH goes above $1500, the long call will be exercised and the short call will be bought back so you make $80 dollars with only $20 in upfront cost, hence a 4x return. In this scenario gains are capped at $1500 and if ETH goes below $1400 you lose $20.

### Chart

<pre style="background-color:#1e1e1e;color:#dcdcdc;padding:16px;border-radius:4px;font-family:'Courier New', Courier, monospace;white-space:pre;overflow:auto;">
Payoff ($)
   ^
 +80 |                  ●─────────────  (Flat at +80 beyond $1500)
     |                 /|             
 +60 |                / |             
     |               /  |             
 +40 |              /   |             
     |             /    |             
 +20 |            /     |             
     |           /      |             
   0 |          /       |             
     |         /        |             
 -20 ●─────────         |             
     +------------------+-----------------> ETH Price at Expiration
         1400           1500

● = strike levels
</pre>

## Usage

```bash
$ forge build
```

### Gas 

Get a gas report:

```sh
$ forge test --gas-report
```

| Quadruple.sol         |               |
|-----------------------|---------------|
| Deployment Cost       | Deployment Size |
| 900917                | 3996          |
| Function Name         | min   | avg  | median | max   | # calls |
| beforeSwap()          | 387   | 6578 | 395    | 20406 | 5       |
| afterSwap()           | 387   | 6578 | 395    | 20406 | 5       |
| beforeAddLiquidity()  | 387   | 6578 | 395    | 20406 | 5       |
| afterAddLiquidity()   | 387   | 6578 | 395    | 20406 | 5       |
| beforeRemoveLiquidity() | 387 | 6578 | 395    | 20406 | 5       |
| afterRemoveLiquidity()  | 387 | 6578 | 395    | 20406 | 5       |

### Lint

Lint the contracts:

```sh
$ bun run lint
```

### Test

Run the tests:

```sh
$ forge test
```

Generate test coverage and output result to the terminal:

```sh
$ bun run test:coverage
```

Generate test coverage with lcov report (you'll have to open the `./coverage/index.html` file in your browser, to do so
simply copy paste the path):

```sh
$ bun run test:coverage:report
```

## License

This project is licensed under MIT.