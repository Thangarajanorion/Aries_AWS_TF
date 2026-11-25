Thanks! Yes, PEM format works. The simplest and most secure option would be for your team to import it directly into AWS Certificate Manager in account 387340471575, region us-east-2, and share the certificate ARN with us. That way, the private key doesn't need to be sent.

If you'd prefer to send the files instead, we need three PEM files:

The certificate for aries.cloud.aep.com
The private key (unencrypted, without a passphrase)
The certificate chain (the intermediate certificate(s))

Please share the private key through a secure channel (not by email), and we'll delete it once it's imported.
