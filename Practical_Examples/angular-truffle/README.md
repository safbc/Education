# Angular Truffle Box

This box comes with everything you need to start using smart contracts from a react app. This is almost as barebones as it gets, so nothing stands in your way. Someone awesome added the style module material-ui to this box, which makes development even easier.

## Installation

1. Install truffle and an ethereum client. For local development, try EthereumJS TestRPC.
    ```javascript
    npm install -g truffle // Version 3.0.5+ required.
    npm install -g ethereumjs-testrpc
    ```

2. Download box.
    ```javascript
    truffle unbox Quintor/angular-truffle-box
    ```

3. Compile and migrate the contracts.
    ```javascript
    truffle compile
    truffle migrate
    ```

5. Truffle's smart contract tesing framework should still work.
    ```javascript
    // Runs Truffle's test suite for smart contract tests.
    truffle test

    // Run Angular component tests
    ng test

    // Run Protractor end-to-end tests
    ng e2e
    ```

6. Serve the app and look on in awe.
    ```javascript
    ng serve
    ```

## FAQ

* __Why is there both a truffle.js file and a truffle-config.js file?__

    Truffle requires the truffle.js file be named truffle-config on Windows machines. Feel free to delete the file that doesn't correspond to your platform.