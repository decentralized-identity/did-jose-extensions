#### `kid` in JWK and JWA/JWE

1. `kid` MUST NOT be present in JWKs and MUST be present in JWA/JWE.

- ✅ `kid` is already optional in [JWK rfc7517](https://tools.ietf.org/html/rfc7517)
- ✅ `kid` would be functionally equivalent to `verificationMethod` already used in LD Proofs.

1. `kid` MAY be present in JWKs and MUST be present in JWA/JWE.

- ✅ `kid` is already optional in [JWK rfc7517](https://tools.ietf.org/html/rfc7517)
- ✅ `kid` would be functionally equivalent to `verificationMethod` already used in LD Proofs.
- ❌ Prefer to recommend MUST or MUST not and not MAY, optionality leads to bugs.

1. `kid` MAY be present in JWKs and MAY be present in JWA/JWE.

- ❌ Prefer to recommend MUST or MUST not and not MAY.

#### `kid` value in JWA/JWE

1. Its value MUST be a DID_URI

- ✅ Supports did parameters, which might include `version`
- ✅ functionally equivalent to `verificationMethod` already used in LD Proofs.

1. Its value MUST be a Fragment

- ❌ Not a key identifier without a base.
- ❌ Requires extra spec text about how to use the base.
- ❌ Does not support DID Params
- ❌ Not all JWE/JWA have a base.

#### `iss` in JWTs

1. Its value MUST be a DID_URI

- ✅ Supports did parameters, which might include `version`
- ❌ Many possible values, lots of bugs and attack vectors.

1. Its value MUST be a DID

- ✅ Simple issuer identifier, does not preclude `kid` being a DID URI
- ✅ functionally equivalent to VC Data Model

#### JWT overlapping fields with VC Data Model

1. Values MUST be repeated in both expected places

- ✅ Objects need not be tranformed to be handled consistently
- ❌ Objects are larger

1. Values MUST only be present in the JWT places.

- ✅ Objects are smaller (but still rely on base64url lol)
- ❌ Objects neeed to be transformed to be handled consistently
- ❌ Why not just use a vanilla JWT?
- ❌ No spec text for resolution via `iss`
- ❌ No spec text for resolution via `sub`

#### JCS vs Stringify

1. Values SHOULD be cannonized with JCS

- ✅ Objects can be hashed and signed safely https://tools.ietf.org/html/rfc8785
- ❌ Who cares?

1. Values MAY be converted to string in any order.

- ❌ Who cares?

#### JsonWebKey2020 vs \_\_VerificationKey2020

1. Key type SHOULD NOT be included in the key name.

- ✅ matches the semantic intention of "this is a JOSE key"
- ✅ avoids redundant semantic annotation from verification relationship, type and key representation.
- ✅ only need to update a supported table, no need to register new linked data things

1. Key type SHOULD be included in the key name.

- ✅ how most (but not all) other keys have been registered
- ❌ Who cares?
