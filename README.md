
## ipid
Interplanetary Identifiers (ipid) -  Implementation of the DID ( decentralized identifiers) specification over the IPFS (Interplanetary File System) network. 
_by Jonathan Holt_

## Functional Requirements 

Save the DDO onto IPNS (Interplanetary Name Service)
- IPNS is a permissioned distributed hash table that resolves to ipfs resources
- cryptographically secure namespace resolution


**The Inter-Planetary Naming System (IPNS)**

ipns is a way to add a small amount of mutability to the permanent immutability that is ipfs. It allows you to store a reference to an ipfs hash under the namespace of your peerID ( the hash of your public key ). The commands to set it up are quite simple.

First, you'll need some content to publish:

DID syntax (globally unique cryptographically verifiable identifiers)

![alt did example using sovrin method specification](https://ipfs.io/ipfs/QmYEgzjp4K1ZBXZ4y6VDQKCnUsTgdoatA31f6HnpLsXi1E "did example from sovrin")

instead for ipid: 

![alt did example using ipid method specification](https://ipfs.io/ipfs/QmUcX32r44k3KJ1PMtQD3YqRfvqHHrEEiogmnEGstUEjA6 "did example from ipid")


*where* 
- ipid represents the method spec 
- 'QmeJGfbW6bhapSfyjV5kDq5wt3h2g46Pwj15pJBVvy7jM3' represents the IPNS (Interplanetary Name Space) which is a base58 hash that resolves to the IPFS hash of the DDO 
 

## sample DDO used by sovrin.org:
```
{ "@context": "https://schema.org/did/v1",
"id": "did:sov:21tDAKCERh95uGgKbJNHYp",
"owner": [{ 
  "id": "did:sov:21tDAKCERh95uGgKbJNHYp#key-1",
  "type": ["CryptographicKey", "EdDsaPublicKey"],
  "curve": "ed25519",
  "expires": "2017-02-08T16:02:20Z",
  "publicKeyBase64": "lji9qTtkCydxtez/bt1zdLxVMMbz4SzWvlqgOBmURoM="
}, {
  "id": "did:sov:21tDAKCERh95uGgKbJNHYp#key-2",
  "type": ["CryptographicKey", "RsaPublicKey"],
  "expires": "2017-03-22T00:00:00Z",
  "publicKeyPem": "----BEGIN PUBLIC KEY-----\r\nMIIBOgIBAAJBAKkbSUT9/Q2uBfGRau6/XJyZhcF5abo7b37I5hr3EmwGykdzyk8GSyJK3TOrjyl0sdJsGbFmgQaRyV\r\n-----END PUBLIC KEY-----"
}],
  "control": [{
  "type": "OrControl",
  "signer": [ "did:sov:21tDAKCERh95uGgKbJNHYp", "did:sov:8uQhQMGzWxR8vw5P3UWH1j" ]
}],
  "service": {
  "openid": "https://openid.example.com/456",
  "xdi": "https://xdi.example.com/123"
},
  "created": "2002-10-10T17:00:00Z",
  "updated": "2016-10-17T02:41:00Z",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20Z",
    "creator": "did:sov:8uQhQMGzWxR8vw5P3UWH1j#key/1",
   "signatureValue": "IOmA4R7TfhkYTYW87z640O3GYFldw0yqie9Wl1kZ5OBYNAKOwG5uOsPRK8/2C4STOWF+83cMcbZ3CBMq2/gi25s="
}}
```

_"@context is JSON-LD for linking attributes solving semantic interoperability"_


## sample DDO stored using did method spec stored on ipid:  


```
{ "@context": "/ipfs/QmfS56jDfrXNaS6Xcsp3RJiXd2wyY7smeEAwyTAnL1RhEG",
"id": "did:ipid:QmeJGfbW6bhapSfyjV5kDq5wt3h2g46Pwj15pJBVvy7jM3",
"owner": [{ 
  "id": "did:ipid:QmeJGfbW6bhapSfyjV5kDq5wt3h2g46Pwj15pJBVvy7jM3",
  "type": ["CryptographicKey", "EdDsaPublicKey"],
  "curve": "ed25519",
  "expires": "2017-02-08T16:02:20Z",
  "publicKeyBase64": "lji9qTtkCydxtez/bt1zdLxVMMbz4SzWvlqgOBmURoM="
}, {
  "id": "did:ipid:QmeJGfbW6bhapSfyjV5kDq5wt3h2g46Pwj15pJBVvy7jM3/key-2",
  "type": ["CryptographicKey", "RsaPublicKey"],
  "expires": "2017-03-22T00:00:00Z",
  "publicKeyPem": "----BEGIN PUBLIC KEY-----\r\nMIIBOgIBAAJBAKkbSUT9/Q2uBfGRau6/XJyZhcF5abo7b37I5hr3EmwGykdzyk8GSyJK3TOrjyl0sdJsGbFmgQaRyV\r\n-----END PUBLIC KEY-----"
}],
  "control": [{
  "type": "OrControl",
  "signer": [ "did:eth:0xd3382e07f2173270ef43817ab1b4e1cdeb36f23b", "did:sov:8uQhQMGzWxR8vw5P3UWH1j" ]
}],
  "service": {
  "did": "did:eth:0x641073322a9aa53fcf025587f86226fe358da1ef2c2e4dcb989d610e9dbf6b9a",
},
  "created": "2017-09-24T17:00:00Z",
  "updated": "2018-09-24T02:41:00Z",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20Z",
    "creator": "did:ipid:QmeJGfbW6bhapSfyjV5kDq5wt3h2g46Pwj15pJBVvy7jM3",
   "signatureValue": "IOmA4R7TfhkYTYW87z640O3GYFldw0yqie9Wl1kZ5OBYNAKOwG5uOsPRK8/2C4STOWF+83cMcbZ3CBMq2/gi25s="
}}
```


## sample verifiable claim that references a did used for prooving physician credentials:  
```
{
   "@context": "/ipfs/QmfS56jDfrXNaS6Xcsp3RJiXd2wyY7smeEAwyTAnL1RhEG",
   "id": "did:ipid:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
   "type": [
       "Credential",
       "ProofOfLicenseCredential"
   ],
   "issuer": "did:ipid:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
   "issued": "2017-09-23",
   "claim": {
       "id": "did:method:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
       "LicenseCode": 4004, 
       "proof" : "did:eth:0xd3382e07f2173270ef43817ab1b4e1cdeb36f23b"
   },
   "signature": {
       "type": "RsaSignature2016",
       "created": "2017-09-23T21:19:10Z",
       "creator": "did:ipid:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
       "nonce": "598c63d6",
       "signatureValue": "IOmA4R7TfhkYTYW87z640O3GYFldw0yqie9Wl1kZ5OBYNAKOwG5uOsPRK8/2C4STOWF+83cMcbZ3CBMq2/gi25s="
   }
}

```

## sample verifiable claim that references a did used for prooving a Vaccination:  
```
{
   "@context": "/ipfs/QmfS56jDfrXNaS6Xcsp3RJiXd2wyY7smeEAwyTAnL1RhEG",
   "id": "did:ipid:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
   "type": [
       "Credential",
       "ProofOfVaccinationCredential"
   ],
   "issuer": "did:ipid:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
   "issued": "2017-09-23",
   "claim": {
       "id": "did:method:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
       "VacinationCode": 123, 
       "proof" : "did:eth:0xd3382e07f2173270ef43817ab1b4e1cdeb36f23b"
   },
   {
   "signature": {
       "type": "RsaSignature2016",
       "created": "2017-09-23T21:19:10Z",
       "creator": "did:ipid:QmbFuwbp7yFDTMX6t8HGcEiy3iHhfvng89A19naCYGKEBj",
       "nonce": "598c63d6",
       "signatureValue": "IOmA4R7TfhkYTYW87z640O3GYFldw0yqie9Wl1kZ5OBYNAKOwG5uOsPRK8/2C4STOWF+83cMcbZ3CBMq2/gi25s="
   }
}
```
