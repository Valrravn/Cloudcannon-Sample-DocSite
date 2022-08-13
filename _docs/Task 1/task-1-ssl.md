---
title: Task 1 - How SSL Works
category: Resume
order: 1
author: Dmitry Korovin
---

# Task 1: SSL: How It Works

Secure Sockets Layer or SSL is the network security protocol designed to ensure secure client-server connections.

## The Basics

The SSL protocol encrypts data transmitted between a server and a client, which denies attackers a chance to intercept this traffic.
Whenever a client attempts to connect to a server, the authentication\validation procedure starts.

* The client starts the process by sending the `“Client Hello”` message along with its portion of a cryptographic key.
* The server responds with the `“Server Hello” - server key portion - key agreement protocol - SSL certificate - “Server Finished”` sequence. The key agreement protocol allows both parties to agree on an encryption key in safe way, without a third-party participating in the process.
* The client checks the server’s SSL certificate legitimacy, and proceeds to combining the encryption key from client and server key portions. This final key is used to cypher data.


The entire process is called the **SSL handshake**, and the client-server connection opens only after the handshake stage was successfully passed.
If a client is unable to verify a server’s SSL certificate, the Error 525 pops up, and the connection is terminated.


## What Sites Need Certificates?

You are probably familiar with HTTP and HTTPS: different versions of the Hypertext Transfer Protocol that defines how data should be transmitted over the Internet.
The “S” letter of HTTPS stands for “secure”, and means the server uses a SSL\TLS certificate to ensure a secure connection.

Not too long ago, it was advocated that HTTPS is required only for resources that deal with sensitive information: login pages, money transaction services, online brokers, and so on.
Nowadays, HTTPS is a standard even for websites that commonly do not require state-of-the-art security measures (for instance, weather forecast or local school newspaper sites).
This transition is furthermore accelerated by Google, who started the “HTTPS everywhere” initiative in 2014.

Modern browsers automatically detect secure connections and draw a padlock icon next to the URL.
Connections to HTTP resources are flagged as unsecure, and browsers advice users to thread cautiosly.

This alone is the major reason to have an SSL certificate installed regardless of what your web-site does. As the number of cyber attacks rises and users become more aware of “digital hygiene” basics, more and more users opt for clicking “Back” when they land on insecure (meaning potentially malicious) pages.


## SSL vs TLS

The latest 3.0 version of SSL was deprecated by RFC in 2015 in favor of TLS – the more secure encryption protocol.
Technically speaking, it’s only TLS now, but the catchy SSL acronym stuck with the industry, and both terms are often used interchangeably.
If you’re not particularly nitpicking about using correct terms, you can use any of them.

## Certificate Authorities and Certificate Types

In order for the entire concept of TLS certificates to work, these certificates must come from a trusted source (otherwise, anyone could issue their own certificates and attach them to their websites).
Such valid source is called a Certificate Authority (CA) – a trusted third-party provider that issues, stores, and signs digital certificates.

Depending on the level of required protection and the number of subdomains, a CA issues different types of certificates.

Depending on the domain and subdomain number:

* Single-domain SSL
* Multi-domain SSL
* Wildcard SSL

Depending on the required security level:

* _Domain Validation (DV)_ – A CA validates the website owner only. Such certificates are issued for public resources that do not require extensive security.
* _Organization Validation (OV)_ – A CA validates the website owner and carries out minor background checks, looking into the business and the owner itself. These certificates provide improved credibility and consumer trust for businesses.
* _Extended Validation (EV)_ – A CA validates everything, up to the owner’s physical location and legal existence. Issued for critical businesses, such as digital banks or money transfer services.

Validation and protection levels affect the certificate price and time it will take to get one.

## See Also

* How to Obtain and Install a Certificate
* How to Resolve Error 525 (SSL Certificate Validation Failed)
