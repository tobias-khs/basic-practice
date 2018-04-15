# Basic Practice

The purpose of this document is to get people up to speed on compiling fintech related software.

For other languages, see:
*  [日本語](README.ja.md)


To avoid messing up the development environment, Docker is used frequently to contain all the working code.  It is highly recommended that you become familiar with how Docker works.  If you have a Linux and/or Mac OS, then it will be easy to set up.  If you have Windows, it is recommended that you spend money (10 USD/month) on a remote server.  It is the same price as 2 cocktails at Starbucks.

# Preparation

[See this page](CheatSheet.md).


# Bitcoin Practice


## Testnet Faucet

In order to do testing, you need to get test coins.  Go to the link below and get some free testnet coins.

[Hamburg Testnet Faucet](https://testnet.manu.backend.hamburg/faucet)

[This is the testnet block chain explorer](https://live.blockcypher.com/btc-testnet/).

## Node.js BTC Wallet


Practice handling Bitcoin with Javascript.

The practice file is [here](js/simple-spend.js).


To create the docker image and container for doing node js work:
1.  `docker build -t mynodejs:jessie --build-arg useruid=$(id -u $USER) -f docker/Dockerfile.js.amd64 .`
1.  `docker run -v $(pwd):/var/share/nodejs --name mynodejs.run -it mynodejs:jessie /bin/bash`
  * with this command, you will end up in a bash shell in which you can execute commands
1. `cd js`
1. `npm install bitcoinjs-lib`
1. `node ./simple-spend.js`
  * this will run the javascript program

Then:  
Copy paste values into `simple-spend.js`:
- `privkey`: The private from-key
- `addrPre`: The from-address
- `toAddr`: The to-address (address from second account)
- make sure everything is in mynetwork
- make sure the balance is in satoshi (`bitcoin * balance`)
- Execute simple-spend and copy the output transaction-ID
- Goto transaction explorer and see balance of second address => it is 0btc
- Goto https://live.blockcypher.com/btc-testnet/decodetx  
  and enter that transaction-ID from before => you'll get a confirmation
- Click the link to broadcast and hit the `broadcast` button from that page
  in order to broadcast the transaction
- check back the balance of second address to see the updated balance

Other links:
- https://bitcoinfees.info/

## Perl BTC Wallet

For Perl, we have [a simple program for transactions set up](pl/simple-wallet.pl).



# Install Docker

*  [For Mac](https://docs.docker.com/docker-for-mac/install/)
*  [For Debian/Ubuntu](https://docs.docker.com/install/linux/docker-ce/debian/)
*  [For Windows](https://docs.docker.com/docker-for-windows/install/) - but the UX in Windows is very, very different from the other two
