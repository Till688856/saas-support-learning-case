# Ticket 01 - User sees no data
> This is a fictional learning case based on a realistic SaaS support scenario.
## Simulated Customer Report

The customer can log in, but the dashboard is empty.

Customer message:

> I can log in, but I don't see any data on my dashboard. Yesterday everything was working normally.

## Initial Questions

- Do you see an empty dashboard or an error message?
- Did this start today?
- Are other users affected?
- Did you change any filters or date ranges?
- Which browser are you using?
- Which workspace or organization are you logged into?

## Reproduction Steps

1. Log in with a test user.
2. Open the dashboard.
3. Check if the dashboard loads.
4. Compare the affected user with another working user.
5. Check filters and selected date range.
6. Check user permissions and organization assignment.

## Investigation

The login works, so the issue is probably not related to authentication.

The dashboard loads, but no data is shown. This means the page itself works, but the user may not have access to the expected data or the selected filters return no results.

Checked items:

- Account status
- Organization/workspace assignment
- User permissions
- Dashboard filters
- Selected date range
- Other users in the same organization

## Root Cause

The user had selected a future date range. Because there was no data for that period, the dashboard appeared empty.

## Fix / Workaround

The user should reset the dashboard filters or select a valid date range, for example:

- Last 30 days
- This month
- Last quarter

After refreshing the dashboard, the data should appear again.

## Example Customer Response

Hi,

Thanks for reporting this.

I checked your account and the dashboard itself is working correctly. The issue was caused by the selected date range. It was set to a period where no data exists, so the dashboard appeared empty.

Please change the date range to "Last 30 days" or "This month" and refresh the dashboard. The data should then be visible again.

Let me know if the issue still appears after changing the filter.

Best regards,  
Till

## Internal Engineering Note

No engineering escalation needed.

Reason:

- Login works
- Dashboard loads correctly
- No system error found
- Other users are not affected
- Issue is related to selected filters

Possible product improvement:

Show a clearer empty-state message:

> No data found for the selected date range. Try changing your filters.

## What I Learned

An empty dashboard does not always mean the system is broken.

Before escalating, I should check simple causes first:

- filters
- date ranges
- permissions
- workspace assignment
- whether other users are affected
