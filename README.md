# ntru.js

## Overview

The [NTRU](https://github.com/NTRUOpenSourceProject/ntru-crypto) post-quantum asymmetric
cipher compiled to pure JavaScript using [Emscripten](https://github.com/kripken/emscripten).
A simple wrapper is provided to make NTRU easy to use in Web applications.

The paramater set defined in ntru.c is EES743EP1 (the highest possible security level as per
[the NTRU documentation](https://github.com/NTRUOpenSourceProject/ntru-crypto/blob/master/reference-code/C/Encrypt/doc/UserNotes-NTRUEncrypt.pdf)).
To change this, modify ntru.c and rebuild with `make`.

## Example Usage

	var plaintext	= new Uint8Array([104, 101, 108, 108, 111]); // ("hello")

	var keyPair		= ntru.keyPair();
	var encrypted	= ntru.encrypt(plaintext, keyPair.publicKey);
	var decrypted	= ntru.decrypt(encrypted, keyPair.privateKey);

Note: NTRU generally shouldn't be used to directly encrypt your data; in most cases, you'll
want to pair it with a symmetric cipher and use it to encrypt symmetric keys.
