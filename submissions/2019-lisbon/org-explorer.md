# Organization Portal/Explorer
Application that allows browsing of organizations registered with winding tree

## Team Members

* James Glennon, jamesglennon@gmail.com, @CyberJimbo
* Martin Massera, martinmassera@gmail.com, @newearthmartin
* Jason Moujaes, jmoujaes@gmail.com, @jmoujaes
* Nathan Hamley, nathan.hamley@peakwork.com @nhamley

## Repository

https://github.com/newearthmartin/hacktravel

## Description


### Running the frontend
Requires `node v10.x.x` and `npm 6.4.1`

```
cd explorer-fe
nvm use 10.16
npm install
npm run serve
```

Then access the explorer at http://localhost:8080/

### Setting up the scanner
Requires `python3.6` and `virtualenv`

```
cd hacktravel
. setup.sh
```

### Running the scanner

In the same hacktravel folder
```
. run.sh
```
Then access the scanner API http://localhost:8000/orgs


## Problem

We need UI tools to easily see information about organizations in WT directory. Currently we only have console tools and require a considerable degree of hackerdom.

## Solution

We created tools related to ORG.ID.The ORG.ID explorer let's you:
 * see information about an ORG.ID
 * see how much Lif they have (for trusting purposes)
 * veriy if a message is effectively signed by an organization
 * create a new Organization from a JSON URL.

We also are presenting information from the trust service created by another hack-team.

## We learned

* To work as an ecosystem, integrating with tools from another hack-team
* To access the WT contracts blockchain from different languages, with helpers like wt-js-libs and calling contracts directly with web3
* Smart contracts, abi, etc
* Truffle, metamask, etc
* WT mission: leveling the playfield to let small companies and independent developers (like us!) access the travel industry players
* Travel industry concepts
* Trust problems in decentralized ecosystem

## Extra resources

* link to presentation (and/or)
* link to running instance

