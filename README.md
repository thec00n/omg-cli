## omg-cli

[![CircleCI](https://circleci.com/gh/thec00n/omg-cli.svg?style=svg)](https://circleci.com/gh/thec00n/omg-cli)

This is a command line tool to interact with the OMG network and it's based on [omg-js](https://github.com/omisego/omg-js). The main intention behind building it was to enable easier security testing by isolating end points and by provding a callable interfaces for both the contracts as well as the watcher component.

### Installation

1. Checkout the repository
2. Install `node` if you have not already. `omg-cli` has been tested with `node` 10.x but should work with other versions. Have not tested it though.
3. Run installation `npm install` 
4. Run build script `npm run build`

### Setup

In order to use `omg-cli` you need to setup a configuration and create `.env`. You can copy [.env.template](./.env.template)) and use it as a template. Important parameters are:  

- `WATCHER_URL`: Watcher info URL 
- `PLASMA_FRAMEWORK`: [PlasmaFramework](https://github.com/omisego/plasma-contracts/blob/master/plasma_framework/docs/contracts/PlasmaFramework.md) contract address 
- `BLOCKEXPLORER_URL`: [OMG network block explorer](https://github.com/omisego/blockexplorer)
- `WATCHER_PROXY_URL`: Set a HTTP/HTTPS proxy for further inspection of requests to the watcher
- `GETH_URL`: ETH node (for testing environment set Ropsten as the default)
- `ERC20_CONTRACT`: For using ERC20 tokens on the network make sure you have some tokens available. You can use [token.sol](./tests/sol/token.sol) to generate some quickly. 
- `ALICE_ETH_ADDRESS` `ALICE_ETH_ADDRESS_PRIVATE_KEY` `BOB_ETH_ADDRESS` `BOB_ETH_ADDRESS_PRIVATE_KEY`: Create two accounts and fund them with sufficient tokens/ETH. `omg-cli` uses them per default to interact with the ETH network. 
   

### Getting started

Any client that interacts with the OMG network communicates with two components:

- [Watcher](https://github.com/omisego/elixir-omg): This is the main point from where the client retrieves information about the OMG network. It helps clients for example to calculate accounts balances, compose valid transactions and forward them to the child chain and it also emits security events about the network. A watcher is a trusted component and users should run their own for the same reasons they should run their own ETH or BTC nodes. More information on what the watcher does can be found in the [architectors docs](https://github.com/omisego/elixir-omg/blob/master/docs/architecture.md). Also checkout the [Swagger API specs](https://developer.omisego.co/elixir-omg/) for further information around watchers end points.
- [Plasma contracts](https://github.com/omisego/plasma-contracts):
