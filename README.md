# XchangE

This was a CTF style sceurity challenge I made for INCTF Nationals Finals 2021.

It is broadly based on the Diffie-helman key exchange (DHKX) algorithm to enable two parties to securely generate a shared secret which can then be applied to key derivation function (KDF) to generate cryptogrpahically secure keys for use in further encryption algorithms. 

More specifically this challenge illustrates the use of man in the middle (MITM) attack on DHKX to retrieve the shared sceret key thus compromisng any further encrypted communications by the participating parties on use of this now exposed shared secret.

This is a real world vulnerability or more to point an intentional flaw incrporated by telegram into its proposed End-to-End Encryption Algorithm MTProto, which precluded the claim by telegram on MTProto being a secure E2E algorithm to secure chat messages by allowing Telegram servers to act as a man in the middle and thus enabling it with enough knowledge on the secure exchange between the two parties for it to generate the same shared secret as generated by the participating parties thereby compromisin privacy.

> PS: This has then been fixed and newer versions of the algorithm are devoid of this flaw

To play around with this challenge follow the below steps to get the application running: 

```bash
git clone this repo

cd Deployment

sudo docker build -t xchange .

sudo docker run -d -p 1337:1337 --rm xchange
```

