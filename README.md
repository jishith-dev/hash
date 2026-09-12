# hash

A lightweight hashing library for Zen.

Provides SHA-256, SHA-512, HMAC-SHA256, and HMAC-SHA512 hashing with hexadecimal string output.

## Installation

```bash
zen install hash
```

## Usage

```zen
import (Hash) from "lib.zen"

Hash hash
```

### SHA-256

```zen
string result = hash.sha256("hello")
screen(result)
```

Output:

```text
2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
```

### SHA-512

```zen
string result = hash.sha512("hello")
screen(result)
```

Output:

```text
9b71d224bd62f3785d96d46ad3ea3d73319bfbc2890caadae2dff72519673ca72323c3d99ba5c11d7c7acc6e14b8c5da0c4663475c2e5c3adef46f73bcdec043
```

### HMAC-SHA256

```zen
string result = hash.hmacSha256(
    "The quick brown fox jumps over the lazy dog",
    "key"
)

screen(result)
```

Output:

```text
f7bc83f430538424b13298e6aa6fb143ef4d59a14946175997479dbc2d1a3cd8
```

The arguments are:

```text
hmacSha256(message, key)
```

### HMAC-SHA512

```zen
string result = hash.hmacSha512(
    "The quick brown fox jumps over the lazy dog",
    "key"
)

screen(result)
```

Output:

```text
b42af09057bac1e2d41708e48a902e09b5ff7f12ab428a4fe86653c73dd248fb82f948a549f7b791a5b41915ee4d1ec3935357e4e2317250d0372afa2ebeeb3a
```

The arguments are:

```text
hmacSha512(message, key)
```

## API

| Method | Description |
|---|---|
| `sha256(string)` | Returns the SHA-256 digest as a hexadecimal string |
| `sha512(string)` | Returns the SHA-512 digest as a hexadecimal string |
| `hmacSha256(string, string)` | Returns an HMAC-SHA256 digest as a hexadecimal string |
| `hmacSha512(string, string)` | Returns an HMAC-SHA512 digest as a hexadecimal string |

## Example

```zen
import (Hash) from "lib.zen"

Hash hash

string message = "hello"
string key = "secret"

screen("SHA-256:")
screen(hash.sha256(message))

screen("SHA-512:")
screen(hash.sha512(message))

screen("HMAC-SHA256:")
screen(hash.hmacSha256(message, key))

screen("HMAC-SHA512:")
screen(hash.hmacSha512(message, key))
```

## Hashing vs HMAC

SHA-256 and SHA-512 are cryptographic hash functions:

```text
message → SHA-256 → digest
message → SHA-512 → digest
```

HMAC additionally uses a secret key:

```text
message + secret key → HMAC-SHA256 → digest
message + secret key → HMAC-SHA512 → digest
```

Use HMAC when you need a keyed integrity/authentication mechanism.

## Security

This package provides cryptographic hashing primitives through Zen's native `crypto` runtime.

Do not use SHA-256 or SHA-512 directly for storing passwords. Password storage should use a password-specific password hashing algorithm such as bcrypt or another modern password hashing scheme designed for that purpose.

## License

MIT
