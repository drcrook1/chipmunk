# Implementation Details

start by implementing a service worker interceptor for remote HTTP/HTTPS calls.

- intercepts remote call with parameters
- checks configuration for if host is a destination needing protection
- checks for local public key and expiration (if not, then get it)
- Attest remote server using remote attestation of Confidential Machinery & configuration
- encrypts fields in remote call according to the configuration
- executes remote call using original library but with modified contents
- returns response per normal
