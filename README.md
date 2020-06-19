# did-jose-extensions

Best practices for working with JOSE and Decentralized Identifiers.

### Examples

#### DID Document

```json
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    {
      "@base": "did:example:alice"
    }
  ],
  "id": "did:example:alice",
  "publicKey": [
    {
      "type": "JsonWebKey2020",
      "id": "#3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac",
      "controller": "",
      "publicKeyJwk": {
        "crv": "P-384",
        "x": "6lYjpT7z8dbCV4cieg5AJkgZ0IeBuhmKFfSzv0DP8ZcG3rMbimsHfK6YJ53u9JGC",
        "y": "LaPvN-O7BW9jfkW2oOe0Lg_rFpISDZn7vtgMkahpWEu0lB9i--nMAmjIUaxHu56B",
        "kty": "EC",
        "kid": "3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac"
      }
    }
  ],
  "authentication": ["#3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac"],
  "assertionMethod": ["#3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac"],
  "capabilityDelegation": ["#3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac"],
  "capabilityInvocation": ["#3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac"],
  "keyAgreement": ["#3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac"]
}
```

#### Vanilla JWT

```json
{
  "header": {
    "kid": "3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac",
    "alg": "ES384"
  },
  "payload": {
    "sub": "did:example:alice",
    "iss": "did:example:alice",
    "boring_vanilla_claim": "with no semantic or cannonicalization support...",
    "iat": 1592600790
  },
  "signature": "swm5-7tD3Ch-OzgZ1_ZmsLwLtZgubGQEJVGWVVfqyjPrUDQ4aU4Y7kvhm4Ioe2s-6P6NMnBrMv1Os05UnfQqDqNXz1UNVNYVg0h6ov9QKdKZNyuMAfD11n4eKUY-8cW5",
  "key": {
    "kid": "3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac",
    "crv": "P-384",
    "x": "6lYjpT7z8dbCV4cieg5AJkgZ0IeBuhmKFfSzv0DP8ZcG3rMbimsHfK6YJ53u9JGC",
    "y": "LaPvN-O7BW9jfkW2oOe0Lg_rFpISDZn7vtgMkahpWEu0lB9i--nMAmjIUaxHu56B",
    "kty": "EC"
  }
}
```

#### VC-JWT

```json
{
  "header": {
    "kid": "3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac",
    "alg": "ES384"
  },
  "payload": {
    "sub": "did:example:alice",
    "iss": "did:example:alice",
    "nbf": 1586814292,
    "exp": 1904939092,
    "vc": {
      "@context": [
        "https://www.w3.org/2018/credentials/v1",
        "https://identity.foundation/.well-known/contexts/did-configuration-v0.0.jsonld"
      ],
      "issuer": "did:example:alice",
      "issuanceDate": "2020-04-13T16:44:52-05:00",
      "expirationDate": "2030-05-13T16:44:52-05:00",
      "type": ["VerifiableCredential", "DomainLinkageCredential"],
      "credentialSubject": {
        "id": "did:example:alice",
        "domain": "identity.foundation"
      }
    },
    "iat": 1592600728
  },
  "signature": "j1sKh9V_TZ1CCvDUfhjmuwjHXWg-0enm0iTmcW56YZ7V-Yk_WU8EEOZzOvuDPHE7zwP08UvnBWfxnbFeMjBuH4T8e9AiqCRjBg9HQHfgSuV-sb-_W49iBdeGaXfJnYFJ",
  "key": {
    "kid": "3Set2I7Yj7T2-E6qTuSu34DMVPbYD3EIbEGfD2KU8Ac",
    "crv": "P-384",
    "x": "6lYjpT7z8dbCV4cieg5AJkgZ0IeBuhmKFfSzv0DP8ZcG3rMbimsHfK6YJ53u9JGC",
    "y": "LaPvN-O7BW9jfkW2oOe0Lg_rFpISDZn7vtgMkahpWEu0lB9i--nMAmjIUaxHu56B",
    "kty": "EC"
  }
}
```

#### JWE

```json
{
  "protected": "eyJlbmMiOiJBMTI4Q0JDLUhTMjU2In0",
  "recipients": [
    {
      "header": {
        "alg": "ECDH-ES+A256KW",
        "epk": {
          "kty": "EC",
          "crv": "P-384",
          "x": "Com5-QGtzotMIY75HV8Te1jaT8tA7oo1jJiXutYFCDEEpPAOmFC4_CXzbecm3u_R",
          "y": "63S18T5JZ48ZUmMQvJm_bA40VnuyRRpXtK-HbcZNERWksmadwi9PtZBSboCAtbDB"
        }
      },
      "encrypted_key": "3Gz9D-ZCpobtU1kpWlK24j0emTe8VFux3FlhucEiaBXSXGjyydDoGA"
    },
    {
      "header": {
        "alg": "ECDH-ES+A256KW",
        "epk": {
          "kty": "EC",
          "crv": "P-384",
          "x": "UoXqVY_SjmBixJemeOiy4QU7zRoe7fCQ-_10GEw7v6gaViw-g2gQ00x5Q8wiMj8a",
          "y": "1-2F3VCTGMtMeWbaxSu5nkaa3wBltWqSzczBGZnAA6j8ojeP1ujIIdvV0BGlpeio"
        }
      },
      "encrypted_key": "dp9ywiGO-ZhoyfrH5SEJU3duvu60xDv_rmK6zbPZ8KwHk9TYN1ot1Q"
    },
    {
      "header": {
        "alg": "ECDH-ES+A256KW",
        "epk": {
          "kty": "EC",
          "crv": "P-384",
          "x": "UHFeB0usmoLObj9KyXwYdB5bieEnj7Ry2XSArB8kitmnJ8orkJxJ4k8ZyUiwouTY",
          "y": "-tNL5ULbtTHBIWozERbXzgISe4JLZ0CCE_xhETUsniz1Nl2yfntrmNJroHHf1mgn"
        }
      },
      "encrypted_key": "rKUUrBCLPv31tYpJbJwfshU-IodeqcpSqXyQDOgr4DC6NK48aPIm5g"
    }
  ],
  "iv": "9yic6nusaOi_bjf4ZR-DHw",
  "ciphertext": "IlKAaxdhYczHjoiyLYLSkcuDtzf-hsGVDWJs6rCwNSM",
  "tag": "sXK-b6Zmh59KqwK-MB8VRg"
}
```

#### JWE from Encrypted Data Vault

```json
{
  "ciphertext": "3SHQQJajNH6q0fyAHmw....",
  "iv": "QldSPLVnFf2-VXcNLza6mbylYwphW57Q",
  "protected": "eyJlbmMiOiJYQzIwUCJ9",
  "recipients": [
    {
      "encrypted_key": "BMJ19zK12YHftJ4sr6Pz1rX1HtYni_L9DZvO1cEZfRWDN2vXeOYlwA",
      "header": {
        "alg": "ECDH-ES+A256KW",
        "apu": "Tx9qG69ZfodhRos-8qfhTPc6ZFnNUcgNDVdHqX1UR3s",
        "apv": "ZGlkOmVsZW06cm9wc3RlbjpFaUQ3ZXlJdU9pekRDY3lvbzBkc25kZmp6ODNOMzUtb29GNWN4cGNqQllBbV9nI1hJR3NkZmlGZTk3MVNWTmFDTEhldnY1aGp3ZkZBQURRbW1ERFZOM2xVX2cjekMxUm51dnc5clZhNkU1VEtGNHVRVlJ1UXVhQ3WZ0I4MVVtMnUxN0Z1N1VLNA",
        "epk": {
          "crv": "X25519",
          "kty": "OKP",
          "x": "Tx9qG69ZfodhRos-8qfhTPc6ZFnNUcgNDVdHqX1UR3s"
        },
        "kid": "did:elem:ropsten:EiD7eyIuOizDCcyoo0dsndfjz83N35-ooF5cxpcjBYAm_g#XIGsdfiFe971SVNaCLHevv5hjwfFAADQmmDDVN3lU_g#zC1Rnuvw9rVa6E5TKF4uQVRuQuaCpVgB81Um2u17Fu7UK"
      }
    }
  ],
  "tag": "xbfwwDkzOAJfSVem0jr1bA"
}
```
