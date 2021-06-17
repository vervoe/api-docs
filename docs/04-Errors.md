# Errors

For indicating request success or failure we use HTTP response codes. Codes in the 2\** range are used to indicate success. 4\** codes indicate an error. In rare cases codes in the 5** range indicate Vervoe Api servers error.

### Codes summary:
- **200** - OK Indicate the request success.
- **400** - Bad Request Indicate malformed request (probably missing or not properly named parameters)
- **403** - Forbidden, The API User doesn't have needed permissions to perform the request.
- **404** - Not Found The requested resource doesn't exist.
- **500** - Server Error Something went wrong on Vervoe API servers. This is a very rare one.