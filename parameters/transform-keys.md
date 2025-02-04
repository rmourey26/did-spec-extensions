# Extension DID Parameter: transformKeys

This specification defines a DID URL parameter for transforming verification method types.

## Status

Work-in-progress

## Syntax

The parameter name is `transformKeys`. Possibles values are any verification method type (see [DID Spec Registries](https://w3c.github.io/did-spec-registries/#verification-method-types) for a list), as well as the special values `jwk` and `jwks`.

## Definition

This DID parameter instructs a DID URL dereferencer to return the verification methods in the DID document in
a specific format.

TODO

## Examples

 * `did:example:123?transformKeys=JsonWebKey2020`
 * `did:example:123?transformKeys=jwk`
 * `did:example:123?transformKeys=jwks`
 * `did:example:123?transformKeys=jwk#keys-1`

To get a DID document with verification methods transformed to **JsonWebKey2020**:

```
curl -H "Accept: application/did+ld+json" -X GET "https://resolver.svip.danubetech.com/1.0/identifiers/did:sov:WRfXPg8dantKVubE3HX8pw?transformKeys=JsonWebKey2020"
```

Example DID document with verification methods transformed to **JsonWebKey2020**:

```
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/suites/ed25519-2018/v1",
    "https://w3id.org/security/suites/x25519-2019/v1",
    "https://w3id.org/security/suites/jws-2020/v1"
  ],
  "id": "did:sov:WRfXPg8dantKVubE3HX8pw",
  "authentication": [
    "did:sov:WRfXPg8dantKVubE3HX8pw#key-1"
  ],
  "assertionMethod": [
    "did:sov:WRfXPg8dantKVubE3HX8pw#key-1"
  ],
  "keyAgreement": [
    "did:sov:WRfXPg8dantKVubE3HX8pw#key-agreement-1"
  ],
  "verificationMethod": [
    {
      "type": "JsonWebKey2020",
      "id": "did:sov:WRfXPg8dantKVubE3HX8pw#key-1",
      "publicKeyJwk": {
        "kid": "did:sov:WRfXPg8dantKVubE3HX8pw#key-1",
        "kty": "OKP",
        "crv": "Ed25519",
        "x": "7kqc5NnojHJHZ11Ec5cGCLMIKgJVDBKhrAbu9YrfVFg"
      }
    },
    {
      "type": "JsonWebKey2020",
      "id": "did:sov:WRfXPg8dantKVubE3HX8pw#key-agreement-1",
      "publicKeyJwk": {
        "kid": "did:sov:WRfXPg8dantKVubE3HX8pw#key-agreement-1",
        "kty": "OKP",
        "crv": "X25519",
        "x": "1KHivX4x0Pf8Odhs_vCAptOCWXzeo9fIFKfhIwdKhCc"
      }
    }
  ]
}
```

To get a JWK Set (use **transformKeys=jwks** and Accept header):

```
curl -H "Accept: application/jwk-set+json" -X GET "https://resolver.svip.danubetech.com/1.0/identifiers/did:sov:WRfXPg8dantKVubE3HX8pw?transformKeys=jwks"
curl -H "Accept: application/jwk-set+json" -X GET "https://resolver.svip.danubetech.com/1.0/identifiers/did:ion:EiClkZMDxPKqC9c-umQfTkR8vvZ9JPhl_xLDI9Nfk38w5w?transformKeys=jwks"
curl -H "Accept: application/jwk-set+json" -X GET "https://resolver.svip.danubetech.com/1.0/identifiers/did:key:z6Mkfriq1MqLBoPWecGoDLjguo1sB9brj6wT3qZ5BxkKpuP6?transformKeys=jwks"
```

## Interaction with other DID Parameters

TODO

## Related Resources

 * https://identity.foundation/did-siop/#example-4
 * https://identity.foundation/did-siop/#example-8

## Contribute

Contributions to this document can be discussed in the DIF I&D Working Group:

 * https://identity.foundation/working-groups/identifiers-discovery.html
 * https://dif.groups.io/g/id-wg/
