# Ticket 03 - API returns 401

> This is a fictional learning case based on a realistic SaaS support scenario.

## Simulated Customer Report

The customer reports that their integration suddenly returns a 401 Unauthorized error.

Customer message:

> Our integration suddenly returns 401 Unauthorized. It worked yesterday, but today our requests are failing.

## Initial Questions

- When did the issue start?
- Is every API request failing or only one endpoint?
- Was the API key or token changed recently?
- Which endpoint is affected?
- Which environment is used: production or sandbox?
- Can the customer share the request headers without exposing secrets?
- Is there an error response body?

## Reproduction Steps

1. Check the affected endpoint.
2. Review the request method and URL.
3. Check if the Authorization header is included.
4. Confirm that the token or API key is not expired.
5. Compare the failing request with a working example.
6. Test the request in Postman with a valid token.

## Investigation

A 401 Unauthorized response usually means the request is not correctly authenticated.

The API endpoint itself is available, but the request is rejected before access to the resource is granted.

Checked items:

- Authorization header
- API token format
- Token expiration
- API key status
- Correct environment
- Recent credential changes
- Difference between 401 and 403

Example failing request:

```http
GET /api/v1/reports HTTP/1.1
Host: api.example-saas.com
Authorization: Bearer expired_token
