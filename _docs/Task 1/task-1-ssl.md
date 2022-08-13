---
title: "Task #1: SSL - How It Works"
category: Resume
order: 1
author: Dmitry Korovin
---

**Secure Sockets Layer** or **SSL** is the network security protocol designed to ensure secure client-server connections.

## The Basics

The SSL protocol encrypts data transmitted between a server and a client, which denies attackers a chance to intercept this traffic. Domains that support secure (HTTPS) connection must have SSL certificates installed on their servers.

Whenever a client attempts to connect to a server, it first asks the server to set up a secured connection.
There are multiple ways to for a server and client to agree to use the secure connection. Two major ways are:

* Use the specific port (for example, port 443 is used exclusively for encrypted HTTPS traffic).
* Send to server a protocol-specific request to use a secured connection.

Once both parties agree on the connection security, the procedure called `SSL handshake` starts.

1. The client sends the _"Client Hello"_ message along with its portion of a cryptographic key.
2. The server chooses a cypher and hash function from the list the client sent.
3. The server sends back the _"Server Hello" - server key portion - key agreement protocol - SSL certificate - "Server Finished"_ sequence. 
4. The client checks the server's SSL certificate legitimacy, and proceeds to combining the encryption key from client and server key portions.

If the handshake is successfull, both client and server use obtained key portions to generate encryption keys, and a secure connection opens.

Otherwise, if any stage of a handshake fails (for example, a client is unable to verify a server's SSL certificate), the connection is cancelled.

## SSL vs TLS

The latest 3.0 version of SSL was deprecated by RFC in 2015 in favor of TLS – the more secure encryption protocol. This means the "SSL" protocol is no longer exists, and you can obtain and install only TLS certificates.
However, the SSL acronym stuck with the industry, and both terms are often used interchangeably.

## Certificate Authorities

In order for the entire concept of TLS certificates to work, these certificates must come from a trusted source (otherwise, anyone could issue their own certificates and attach them to their websites).

A trusted third-party provider that issues, stores, and signs digital certificates is called **Certificate Authority (CA)**.

Three largest CAs are:

* [IdenTrust](https://www.identrust.com/)
* [Digicert](https://www.digicert.com/)
* [Comodo Cybersecurity](https://www.comodo.com/)

> See Also: Which Certificate Authority to Choose?

## Certificate Types

CAs issue different types of certificates based on the level of required protection and the number of subdomains.

Depending on the domain and subdomain number:

* Single-domain SSL
* Multi-domain SSL
* Wildcard SSL

Depending on the required security level:

* _Domain Validation (DV)_ – A CA validates the website owner only. Such certificates are issued for public resources that do not require extensive security.
* _Organization Validation (OV)_ – A CA validates the website owner and carries out minor background checks, looking into the business and the owner itself. These certificates provide improved credibility and consumer trust for businesses.
* _Extended Validation (EV)_ – A CA validates everything, up to the owner's physical location and legal existence. Issued for critical businesses, such as digital banks or money transfer services.

Validation and protection levels affect the certificate price and time it will take to obtain this certificate.


## SSL Disadvantages

Although you should always use SSL/TLS encryption, certificates exhibit a few drawback you should be aware of.

### Vulnerabilities

Newer TLS version are more secure compared to older SSL implementations. However, all versions have known implementation flaws that allow attackers to exloit them.

The list of known SSL/TLS vulnerabilities:

* POODLE
* ...
* ...

### Connection Speed Issues

Since secure connections start with the handshake stage, during which a client and server exchange data and use complex algorythms to create keys, connections open with a certain delay.
This delay is negligible if connection speeds are high, visitor traffic is low, and both parties use moderately modern hardware. Otherwise, the certificate validation can significantly impact the connection speed.

> See also: Three Tips to Avoid Bandwidth Issues

### Setup Issues

Certificates do not guarantee secure connections all by themselves. The outcome greatly depends on the specific server configuration.
SSL/TLS has an option to select a simplified, less efficient encryption method when a server is configured incorrectly, or uses outdated software.
Such connections are still marked as "secure", but have lower chances to withstand attacks form knowledgeable hackers. 

> See also: How to Correctly Configure SSL/TLS Certificates

### Plugin Compatibility

Older plugins built without HTTPS in mind can trigger SSL/TLS errors. If your domains use outdated plugins, you will require to update them or find an alternative.

## See Also

* Methods Used for Key Exchange/Agreement
* How to Obtain and Install a Certificate
* How to Resolve Error 525 (SSL Certificate Validation Failed)
