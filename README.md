
# DBank

## Introduction

DBank is a web-based banking application built using the DFINITY Internet Computer framework. It enables users to perform basic banking operations like checking balances, making deposits (top-ups), and withdrawals, all within a secure and decentralized environment.

## Features

- **Check Balance**: Users can view their current account balance.
- **Deposit Funds (Top Up)**: Allows depositing funds into the account.
- **Withdraw Funds**: Enables withdrawal of funds from the account.
- **Real-time Balance Update**: The account balance updates in real time after every transaction.


To learn more before you start working with dbank, see the following documentation available online:

- [Quick Start](https://internetcomputer.org/docs/current/developer-docs/setup/deploy-locally)
- [SDK Developer Tools](https://internetcomputer.org/docs/current/developer-docs/setup/install)
- [Motoko Programming Language Guide](https://internetcomputer.org/docs/current/motoko/main/motoko)
- [Motoko Language Quick Reference](https://internetcomputer.org/docs/current/motoko/main/language-manual)

If you want to start working on your project right away, you might want to try the following commands:

```bash
cd dbank/
dfx help
dfx canister --help
```

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# Starts the replica, running in the background
dfx start --background

# Deploys your canisters to the replica and generates your candid interface
dfx deploy
```

Once the job completes, your application will be available at `http://localhost:4943?canisterId={asset_canister_id}`.

If you have made changes to your backend canister, you can generate a new candid interface with

```bash
npm run generate
```

at any time. This is recommended before starting the frontend development server, and will be run automatically any time you run `dfx deploy`.

If you are making frontend changes, you can start a development server with

```bash
npm start
```

Which will start a server at `http://localhost:8080`, proxying API requests to the replica at port 4943.

### Note on frontend environment variables

If you are hosting frontend code somewhere without using DFX, you may need to make one of the following adjustments to ensure your project does not fetch the root key in production:

- set`DFX_NETWORK` to `ic` if you are using Webpack
- use your own preferred method to replace `process.env.DFX_NETWORK` in the autogenerated declarations
  - Setting `canisters -> {asset_canister_id} -> declarations -> env_override to a string` in `dfx.json` will replace `process.env.DFX_NETWORK` with the string in the autogenerated declarations
- Write your own `createActor` constructor

## Usage
After deployment, the application can be accessed through a web browser.

Open the Application: Navigate to the provided local URL in your web browser.

Interacting with the Application:

- Enter the amount in the 'Amount to Top Up' field and click 'Finalise Transaction' to deposit funds.
- Enter the amount in the 'Amount to Withdraw' field and click 'Finalise Transaction' to withdraw funds.
- The current balance is displayed at the top and is updated after each transaction.

## Troubleshooting
- DFINITY Network Issues: Confirm that the DFINITY network is running using dfx start --background.
- Frontend-Backend Connection: Check that the paths in index.js for importing backend functions are correctly set.
- Browser Console Errors: Look for any errors in the browser console.
- Function Name Consistency: Ensure that the function names in index.js match those in main.mo.

## Screenshot
- <img width="775" alt="Screenshot 2024-01-08 at 4 36 58 PM" src="https://github.com/shovo4/dbank/assets/58551093/149f1636-0dc8-4933-b9eb-a51af3944fd0">
