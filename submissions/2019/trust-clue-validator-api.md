# Trust Clue Validation API

This project implements an API that allows you to validate two exemplary trust clues for an Hotel Organization.

## Team Members

* Axel Philipsenburg, axel.philipsenburg@peakwork.com, @AxelAtPeakwork
* Thibaud Durivaux, durivaxt@iata.org, @tdurivaux
* Susan Wang, susanwangds@gmail.com
* Mathieu Tahon, mathieu.tahon@noath.net
  
## Repository

https://github.com/AxelAtPeakwork/wt-hackathon-trustcluevalidators

## Description

This API is implemented in python 3.6, using the web3.py framework to access the etherum ropsten networks along with few other ones to do HTTP requests and DNS entry lookups.

### Python development setup

Given that a python virtualenv development environment is setup, you can install the required libraries by calling 

```
pip install -r requirements.txt
```

from the projects main directory.

Afterwards start the app by calling:

```
cd trust-clue-validator
python3 app.py
```

### Docker build and deployment

An easy way to run the API on your local machine is to utilize the docker container runtime

Switch to the direcotry containing the `Dockerfile` and run

```
docker build -t wt-clue-validators .
```

to build the service image.

Once this is done, you can run the API by staring a container from the newly build image:

```
docker run -it -p 5000:5000 wt-clue-validators
```

This will expose the API's HTTP interface on `http://localhost:5000`. 

An example query should work

```
curl "http://localhost:5000/clue/dns?organization=0x7a840A240C561fEf55aae85aCcC5974b60546334"
```

### Temporary deployment on a public server

For collaboration purposes with other teams during the hackathon, we 
deployed the API on a publically avaiable server.

The example query below makes use of it:

```
curl "http://caramon.kunveni.net:5010/clue/dns?organization=0x7a840A240C561fEf55aae85aCcC5974b60546334"
```

## Problems

On a decentralized platform, validating the trust between two parties with no central trust authority available, other
ways of evaluating and validating truts must be fround.

One way for example, is to evaluate a proof of effort or do cross checks with off-chain information.

Another one is to store hints of trust on the block chain itself, where one party expresses its trust for
another one.

These are just two examples of possible clues. Please check the presentation in the GIT repository for a few more
thoughts on what kind of clues could exist.

## Solution

In ths proof of concept we approached the two types of clues mentioned above and implemented them as an HTTP API
that you cann call to see if the clues hold true for a given organisation and a trust vouching party.

### Cross checking domain claimed by ORG.JSON with DNS record

Each hotel organization describes itself with an ORG.JSON document that is accessible via a public address. This
document can contain an website URL that the ORG.JSON claims belongs to its organization.

This claim can be cross checked by storing information with the website's domain DNS record.

DNS allows to store abritrary information within so called TXT entries that belong to a domain.

Given that the party owning the hotel organization also owns the website and as such holds control of its DNS record,
it can store its ethereum address within the "wtaddress.<domain.tld>" TXT entry.

This way, when queried with an ORG.ID's address, the API can query that organization for its owner and the website.
With that, it can then query the website's domain DNS record and compare the stored address with the one retrieved
from ethereum.

If they match, the clue holds true and provides the verification that the party owning the ORG.ID has control 
over the website's DNS records, which can be preceived as a strong or weak trust clue 
depending on the website's reputation.

Example query untrusted clue:

```
curl "http://caramon.kunveni.net:5010/clue/dns?organization=0x98Fa47CFA890b12465775c723C072376FC64eE1e"
```

```
{
    "trusted": false,
    "dns_record": "_wtaddress.hotel-martin.com"
}
```

Example query trusted clue:

```
curl "http://caramon.kunveni.net:5010/clue/dns?organization=0x7a840A240C561fEf55aae85aCcC5974b60546334"
```

```
{
    "trusted": true,
    "dns_record": "_wtaddress.kunveni.net"
}
```

### Checking P2P trust links

As an on-chain trust clue we deployed a smart contract on ethereum that allows a party to set trust/distrust flags for organizations.

Contract address

```
0x059745F23cc4D942BC1C890E7589f7d3A8a3406d
```

ABI
```
[
  {
    "constant": true,
    "inputs": [
      {
        "name": "",
        "type": "address"
      },
      {
        "name": "",
        "type": "uint256"
      }
    ],
    "name": "reverseLookup",
    "outputs": [
      {
        "name": "",
        "type": "address"
      }
    ],
    "payable": false,
    "stateMutability": "view",
    "type": "function"
  },
  {
    "constant": true,
    "inputs": [
      {
        "name": "receiver",
        "type": "address"
      },
      {
        "name": "sender",
        "type": "address"
      }
    ],
    "name": "isTrustedLink",
    "outputs": [
      {
        "name": "",
        "type": "bool"
      }
    ],
    "payable": false,
    "stateMutability": "view",
    "type": "function"
  },
  {
    "constant": true,
    "inputs": [
      {
        "name": "",
        "type": "address"
      },
      {
        "name": "",
        "type": "address"
      }
    ],
    "name": "trustLinks",
    "outputs": [
      {
        "name": "trusted",
        "type": "bool"
      },
      {
        "name": "updated",
        "type": "uint256"
      }
    ],
    "payable": false,
    "stateMutability": "view",
    "type": "function"
  },
  {
    "constant": false,
    "inputs": [
      {
        "name": "receiver",
        "type": "address"
      },
      {
        "name": "trusted",
        "type": "bool"
      }
    ],
    "name": "addTrustLink",
    "outputs": [],
    "payable": false,
    "stateMutability": "nonpayable",
    "type": "function"
  }
]
```

If a party vouches trust or distrust for an organization, the API can be queried with the address of a party (the `sender`) and an ORG.ID (the `receiver`)

Example query with a set trust clue

```
curl "http://caramon.kunveni.net:5010/clue/p2ptrust?receiver=0xd5D3420a445Eac855c5db0340D55423D86e8a599&sender=0x2af54462C410a42b013dcB3367751c7AD5F86021"
```
```
{
    "trusted": true,
    "trusted_since_block": 5930417
}
```

Example query with set distrust clue

```
curl "http://caramon.kunveni.net:5010/clue/p2ptrust?receiver=0xd5D3420a445Eac855c5db0340D55423D86e8a599&sender=0xdc82af2c4048Fa661B72008a324AAA79eFA05e0E
```

```
{
    "trusted": false,
    "trusted_since_block": 5930844
}
```

## Extra resource

* See PDF inside the GIT repository

