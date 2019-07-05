# Pirate-tree

## Team Members

* Giuseppe Maniscalco, g.maniscalco@holidaypirates.com, https://github.com/giuseppemaniscalco
* James O'Shea, j.oshea@holidaypirates.com, https://github.com/jamesoshea
* Bojan Smudja, b.smudja@piratetech.rs
* Anita Popvic, a.popovic@holidaypirates.com
* Vladimir Jankovic, v.jankovic@piratetech.rs

## Repositories

- https://github.com/giuseppemaniscalco/piratetree

### What we wanted to do:

- Make a booking (we ended up picking hotels as there was inventory ready to go)
- Get a price for it and create a smart contract which whould hold ETH in escrow until the value of the booking is fully paid for
- Allow guest to partially pay for the booking
- Release these funds to the hotel once the full amount has been paid
- Nice to have: notify hotels/guests once this is done

### What we actually managed:

- Get the WT booking API server running locally (using the provided `lisbon` read and write APIs) and deploy it to Zeit/Now to make it easily accessible
- Create a hotel booking using this server and retrieve a booking ID
- Create a go app which hits this endpoint
- Create and deploy a Smart contract using Remix. It's for a single hotel booking and it doesn't really do anything.
- Interact with this smart contract using Remix (update and show paid value)

##### Smart Contract

```
pragma solidity ^0.4.15;

contract Purchase {
    address buyer;
    address hotelId;
    bytes9 bookingId;
    uint purchaseAmount;
    uint paidAmount = 0;

    event paymentFulfilled();
    event overPayment();
    
    function createBooking(address _hotelId, address _buyer, bytes9 _bookingId, uint _purchaseAmount) public {
        buyer = _buyer;
        hotelId = _hotelId;
        bookingId = _bookingId;
        purchaseAmount = _purchaseAmount;
    }

    function updateValue(uint _amount) public payable returns (uint) {

        if (paidAmount + _amount > purchaseAmount) {
            emit overPayment();
            return 1;
        }

        paidAmount += _amount;
        if (paidAmount == purchaseAmount) {
            emit paymentFulfilled();
            return 0;
        }
    }
    function showValue() public view returns (uint){
        return paidAmount;
    }
}
```

### What we would like to do next:

- Figure out how to create and deploy smart contracts programmatically to handle more than one booking
- Take the hotel ID, booking ID, price, wallet address and the price and create a booking which can then be updated and paid for using ETH
- Figure out a way to make booking data accessible for hotels
- Notify hotels/ users when a room is fully paid for
- Create interfaces to make this pretty

## We learned
- Creating wallets
- Smart contracts / Solidity
- WT accounts/organizations
- Ethereum basics
