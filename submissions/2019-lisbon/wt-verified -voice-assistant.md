# Verified Winding Tree voice assistant

Using Google Home Voice Asssistant to search for hotels in partiucular city using WT read, listing the hotels, choosing one with the dates and creating booking. 
Signing the booking with the private key of SSL certificate of particular domain. Composing WT booking object and attaching the signature as header to the booking request. 
Receiving booking and getting public key out of domain SSL certificate, checking signature of booking object.

## Team Members

* David Duong, david.duong@siesta.cloud
* Jan Hanák, jan.hanak@siesta.cloud
* Mikolas Belec, mikolas@siesta.cloud

## Repository

https://github.com/cduongt/wt-hackathon-submission

## Description

We wanted to explore the possibilities of voice assistant and use it for search and booking of accommodation of WT inventory. 
We havent worked with the Google voice assistant before, so we had to learn the API and feautres. 
We used libraries from previous hackathon for connection WT and composing booking object. The models are part of the project now.
We used our  SSL certificate private key to sign hash of booking object, so receiveing party can verify origin of booking from siesta.cloud domain

## Problems

- Booking hotel without OTA (skipping the massive development nessecary for bookings)
- Trust clue - domain verification via SSL certificate

## Solution

1) Implementation of Google Home Voice Assistant dialog flow APIapi > Listening for the city.
2) Searching in Winding Tree (using WT read API) for hotels in particular city.
3) Reading the found hotels
4) Selecting hotels and dates
5) Composing WT booking object, hashong and signing by verified domain SSL certificate private key 
6) Seding booking to WT booking API endpoint
7) Receiving booking and fetching public key of varified domain
8) Checking validity of signature with the domain public key

## We learned

1) Google Home API / Dialog is not that easy
2) The signatures and hashes should be in headers so the content of the request allways correspond to signature
3) Various SSL certificate formats
4) Searching by city and WT read filter params

## Extra resources

* https://docs.google.com/presentation/d/1bqv5TXaZVns6K4vI-Pl89_oJeJFBJfpB47kJHHpYoUU/edit?usp=sharing
