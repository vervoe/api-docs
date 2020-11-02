---
tags: [Endpoints]
---

# Report Notification WebHook

Employer user can set reporting webhook. To this webhook Assessment Report will be sent. There are list of events that fire webhook update:

- CANDIDATE_START_INTERVIEW
- CANDIDATE_COMPLETE_INTERVIEW
- AI_SCORE
- MANUAL_SCORE
- MANUAL_SCORE_CHANGED

### Request

<!--
title: "Request Body example"
lineNumbers: true
-->

```json
{
        "candidateAssessmentUuid": "cbb3e136-ef30-4452-955b-1835a79caa65",
        "status": "complete",
        "startedAt": "2020-03-10T08:39:46+00:00",
        "completedAt": "2020-03-10T08:39:58+00:00",
        "score": {
            "type": "TYPE_MANUAL",
            "score": 100,
            "scoreByFormat": 100
        }
        "integrationCandidateCardUrl": "https://api.vervoe.com/integration_candidate_card"
}
```

### Response

The consumer of webhook must send http 200 response to notify Vervoe api that the report is successfully received. If response not equals to 200 Vervoe api will try to send the report. 

### How to verify verify webhook signatures

The Vervoe API is signing the webhook data which is sent to API user endpoints. It is done by including a signature in the request Vervoe-Signature header. This allows API user to verify that the data coming from webhook was sent by Vervoe, not by a third party.

Before you can verify signatures, you need to retrieve your webhook secret from your Vervoe dashboard’s API webhook settings.

The Vervoe-Signature header contains a timestamp and one signature. The timestamp is prefixed by `t=`, and signature is prefixed by `hash=`.

    Vervoe-Signature: t=1494224576,hash=5257a869e7ecebeda32affa62cdca3fa51cad7e77a0e56ff536d0ce8e108d8bd

Signatures are generated using a hash-based message authentication code ([HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)) with [SHA-256](https://en.wikipedia.org/wiki/SHA-2).

1.  **Extract the timestamp and signatures from the header**
    Split the `Vervoe-Signature` header, using the `,` character as the separator. And then split each element, using the `=` character as the separator. The value  `t`  value corresponds to the request time (in unix timestamp format), and `hash` corresponds to the signature.

2.  **Prepare the payload for hashing**
    Payload for caching can be obtained by concatenating `t` value (request time) from the `Vervoe-Signature` header with a dot character `'.'` and with the actual request body.

3.  **To compute the expected signature:**
    Compute a HMAC with the SHA256 hash function. Use the endpoint’s signing secret as the key, and use the payload string from the previous step as the message.

4.  **Check:**
    If the signature in the header and the expected signature matches, compute the difference between the current timestamp and the received timestamp `t`. If the difference is within your tolerance you can process request data.
