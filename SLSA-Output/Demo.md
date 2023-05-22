# Demo SLSA Output Verification

- `shasum -a 256 MyAwesomePDFGenerator.1.0.0.nupkg bom.json`
- `cat multiple.intoto.jsonl | jq -r '.payload' | base64 -d > provenance.json`
- `cat multiple.intoto.jsonl | jq -r '.signatures[0].cert' > pub.crt`