primecheck
==========

This is a script that will check primes for Diffie Hellman key exchanges.
It currently does two things:
* Check whether the prime is a known, widely used prime
* Check whether the prime is a safe prime

usage
=====

Send hostnames plus (optionally port) on stdin, one per line. Get JSON output
to stdout:

echo "www.foo.com\nwww.bar.net:8080" | ./primecheck

notes on openssl usage
======================

As I am not aware of an easy way to extract diffie hellman parameters from a TLS
connection with any readily available Python API I'm using OpenSSL compiled with
the enable-ssl-trace option. This is not on by default, therefore I bundled a
pre-compiled openssl binary. If you don't trust me you may recompile OpenSSL
yourself with trace support and replace the openssl-trace binary.

background
==========

The Logjam Attack and the corresponding research identified several problems in the use of
Diffie Hellman key exchanges.

https://weakdh.org/
