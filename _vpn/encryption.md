---
layout: page
title: Encryption
order: 3
---
The last article went over the properties that make a secure connection. Encryption is used to fulfil some of those properties, and here we'll go over the more in-depth details.









## Encryption

The goal of encryption is to prevent a block of data from being read, except by the intended recipient.

When looking at data encryption, there are a few terms that are good to know:

* **Plaintext**: Regular data. Text, images, etc before they are encrypted. e.g. `"What does the fox say?"`
* **Ciphertext**: Encrypted data. Text, images, etc after they've been encrypted. e.g. `^Lwpi sdth iwt udm hpn$^`

You take **plaintext**, encrypt it to produce **ciphertext**, and then can decrypt that ciphertext to get the original **plaintext**. For example:

![Encryption Cipher]({{ site.baseurl }}/img/articles/vpn-security/encryption-cipher.svg "Encryption Cipher")

Along with the data to encrypt, most methods of encryption also let you specify a key to encrypt the data with. To decrypt the data, you also need to know the key that was used to encrypt it.

### Ciphers

An _encryption cipher_ is what you use to encrypt and decrypt data. To be more exact, an encryption cipher takes plaintext (along with some other information such as the key) and produces ciphertext. And similarly, takes ciphertext and produces plaintext.

There are many different encryption ciphers out there, each with their own levels of security and uses. Some, for instance, are focused on being fast (and appropriate for encrypting up to 50MB/s of data in realtime), and others are focused on being more secure (but are much slower).

There are different types of encryption ciphers – symmetric and asymmetric. In symmetric encryption, the same key is used to encrypt and decrypt the data; in asymmetric encryption, different keys are used to encrypt, and to decrypt, the data. Both are useful for different reasons, so let's go over where each is used.

#### Symmetric Encryption Ciphers

A symmetric encryption cipher uses the same key to both encrypt and decrypt data, and are the ones most commonly used today.

Symmetric ciphers are typically more efficient than asymmetric ones, meaning that they encrypt and decrypt data more quickly. Because of this, symmetric ciphers are used when you want to encrypt a large amount of data.

The main downside of symmetric ciphers is that the key needs to be the same. This means that you need to transmit the key between both endpoints before data can be securely encrypted and decrypted using that key.

#### Asymmetric Encryption Ciphers

An asymmetric encryption cipher uses different keys to encrypt and decrypt data, and are not as commonly-used. They're also typically slower than symmetric ciphers.

The main upside of asymmetric ciphers is that there are ways for two machines to open communications, and to then exchange this key information between the two of them without anyone in the middle being able to work out the actual keys being used on either side.






## Encryption Ciphers

VPNs encrypt traffic between the client computer and the gateway. To do this, it uses an encryption cipher so that only the client and our gateway can find out what the traffic in the middle is.


## Authentication Hashes


## Handshake Encryption


## Active Attacks


## Passive Attacks


## Ephemeral Keys
