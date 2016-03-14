# Plugglapp, jajamensan

## Authentication procedure

1. __Identification__ of the user (who is it?)
2. __Provision__ of some kind of authentication information, which is secret and unforgeable.
3. __Transmission__ of the authentication information to the system through a secure channel.
4. __Validation__ of the authentication information with some reference information (proof of correctness).

The authentication information can be of __3 different, generic types__, based on something that is unique for the user:

* Something you __KNOW__ (e.g password, PIN code)
* Something you __HAVE__ (e.g smartcard)
* Something you __ARE (DO)__ (e.g fingerprint), (biometrical methods, something characteristic about you)
* (__WHERE__ you are can also be used in some situations)

In general, something that you have is called a _token_. i.e. something that is used for authentication.

A __capability__ is an unforgeable token that gives the possessor certain _rights_ (to an object) - __authorization__
