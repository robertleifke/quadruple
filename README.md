# Quadruple

![image](https://github.com/user-attachments/assets/06cfd20d-e63f-401a-98d8-a40f9d9578be)

A bull call spread strategy that quadruples the returns of any ERC-20 token.

## Usage

```bash
forge build
```

### Gas 

Get a gas report:

```sh
$ forge test --gas-report
```

| Contract         |           |
|------------------|-----------|
| Deployment Cost  | Deployment Size |
| 900917           | 3996      |
| Function Name    | min   | avg  | median | max  | # calls |
|------------------|-------|------|--------|------|---------|
| checkQuintic     | 387   | 6578 | 395    | 20406| 5       |

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