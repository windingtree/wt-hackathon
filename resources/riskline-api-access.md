# Riskline API Access

*Riskline openned it's API for hackathon participants who creates a Winding
Tree OrgID. To get limited access token you need to proof that you have access
to an existing OrgID.

Here is an example of communication which needs to be done to get limited free
access token.

This protocol is also a proof-of-concept of programatic control of access to an
API for OrgIDs

There is also a code snipped showing how to do sign nonce and verify it using
javascript and Metamask's web3: https://jsfiddle.net/czervenka/cye5n9m6*


**Riskline API base url for token acquisition:** To be defined.

## Actors:

- Owner of Org ID willing to get a token (further just "OrgID")
- Riskline


## Steps:

### 1. Generate Nonce

#### Request:

    POST /api/nonce
    content-type: application/json; charset: utf-8

    {
        "org_id_address": "0xab97c6afe5a025d1dff5341d935e21dfb8e5c468"
    }


#### Response:
201 Created 
    {
        "nonce": "a-unique-string-specific-to-this-challenge-response-series"
    }

### 2. Sign the nonce

#### Request:
*OrgId creates message to sign as: `nonce` + `.` + `org_id_address`, signs the
message using one of OrgID's associatedKeys and sends the response.*

    POST /token/
    content-type: application/json; charset: utf-8

    {
        "nonce": "a-unique-string-specific-to-this-challenge-response-series",
        "signature": "0x...",
        "org_id_address": "0x..."
    }

#### Response:
*Riskline*
*- checks whether the nonce was issued by Riskline,*
*- re-created the signed message (`nonce` + `.` + `org_id_address`),*
*- extracts signee from `signature` (using ethereum ecRecover function) and*
*- verifies that the extracted signee is in OrgID.associatedKeys (by calling*
*OrgID.hasAssociatedKey).*
*If the verification succeeds, it returns OrgID's access token.*

    201 Created

    {
        "token": "secret-token-for-the-org-id-address"
    }
    

