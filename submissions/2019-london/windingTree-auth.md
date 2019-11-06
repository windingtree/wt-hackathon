# Full Name of an Example Hackathon Project

Here comes a short one liner description of the project.

## Team Members

* Bach Adylbekov, adylbekov@protonmail.com, @bahadylbekov
* Sergey Solovyov, adress2009@mail.ru,

## Repository

https://github.com/bahadylbekov/windingtree-auth.git
https://github.com/bahadylbekov/winding-tree-server.git

## Description

First version of that solution using accelerometer data from mobile phone that used in order to identify movement patterns of person and verify that mobile phone wasn’t stolen or used by other person in various authentication actions.

## Problems

Reasons of Identity Theft

Human being all the time was the most vulnerable part in account/identity theft

Passwords are vulnerable to brute force attacks, more than 60% of passwords using common letters and patterns

Fingerprint protection vulnerable to fingerprint modelling using a photo of hands

Face recognition systems vulnerable to twins faces and highly detailed model of fake face

In decentralized world where people controlling their accounts and identities those systems has to be protected from possible frauds

## Solution

Client side algorithm to identify movement pattern:

In-house FFT (Fast Fourier Transform) algorithm. JS-algorithm that calculating FFT on provided data that returns Fourier Transform of movement waves.

Abstract DIST variable that finds out the difference between peak frequencies. Abstract variable used for identifying average distance between peak values that shows deviation of analysed patterns

Peak frequency identification. Identification of frequency peaks that shows artefacts in movement process (similar to fraud detection) 

Mobile Application with our integrated FFT-DIST algorithm and sensor data collection

## We learned

FFT-algorithm coded in JavaScript

## Extra resources

https://openbooks.itmo.ru/read_ntv/3824/3824.pdf - ITMO university publication
https://drive.google.com/file/d/1IvwFv_cOmABEzD1_TggWlqSf7FAJVryr/view?usp=sharing - presentation

