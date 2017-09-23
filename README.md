
## ipid
Interplanetary Identifiers (ipid) -  Implementation of the DID ( decentralized identifiers) specification over the IPFS (Interplanetary File System) network. 


## Functional Requirements 

Save the DDO onto IPNS (Interplanetary Name Service)
- given the IPNS is a permissioned filestore 

DID syntax (globally unique cryptographically verifiable identifiers)

![alt did example](https://ipfs.io/ipfs/QmYEgzjp4K1ZBXZ4y6VDQKCnUsTgdoatA31f6HnpLsXi1E "did example from sovrin")

instead for ipid: 

![alt did example](https://ipfs.io/ipfs/QmUcX32r44k3KJ1PMtQD3YqRfvqHHrEEiogmnEGstUEjA6 "did example from ipid")


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

- "@context is JSON-LD for linking the semantic interoperability"


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


