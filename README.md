# Anpheros FHIR R4 Healthcare API: OpenAPI spec and Postman collection

**OpenAPI 3.1 specification and a Postman collection for the Anpheros healthcare API**: a managed HL7 FHIR R4 server
plus a simpler REST API on the same data, with patient consent (OAuth 2.1 / SMART App Launch), provenance on every
write, International Patient Summary (IPS) and SMART Health Links. EU-hosted, with a free FHIR sandbox of 30 synthetic patients.

| File | What it is |
|---|---|
| [`openapi.json`](openapi.json) | OpenAPI 3.1 spec of the public API: `/fhir/R4`, `/v1`, `/oauth`, `/shl` |
| [`postman/anpheros-fhir-api.postman_collection.json`](postman/anpheros-fhir-api.postman_collection.json) | Postman v2.1 collection (also imports into Bruno, Insomnia and Hoppscotch) |

## Quick start in 2 minutes

1. **Get a free sandbox key.** Sign in on the [dashboard](https://platform.anpheros.com/dashboard/?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi) and press **Get a sandbox key** (`sk_test_…`). Your sandbox comes with 30 synthetic patients and six months of history.
2. **Call the FHIR API:**

   ```bash
   curl -H "Authorization: Bearer $ANPHEROS_KEY" \
     "https://platform.anpheros.com/fhir/R4/Patient?_count=3"
   ```

3. **Or import the collection** into Postman, set the `apiKey` variable to your key and run any request.

The same spec is served live at [`platform.anpheros.com/openapi.json`](https://platform.anpheros.com/openapi.json),
and the FHIR CapabilityStatement at [`/fhir/R4/metadata`](https://platform.anpheros.com/fhir/R4/metadata).

## Generate a client

```bash
npx @openapitools/openapi-generator-cli generate -i openapi.json -g python -o anpheros-python
```

Official SDKs already exist for TypeScript and Dart / Flutter: [anpheros-sdk](https://github.com/anpheros/anpheros-sdk).

## What the API covers

- **FHIR R4 (4.0.1)**: read, search, history, transactions, `Patient/$everything`, `Patient/$summary` (IPS) and `$validate` across 26 resource types (Patient, Observation, Condition, MedicationStatement, AllergyIntolerance, Immunization, DocumentReference, Encounter, Procedure, DiagnosticReport…).
- **REST v1**: patients, observations, conditions, medications, documents, timeline, lab report import (CSV, HL7 v2 ORU^R01), terminology (LOINC, ATC) and an AI context endpoint.
- **OAuth 2.1 / SMART App Launch** with PKCE, so an app reaches a person's record only with their consent.
- **SMART Health Links** for sharing a record by link or QR code.

## Guides

[Getting started](https://developers.anpheros.com/guides/getting-started?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi) ·
[FHIR sandbox](https://developers.anpheros.com/guides/fhir-sandbox?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi) ·
[Healthcare API](https://developers.anpheros.com/guides/healthcare-api?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi) ·
[EHR API](https://developers.anpheros.com/guides/ehr-api?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi) ·
[API reference](https://developers.anpheros.com/docs?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi)

The spec is regenerated from the running platform, so it changes when the API changes. Anpheros is a data API: it
stores and shares health records and does not diagnose or give treatment advice.

Apache-2.0 · [anpheros.com](https://anpheros.com/?utm_source=github&utm_medium=readme&utm_content=fhir-api-openapi)
