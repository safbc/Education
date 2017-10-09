# A Serverless Chatbot

This example comes with everything you need to start using smart contracts from a react app on your mobile and uses the Status API to have a very basic chat with a serverless chatbot.

## Enabling debug mode in Status

To make debugging work we run a web server on your device. It runs on port 5561 on both iOS and Android.
To start a server you need to: 

1. Connect your device to a computer
2. Open Status application on your device and log in
3. Open `Console` chat and execute `/debug` command providing `On` as the argument

Please note that the server will start automatically next time you log in with the same credentials. You can easily change this behavior by turning the debug server off (it can be done by executing `/debug` command with `Off` argument)

You will also need to install `status-dev-cli`, the tool for talking to the API.

```shell
npm install status-dev-cli --save
```


## Building

1. Install truffle and an ethereum client. For local development, try Ethereum TestRPC.
    ```shell
    npm install -g truffle // Version 3.0.5+ required.
    npm install -g ethereumjs-testrpc
    ```

2. Clone this repo and cd into it

3. Install the node dependencies.
    ```shell
    npm install
    ```
4. Run Ethereum RPC on port **8546**. For simplicity and development we will be using Ethereum TestRPC.
    ```shell
    testrpc -p 8546
    ```
   
5. *If you use Android* then make TestRPC accessible from your device.
    ```shell
    adb reverse tcp:8546 tcp:8546
    ```
    
6. Switch node in Status.
    ```shell
    status-dev-cli switch-node http://localhost:8546
    ```
    
   Of course, there can be options. You can use go-ethereum instead of TestRPC, and instead of port forwarding you can switch to any other accessible node using its IP address.

7. Compile and migrate the contracts.
    ```shell
    truffle compile
    truffle migrate
    ```
    
8. *If you use Android* the application won't be accessible automatically, since it runs on port 3000 and your device/emulator knows nothing about it. Execute the following to make web application accessible:
    ```shell
    adb reverse tcp:3000 tcp:3000
    ```
    
## Running

Now it's time to run your application!

1. Run the webpack server for front-end hot reloading. This command also tries to add your DApp to Status (so it requires the debug mode to be established). For now, smart contract changes must be manually recompiled and migrated. 
    ```javascript
    npm run start
    ```

## Testing

Jest is included for testing React components and Truffle's own suite is included for smart contracts. Be sure you've compiled your contracts before running jest, or you'll get file not found errors.

    ```javascript
    // Runs Jest for component tests.
    npm run test

    // Runs Truffle's test suite for smart contract tests.
    truffle test
    ```
    
## Releasing

To build the application for production, use the build command. A production build will be in the build_webpack folder.

    ```javascript
    npm run build
    ```

## FAQ

* __Why is there both a truffle.js file and a truffle-config.js file?__

    Truffle requires the truffle.js file be named truffle-config on Windows machines. Feel free to delete the file that doesn't correspond to your platform.

* __Where is my production build?__

    The production build will be in the build_webpack folder. This is because Truffle outputs contract compilations to the build folder.

* __Where can I find more documentation?__

    All truffle boxes are a marriage of [Truffle](http://truffleframework.com/) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start!
    
* __Where is the chatbot and what's happening there?__  
    You can also find documentation on the API [here](https://wiki.status.im/), on the Status Wiki. The Javascript that controls the simple chatbot that will greet you if you either send a message with any text directly to it, or help you decide which way to greet by providing an extra route in the suggestions bar can be found in `public/bot/bot.js` and I had to hack the truffle-box build and place it there after, but this should showcase the beginnings of what is possible. You can also read this [blog post](https://blog.status.im/announcing-winners-of-the-status-global-hackathon-a44fb54e98f7) from our hackathon to find more detailed examples.
