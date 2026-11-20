# qcrypt-ocaml
Store short secret information in your docs, base64 format, encrypt/decrypt with command line tool.
The salt usage makes shure every new encryption of same password and same cleartext generates a different output.

# encryption scheme
encrypt:
- read cleartext
- read password (no echo)
  - read salt from dev/urandom
  - create mask: sha512 hash from (password, salt)
  - XOR cleartext and mask using cleartext.length() 
  - print base64 encoded salt:resultmask

# decryption
Decryption is the same logic, using existing salt, password and resultmask

# is this crackable?

Since the mask is effectively a random bitmask you cannot derive any information or structure from the output.

Not true? You tell me.
