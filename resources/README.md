# Winding Tree Hackathon #3 Technical Resources - London, UK

- **Winding Tree Developers Portal: https://developers.windingtree.com**
- Winding Tree Debugging Tools: https://debugging-tools.windingtree.com/
- Ethereum Developers Resources: https://www.ethereum.org/developers/

## Random tips

- Version your code. Any of [GitHub](https://github.com), [GitLab](https://about.gitlab.com/) or [BitBucket](https://bitbucket.org) are fine. Or use another service, the code has to be publicly accessible and open-sourced though.
- Deployment is always a pain. Don't spend too much time on it. For frontend, we can recommend [now.sh](https://now.sh), [GitHub pages](https://pages.github.com/) or maybe [Heroku](https://www.heroku.com). For backend services, [Heroku](https://www.heroku.com), [free 1st year tier of AWS](https://aws.amazon.com/), [Digital Ocean trial](https://try.digitalocean.com/cloud-hosting/) or maybe [Jelastic](https://jelastic.com/docker/) should work. There are so many options that we might advice on how and where to run your service, but we probably don't know every service out there. A solid recommendation would be to pack your service into an easily portable [docker](https://docker.com) container.
- If you need to host static files, use [now.sh](https://now.sh), [GitHub pages](https://pages.github.com), [GitHub Gist](https://gist.github.com) or even [Pastebin](https://pastebin.com) - basically any service that offers direct access to the content (Dropbox for example does not allow that).
- If you need to connect directly to Ethereum, don't spend time on running your own nodes. Feel free to use [Infura](https://infura.io).
- If you'd like to connect to [Swarm](https://swarm.ethereum.org/), use an [existing gateway](https://swarm-gateways.net).
- There's a lot of outdated or broken tools and tutorials on Ethereum. Be careful on which version you are using.
- If you're working on smart contracts, you can use an excellent [openzeppelin](https://openzeppelin.org/) library.
- [web3.js](https://github.com/ethereum/web3.js/) has some serious issues with versioning. There was a lot of breaking changes after `1.0.0-beta.38`. You can use the [latest documented version](https://web3js.readthedocs.io/en/1.0/), but some of the libraries (like truffle, wt-js-libs) might not (probably won't actually) work with the latest version.
- If ETH faucets don't work for you, ask us. We should be able to transfer some Ropsten Ether to you.

## Running Winding Tree environment

[Developer Environments](https://developers.windingtree.com/environments.html)

- WT Entrypoint: [0xa268937c2573e2AB274BF6d96e88FfE0827F0D4D](https://ropsten.etherscan.io/address/0xa268937c2573e2AB274BF6d96e88FfE0827F0D4D)
- 0xORG Factory: [0x8E6463ea056d812094Ed514455Ab3C88fc23D59C](https://ropsten.etherscan.io/address/0x8E6463ea056d812094Ed514455Ab3C88fc23D59C)
- Hotels Segment Directory: [0x2c29c421d7fd7be4cc2bfb6d1a44426e43021914](https://ropsten.etherscan.io/address/0x2c29c421d7fd7be4cc2bfb6d1a44426e43021914)
- Airlines Segment Directory: [0x7d3Ce0d422D381971Eb2bD9615b58f2df5C9f047](https://ropsten.etherscan.io/address/0x7d3Ce0d422D381971Eb2bD9615b58f2df5C9f047)
- Líf Deposit: [0xfCfD5E296E4eD50B5F261b11818c50B73ED6c89E](https://ropsten.etherscan.io/address/0xfCfD5E296E4eD50B5F261b11818c50B73ED6c89E)
- Lif Token with a faucet: [0xB6e225194a1C892770c43D4B529841C99b3DA1d7](https://ropsten.etherscan.io/address/0xB6e225194a1C892770c43D4B529841C99b3DA1d7)

- Debugging tools: http://debugging-tools.windingtree.com
- Read API (v0.15.0): https://madrid-api.windingtree.com
- Write API (v0.17.0): https://madrid-write-api.windingtree.com
- Search API (v0.7.1): https://madrid-search-api.windingtree.com
- Hotel explorer (v0.11.3): https://hotel-explorer-madrid.windingtree.com
