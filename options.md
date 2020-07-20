#### `kid` in JWK and JWA/JWE

1. `kid` MAY be present in JWKs and MUST be present in JWA/JWE.
1. `kid` MUST NOT be present in JWKs and MUST be present in JWA/JWE.
1. `kid` MAY be present in JWKs and MAY be present in JWA/JWE.

#### `kid` in JWA/JWE

1. Its value MUST be a DID_URI
1. Its value MUST be a Fragment

#### `iss` in JWTs

1. Its value MUST be a DID_URI
1. Its value MUST be a DID

#### JWT overlapping fields with VC Data Model

1. Values MUST be repeated in both expected places
1. Values MUST only be present in the vc / vp
1. Values MUST only be present in the JWT places.

#### JCS vs Stringify

1. Values SHOULD be cannonized with JCS
1. Values MAY be converted to string in any order.

#### JsonWebKey2020 vs \_\_VerificationKey2020

1. Key type SHOULD NOT be included in the key name.
1. Key type SHOULD be included in the key name.
