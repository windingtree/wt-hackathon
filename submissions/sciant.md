# Team Sciant

* Georgi Yovchev, georgi.yovchev@sciant.com, @GYovchev at GitHub
* Nikola Toshev, nik@sciant.com, @ntoshev at GitHub

Our project involves modification across several WT repos:
* https://github.com/windingtree/wt-read-api/
* https://github.com/windingtree/wt-write-api/
* https://github.com/windingtree/wt-contracts/
* https://github.com/sciant/wt-hotel-manager/

## Private offers implementation

We implement distribution of private offers independent of the storage mechanism (S3, Swarm) and without introducing external dependencies. We modify the rates schema to add an optional collection of rates to each rate plan. These rates are passed to `wt-write-api` unencrypted, and the API implementation encrypts them with the public key of the private consumer (in reality, the price is encrypted with a nonce to prevent brute forcing it). The unencrypted rate data looks like:
```json
  ...
  "price": 220 
  "privatePrices": {
      "0x87265a62c60247f862b9149423061b36b460f4bb": 200,
      "0xd037ab9025d43f60a31b32a82e10936f07484246": 195
  }
  ...
```
The `wt-read-api` is modified to decrypt any private offers to the user and filter out the rest. Only the holder of the private consumer's private key can decrypt these prices.

## Booking with payment rules managed by a smart contract

We implement booking and payment managed by the Hotel smart contract while maintaining a good level of privacy. Booking privacy requires encrypting user data that are accessible by the smart contract / blockchain. On the other hand, the smart contract can only make decisions (smart or not) based on cleartext data and potentially commitment schemes (hashes). Payments in ether are always public, the only thing that can be hidden is what the payment is for.

A compromise between the two can be to send all booking data encrypted to a smart contract, with cancelation data in clear text so that the smart contract can manage payment and cancellation. The data, encrypted with the hotel's public key, are sent via the blockchain to the hotel. The hotel can decide whether to accept the booking or reject it, the smart contract does not validate it. However the traveler can prove if he sent a booking request that conforms to the hotel pricing to an external judge. The hotel pricing remains relatively hidden in the cases of private offers, although it probably can be inferred with statistical analysis.

![booking diagram](./WT%20Booking%20with%20payment%20or%20guarantee.png?raw=true)

## Lessons learned

A true solution to anonymity on the blockchain involves zero-knowledge proofs. We learned about ZoKrates. An off-chain solution is easier to remain private, however it doesn't allow for trustless decisions based on smart contract policies, and it also removes the opportunities for incentivization of the various parties involved in the WindingTree ecosystem based on reservation fees.
