---
title: "Generate passwords and encrypt/decrypt content in Linux"
datePublished: Sat May 04 2024 07:47:10 GMT+0000 (Coordinated Universal Time)
cuid: clvrswhng000209l58nbk79k5
slug: generate-passwords-and-encryptdecrypt-content-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714808817573/450ec83b-ca27-4b69-89f5-d31fe8623f56.jpeg
tags: linux

---

OpenSSL is one of the utilities available with all major Linux distributions. We can use the same to encrypt and decrypt passwords in Linux to protect sensitive data.

**Generate Random Passwords**

We can utilities like mkpasswd or pwgen to generate random passwords if needed:

```bash
# generates multiple 8-character passwords
pwgen

# generates single random password
makepasswd

# generates multiple 12-character passwords
pwgen 12
makepasswd --chars=12

# generates specified 12-character passwords, say 5
pwgen 12 5
makepasswd --chars=12 --count=5
```

**Generate Encrypted/Hashed Passwords**

We can generated encrypted passwords with utilities like makepasswd:

```bash
# generates 12-character password and encrypted password with crypt algorithm
makepasswd --chars=12 --crypt

# generates 12-character password and encrypted password with crypt algorithm + salt
makepasswd --chars=12 --crypt --cryptsalt=20

# generates 12-character password and encrypted md5 password
makepasswd --chars=12 --crypt-md5
```

With openssl, we can generated hashed-passwords for supplied password as input:

```bash
# generates hashed password with crypt algorithm
openssl passwd -crypt my_password

# generates hashed password with crypt algorithm + salt
openssl passwd -crypt -salt my_salt my_password

# generates hashed md5 password
openssl password -1 my_password

# generates hashed sha-256/512 password
openssl password -5 my_password
```

**Encrypting Contents with OpenSSL**

Lets say we have a file with some sensitive content. We can encrypt sensitive content, say “my\_content” with openssl with different encryption algorithms in the below manner:

```bash
# encrypt string with algorithm pbkdf2 with randomly generated salt and input password
echo "my_content" | openssl enc -pbkdf2 -a -salt -pass pass:my_password

# decrypt string (encoded as above)
# note: just add parameter -d to above openssl parameters
echo "bXlfY29udGVudAo=" | openssl enc -pbkdf2 -a -d -salt -pass pass:my_password

# encrypt string with algorithm aes-256-cbc with randomly generated salt and input password
echo "my_content" | openssl enc -aes-256-cbc -a -salt -pass pass:my_password

# decrypt string (encoded as above)
# note: just add parameter -d to above openssl parameters
echo "U2FsdGVkX19MdDInWumh31tKJoqR5HQwSXlxj3NiRC8=" | openssl enc -aes-256-cbc -a -d -salt -pass pass:my_password
```

```bash
user@d7e5dc06581c:~$ echo "my_content" | openssl enc -pbkdf2 -a -salt -pass pass:my_password
bXlfY29udGVudAo=

user@d7e5dc06581c:~$ echo "bXlfY29udGVudAo=" | openssl enc -pbkdf2 -a -d -salt -pass pass:my_password
my_content

user@d7e5dc06581c:~$ echo "my_content" | openssl enc -aes-256-cbc -a -salt -pass pass:my_password
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
U2FsdGVkX19MdDInWumh31tKJoqR5HQwSXlxj3NiRC8=

user@d7e5dc06581c:~$ echo "U2FsdGVkX19MdDInWumh31tKJoqR5HQwSXlxj3NiRC8=" | openssl enc -aes-256-cbc -a -d -salt -pass pass:my_password
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
my_content
```