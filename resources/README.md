# Technical Resources

- **Winding Tree Developers Portal: https://developers.windingtree.com**
- Winding Tree Debugging Tools: https://debugging-tools.windingtree.com/
- Ethereum Developers Resources: https://www.ethereum.org/developers/

## Presentation Slides

TBA

## Random tips

- Version your code. Any of [GitHub](https://github.com), [GitLab](https://about.gitlab.com/) or [BitBucket](https://bitbucket.org) are fine. Or use another service, the code has to be publicly accessible and open-sourced though.
- Deployment is always a pain. Don't spend too much time on it. For frontend, we can recommend [now.sh](https://now.sh), [GitHub pages](https://pages.github.com/) or maybe [Heroku](https://www.heroku.com). For backend services, [Heroku](https://www.heroku.com), [free 1st year tier of AWS](https://aws.amazon.com/), [Digital Ocean trial](https://try.digitalocean.com/cloud-hosting/) or maybe [Jelastic](https://jelastic.com/docker/) should work. There are so many options that we might advice on how and where to run your service, but we probably don't know every service out there. A solid recommendation would be to pack your service into an easily portable [docker](https://docker.com) container.
- If you need to host static files, use [now.sh](https://now.sh), [GitHub pages](https://pages.github.com), [GitHub Gist](https://gist.github.com) or even [Pastebin](https://pastebin.com) - basically any service that offers direct access to the content (Dropbox for example does not allow that).
- If you need to connect directly to Ethereum, don't spend time on running your own nodes. Feel free to use [Infura](https://infura.io).
- If you'd like to connect to [Swarm](https://swarm.ethereum.org/), use an [existing gateway](https://swarm-gateways.net).
- There's a lot of outdated or broken tools and tutorials on Ethereum. Be careful on which version you are using.
- If you're working on smart contracts, you can use an excellent [openzeppelin](https://openzeppelin.org/) library.
- [web3.js](https://github.com/ethereum/web3.js/) has some serious issues with versioning. There was a lot of breaking changes after `1.0.0-beta.38`. You can use the [latest documented version](https://web3js.readthedocs.io/en/1.0/), but some of the libraries (like truffle, wt-js-libs) might not (probably won't actually) work with the latest version.

## Running Winding Tree environment

- Entrypoint: [0x7EB7c3B768D75C740B6d08D3b3eA411B3296ceBB](https://ropsten.etherscan.io/address/0x7EB7c3B768D75C740B6d08D3b3eA411B3296ceBB)
- 0xORG Factory: [0x78D1548E03660093B51159De0E615ea8F6B9eaF9](https://ropsten.etherscan.io/address/0x78D1548E03660093B51159De0E615ea8F6B9eaF9)
- Hotels Segment Directory: [0x8ea119A7Ef0Ac4c1a83a3BB6D1aa1a3afcAfDE8b](https://ropsten.etherscan.io/address/0x8ea119A7Ef0Ac4c1a83a3BB6D1aa1a3afcAfDE8b)
- Líf Deposit: [0x39af806825B81342D51980E2AD96B7A75Ab31CDa](https://ropsten.etherscan.io/address/0x39af806825B81342D51980E2AD96B7A75Ab31CDa)
- Lif Token with a faucet: [0xB6e225194a1C892770c43D4B529841C99b3DA1d7](https://ropsten.etherscan.io/address/0xB6e225194a1C892770c43D4B529841C99b3DA1d7)

- Read API: https://lisbon-api.windingtree.com
- Write API: https://lisbon-write-api.windingtree.com
- Search API: https://lisbon-search-api.windingtree.com
- Hotel explorer: https://hotel-explorer-lisbon.windingtree.com