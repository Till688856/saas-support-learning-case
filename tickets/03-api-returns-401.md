# Ticket 03 - API returns 401

> This is a fictional learning case based on a realistic SaaS support scenario.

## Simulated Customer Report

The customer reports that their integration suddenly returns a 401 Unauthorized error.

Customer message:

> Our integration suddenly returns 401 Unauthorized. It worked yesterday, but today our requests are failing.

## Initial Questions

* When did the issue start?
* Is every API request failing or only one endpoint?
* Was the API key or token changed recently?
* Which endpoint is affected?
* Which environment is used: production or sandbox?
* Can the customer share the request headers without exposing secrets?
* Is there an error response body?

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

* Authorization header
* API token format
* Token expiration
* API key status
* Correct environment
* Recent credential changes
* Difference between 401 and 403

## Example Failing Request

```http
GET /api/v1/reports HTTP/1.1
Host: api.example-saas.com
Authorization: Bearer expired_token
```

## Example Response

```json
{
  "error": "unauthorized",
  "message": "The access token is expired or invalid."
}
```

## How I Would Verify This

In a real support tool, I would verify this by checking:

* whether the Authorization header is included
* whether the token is expired or revoked
* whether the token format is correct
* whether the customer is using the correct environment
* whether the same request works with a valid test token
* whether the issue is 401 Unauthorized or 403 Forbidden

## Root Cause

The customer's access token had expired.

The integration was still using the old token, so the API rejected the request with 401 Unauthorized.

## Fix / Workaround

The customer should generate a new access token and update the integration configuration.

Suggested steps:

1. Open API settings.
2. Generate a new access token.
3. Replace the old token in the integration.
4. Save the configuration.
5. Retry the API request.
6. Set a reminder or process to rotate tokens before they expire.

## Example Customer Response

Hi,

Thanks for the details.

I checked the error and the API endpoint itself appears to be available. The 401 Unauthorized response is caused by the access token used in the request.

The token is expired or no longer valid. Please generate a new access token in the API settings and update it in your integration configuration.

After replacing the token, retry the request. The API should then accept the request again.

Best regards,
Till

## Internal Engineering Note

No engineering escalation needed at this stage.

Reason:

* API endpoint is available
* Error is authentication-related
* Response clearly indicates an invalid or expired token
* Issue can be solved by replacing the token

Possible product improvement:

The API documentation could include a clearer troubleshooting section for 401 errors.

Suggested addition:

> 401 Unauthorized usually means the token is missing, expired, invalid or sent in the wrong format.

## What I Learned

A 401 error means the request is not properly authenticated.

Before escalating API issues, I should check:

* Is the token included?
* Is the token expired?
* Is the Authorization header correct?
* Is the customer using the right environment?
* Is the issue 401 Unauthorized or 403 Forbidden?

This case helped me understand basic API authentication troubleshooting from a support perspective.
