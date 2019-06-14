
## IPID Interplanetary Identifiers 
**(ipid)** is and implementation of the DID (decentralized identifiers) specification over the IPFS (Interplanetary File System) network using the IPNS (Interplanetary Name Service) cryptographic namespace resolution service. 

**_by Jonathan Holt, Founder TranSendX_**

[IPFS](https://ipfs.io)  is a peer-to-peer distributed file system that seeks to connect all computing devices with the same system of files. 
[IPNS](https://github.com/ipfs/faq/issues/16) is a mutable namespace resolution over the distributed hash table that is control by the peerID and associated public key.

While IPFS and IPNS are not specifically designed for the creation and management of decentralized identifiers (DIDs) and the associated DDO/DID Document it can easily used for this purpose. 

The ipid method of the DID specification built on top of IPFS and IPNS is a truly self-sovereign identifiers that may be used by people, organizations, and digital devices to establish a cryptographic identifier and associated distributed public key infrastructure that is truly under their control and does not require a third party agent to resolve.
Updating the DDO could be done manually by updating the DDO/DID Document and re-publishing to the IPNS namespace controlled by the public key. 

## Functional Requirements 

Save the DDO onto IPNS (Interplanetary Name Service)
- IPNS is a permissioned distributed hash table that resolves to a ipfs resource
- cryptographically secure namespace resolution, in this case of a DID document

## DEMO

[Presentation](https://www.youtube.com/watch?v=nAoheXEXckQ) on IPID method spec from the Rebooting the Web of Trust conference in Cambridge, MA on October 4th, 2017.  

[![Presentation from Rebooting Web of Trust](https://img.youtube.com/vi/nAoheXEXckQ/0.jpg)](https://www.youtube.com/watch?v=nAoheXEXckQ "Presentation from Reboot Web of Trust")



## DID Method Specification

[DIDs (decentralized identifiers)](https://w3c-ccg.github.io/did-spec/) are a new type of identifier intended for verifiable digital identity that is "self-sovereign", i.e., fully under the control of the identity owner and not dependent on a centralized registry, identity provider, or certificate authority. DIDs resolve to DDOs (DID descriptor objects)—simple JSON documents that contain all the metadata needed to prove ownership and control of a DID. Specifically, a DDO contains a set of key descriptions, which are machine-readable descriptions of the identity owner’s public keys, and a set of service endpoints, which are resource pointers necessary to initiate trusted interactions with the identity owner. Each DID uses a specific DID method, defined in a separate DID method specification, to define how the DID is registered, resolved, updated, and revoked on a specific distributed ledger or network.

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
 

## Using IPNS ## 

To add a DID document to IPNS, publish it to your peer id

>$ echo "< DID Document text >" | ipfs add 
>$ <HASH> 
>$ ipfs name publish <HASH>



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

## DID universal resolver

[link](https://www.github.com/) **Discussed at the RebootingWebofTrust conference** 


## References

1. [IPFS white paper](https://github.com/ipfs/papers/raw/master/ipfs-cap2pfs/ipfs-p2p-file-system.pdf) Juan Benet (protocol labs).
2. [Sovrin](http://sovrin.org)
