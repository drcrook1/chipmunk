# Project Chipmunk

Chipmunk is an implementation of Confidential Field Level Network Traversal. Essentially what this does is intercepts remote requests and encrypts specific fields on the client prior to transmitting to the server.

## How it works

We write a series of "interceptors" across multiple client languages which essentially overrites all remote calls, starting with a prioritized list. There is a configuration file which defines destinations which need protection, pacakge formats that need protection and fields that need protection. The interceptor essentially does the following steps.

- intercepts remote call with parameters
- checks configuration for if host is a destination needing protection
- checks for local public key and expiration (if not, then get it)
- Attest remote server using remote attestation of Confidential Machinery & configuration
- encrypts fields in remote call according to the configuration
- executes remote call using original library but with modified contents
- returns response per normal

## Repository Layout

- Samples Folder contains all sample applications leveraging the installable packages
- src contains all the source code for each sdk/library implementation
