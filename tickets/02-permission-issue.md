# Ticket 02 - Permission issue

> This is a fictional learning case based on a realistic SaaS support scenario.

## Simulated Customer Report

The customer reports that one user cannot access the reports page.

Customer message:

> One of our users gets a permission error when opening the reports page. Other users in the same team can access it without problems.

## Initial Questions

* What exact error message does the user see?
* Is only one user affected?
* Can other users in the same organization access the reports page?
* Did the user recently change role or team?
* Was the user newly invited to the workspace?
* Which browser is the user using?

## Reproduction Steps

1. Check the affected user's account.
2. Confirm the user is in the correct organization/workspace.
3. Open the reports page with a test account.
4. Compare the affected user's role with a working user.
5. Check if the reports feature is enabled for the organization.
6. Check if the affected user has the required permission.

## Investigation

The issue affects only one user. Other users in the same organization can access the reports page.

This means the reports feature itself is working. The issue is most likely related to the affected user's role or permissions.

Checked items:

* Workspace assignment
* User role
* Team assignment
* Reports permission
* Feature availability
* Browser/session issue

## How I Would Verify This

In a real support tool, I would verify this by checking:

* the affected user's role
* the affected user's workspace or organization
* whether a working user has a different role
* whether the reports feature is enabled for the organization
* whether the user recently changed team or permissions
* whether the error appears in another browser or session

## Root Cause

The affected user had the role "Viewer".

This role can access the dashboard, but it does not include permission to open the reports page.

Users need the "Manager" or "Admin" role to access reports.

## Fix / Workaround

The customer's workspace admin should update the user's role from "Viewer" to "Manager" if the user needs access to reports.

Suggested steps:

1. Open organization settings.
2. Go to Users.
3. Select the affected user.
4. Change the role from "Viewer" to "Manager".
5. Ask the user to log out and log in again.

## Example Customer Response

Hi,

Thanks for the details.

I checked the affected user and the reports page itself is working correctly. The issue is related to the user's current role.

The user currently has the "Viewer" role. This role can access the dashboard, but it does not include permission to open the reports page.

To fix this, an admin in your organization can change the user's role to "Manager" if the user should have access to reports.

After the role change, the user should log out and log in again.

Best regards,
Till

## Internal Engineering Note

No engineering escalation needed.

Reason:

* Only one user is affected
* Other users can access reports
* Reports feature is available
* No system error found
* Issue is caused by user role permissions

Possible product improvement:

The error message could be clearer. Instead of only showing "Permission denied", the product could show:

> Your current role does not include access to Reports. Please contact your workspace admin.

## What I Learned

A permission issue does not always mean that something is broken.

Before escalating, I should compare the affected user with a working user and check:

* role
* permissions
* workspace
* team assignment
* feature access

This case helped me understand how role-based access issues can look like product errors from the customer's perspective.
