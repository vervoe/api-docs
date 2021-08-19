# Using Vervoe APIs

Vervoe APIs allow developers to request and send information to and from Vervoe.

Access to Vervoe’s API is for Enterprise customers and Partners. To learn more about the API solution or to set up your access please contact: [sales@vervoe.com](mailto:sales@vervoe.com).


## Authentication 
Each HTTP request made to the Vervoe API must be authenticated by Verveo. 

Vervoe uses tokens to authenticate the API users. Those tokens must be sent on every API request in the header as “Authorization: Bearer <\token>”.

*When using the example above, be sure to remove the `\`*

To obtain the token following endpoint must be used:

 @Rest\Get ("https://api.vervoe.com/api/public/ats-api/token")

#### Request headers:

<!--
title: "Authorization request header"
lineNumbers: true
-->

```
Authorization: Basic <\Base64 encoded apiKey:secretKey>
```
```
Authorization: Basic <\Base64 encoded apiKey:secretKey>
```
*When using the example above, be sure to remove the `\`*

#### Response:

```json
{
    "success": true,
    "data": {
        "token": "7He9ABtS1t6LLhOTyAr3M0uvF1mTa4w2r7koKVx83s373khNVtXp-WK3ufXuYasSc4mpUVwo0X4jcxpB1JBh4YRLN3bppvd_F-POMUCZPWGYIP7jz7h47cnD4Db9hqP2b4JdvO4N8y7bpqz6gcYnz6huSAHNy0ADEGWoqR5PvMpWeZBBrqzi8lHE4rgV4g9KBDp-bUbLybsuy-cvI1ueD4W5YUzd55-nn80fvBhAMDH5r18CVoIiSjY4CfTO7GY-bNUvLE4AMFk27XwyCxhJJ-uY4katIuQwkdB4vfECPYNFbXVPOiUtGL1K5Y5IzPCxKpn9ApfOeVDFSoXYectASVGu4wqcU1AnHtL54hdcYyQJXfX9fBB0owXxuPWLaRJlVQhUUNAGSfp5owbtSxpf0PmeynuDlUdOM2hFbSGXyx5RzycwkTM1LDiIKKgYCHirqswrgX7mBxQXfXo3U3GXobAQsxRwFOPTqvPWrrSXGIjfna1_x4rGb_XvWEtwzmYOX02cZH2Q0A5Vcql0tDRyHBovU7s6Y"
    }
}
```
<!-- theme: warning -->

> Token expiration time is **10 minutes**. After that time api user must obtain a new token using above mentioned endpoint.

**Then use this token in Authorization header like this:**

Authorization: Bearer <\token>

*When using the example above, be sure to remove the `\`*

**For the API requests containing JSON data please include the Content-Type header:**

Content-Type: application/json
