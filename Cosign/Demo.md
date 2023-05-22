# Demo signing file with Cosign

- `COSIGN_EXPERIMENTAL=1 cosign sign-blob --rekor-url https://rekor.sigstore.dev --oidc-issuer https://oauth2.sigstore.dev/auth code-europe.txt`
- `rekor-cli get --log-index IDHERE --format json | jq > output.json`
- `cat output.json | jq -r '.Body.HashedRekordObj.signature.content' > code-europe.txt.sig`
- `cat output.json | jq -r '.Body.HashedRekordObj.signature.publicKey.content' | base64 -d > pub.crt`
- `openssl x509 -noout -text -in pub.crt`
- `COSIGN_EXPERIMENTAL=1 cosign verify-blob --cert pub.crt --signature code-europe.txt.sig code-europe.txt`