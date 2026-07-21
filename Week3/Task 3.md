## Task 3

### Who has issued the certificate?

With

```console
openssl s_client -connect polimi.it:443
-servername polimi.it 2>/dev/null | openssl x509
-noout -issuer
```
I find

```console
issuer=C = GB, ST = Greater Manchester, L =
Salford, O = Sectigo Limited, CN = Sectigo ECC
Organization Validation Secure Server CA
```
Which means:
the CA is based in GB (Great Britain)
in the state of Great Manchester
and the locality is Saltford;
the organization is Sectigo Limited
and the common name - that specifies the intermediate certificate
used to sign the certificate for polimi.it - is
Sectigo ECC Organization Validation Secure Server CA

### For what exact domain it has been certificated?

with

```console
openssl s_client -connect example.com:443
-servername example.com 2>/dev/null | openssl
x509 -noout -subject -ext subjectAltName
```

I find

```console
subject=C = IT, ST = Milano, O = Politecnico di
Milano, CN = 2023.polimi.it
X509v3 Subject Alternative Name:
DNS:2023.polimi.it,
DNS:dynamicpoli.polimi.it, DNS:polimi.it,
DNS:www-polimi.it, DNS:www.english.polimi.it,
DNS:www.polimi.it, DNS:www1.polimi.it,
DNS:wwwpolimi.it
```

So, the certificate country is Italy
The Politecnico di Milano organization owns the certificate, and is
based in Milan

### When does it exprire?

with

```console
openssl s_client -connect polimi.it:443
-servername polimi.it 2>/dev/null | openssl x509
-noout -enddate
```

I find

```console
notAfter=Dec 3 23:59:59 2025 GMT
```

which is clearly the expiration date

### What is the encryption algorithm and key size?

With

```console
openssl s_client -connect polimi.it:443 -servername polimi.it 2>/dev/
null | openssl x509 -noout -text | grep -E "Signature Algorithm|
Public-Key"
```

I find

```console
Signature Algorithm: ecdsa-with-SHA256
Public-Key: (256 bit)
Signature Algorithm: ecdsa-with-SHA256
```

which means the algorithm used is ECDSA (Elliptic Curve Digital
Signature Algorithm) with hash function SHA-256;
the key is 256 bit long.

### Manual validation with openssl verify with local file:

With

```console
openssl s_client -connect polimi.it:443
-servername polimi.it </dev/null 2>/dev/null |
openssl x509 -outform PEM > polimi.crt
```

a file named polimi.crt is downloaded.

Looking at the Certificate Hierarchy of the site, this is shown:
- USERTrust ECC Certification Authority 
    - Sectigo ECC Organization Validation Secure Service
        2023.polimi.it

It is possible to download the other two certificates directly from the websites
and to concatenate them into a new .crt file through

```console
cat SectigoECCDomainValidationSecureServerCA.crt
root.crt > combined.crt
```

At this point, the hierarchy can be verified with

```console
openssl verify -CAfile combined.crt polimi.crt
```

Finding some errors, I tried with

```console
cat polimi.crt SectigoECCDomainValidationSecureServerCA.crt
root.crt > combined.crt
```

but I still got

```console
error 20 at 0 depth lookup: unable to get local
issuer certificate
error polimi.crt: verification failed
```

I tried to change folders, repeat the process, but I couldn’t have a
positive answer returned.
All the files format has been checked with ‘cat’ command and the
format was correct ( -----BEGIN CERTIFICATE----- etc… )