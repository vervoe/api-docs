# Using Vervoe APIs and Authentication

Vervoe APIs allow developers to request and send information to and from Vervoe.

To access Vervoe’s API you need to be on an Enterprise plan or be a Vervoe Partner. To learn more about the API solution or to set up your access please contact: [sales@vervoe.com](mailto:sales@vervoe.com).


## API Requests and Authentication Request Method
All API requests <strong>must</strong> be made over HTTPS. The https://api.vervoe.com/api URL is the request base URL. The complete URL varies depending on the accessed resource. All API requests <strong>must</strong> also be authenticated by Vervoe.  

Vervoe uses tokens to authenticate the API users. Those tokens must be sent on every API request in the header as “`Authorization: Bearer <\token>`”.

*When using the example above, be sure to remove the `\`*

### Authentication API Request:

To obtain your token you must make a <strong>HTTP GET</strong> request to the: https://api.vervoe.com/api/public/ats-api/token URL.   

<!--
title: "Authorization request header"
lineNumbers: true
-->
#### Request header:
`Authorization: Basic <\Base64 encoded apiKey:secretKey>`

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
