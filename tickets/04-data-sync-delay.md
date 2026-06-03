# Ticket 04 - Data sync delay

> This is a fictional learning case based on a realistic SaaS support scenario.

## Simulated Customer Report

The customer reports that newly imported data is not visible in the dashboard.

Customer message:

> We imported new data from our integration this morning, but it is still not showing in the dashboard. The import did not show an error.

## Initial Questions

* When was the data imported?
* Which integration or source system was used?
* Is all imported data missing or only some records?
* Does the import history show a successful import?
* Are other users affected?
* Is the data missing everywhere or only in the dashboard?
* Was this the first import or did it work before?

## Reproduction Steps

1. Check the customer's workspace.
2. Review the latest import or sync status.
3. Check the timestamp of the last successful sync.
4. Compare imported records with visible dashboard data.
5. Check if the dashboard uses cached or delayed data.
6. Verify whether the data appears after refreshing or waiting.

## Investigation

The customer did not receive an import error, so the upload itself was probably successful.

The dashboard is loading normally, but the new data is not visible yet. This suggests that the issue may be related to delayed processing or dashboard refresh timing.

Checked items:

* Import status
* Last sync timestamp
* Dashboard refresh time
* Processing delay
* Affected workspace
* Whether older data is still visible
* Whether other users see the same result

## How I Would Verify This

In a real support tool, I would verify this by checking:

* whether the import job completed successfully
* when the last sync finished
* whether the imported records exist in the system
* whether the dashboard has already refreshed after the import
* whether there are failed background jobs
* whether the issue affects only one customer or multiple customers

## Root Cause

The imported data was successfully received, but the dashboard had not refreshed yet.

The system processes imported data in the background before it appears in the dashboard. In this case, the sync job was delayed, so the dashboard still showed the previous data state.

## Fix / Workaround

The customer should wait for the sync job to finish or trigger a manual refresh if available.

Suggested steps:

1. Check the import status.
2. Wait until the sync status shows completed.
3. Refresh the dashboard.
4. If available, trigger a manual sync.
5. Contact support again if the data is still missing after the expected processing time.

## Example Customer Response

Hi,

Thanks for reporting this.

I checked the import status and the data was received successfully. The reason it is not visible in the dashboard yet is that the dashboard data is updated after the background sync process has finished.

Please wait until the sync status shows as completed and then refresh the dashboard. If the data is still missing after the expected processing time, let me know and I will continue investigating.

Best regards,
Till

## Internal Engineering Note

No engineering escalation needed at this stage.

Reason:

* Import was successful
* Dashboard loads correctly
* No error message was found
* Issue appears related to delayed background processing
* Data should appear after sync completion

Escalation would be needed if:

* the sync job remains stuck
* multiple customers are affected
* imported records are missing from the system
* the dashboard does not update after successful sync completion

Possible product improvement:

The dashboard could show a clearer sync status message, for example:

> New data is still being processed. This may take a few minutes.

## What I Learned

Missing data does not always mean that the import failed.

Before treating this as a bug, I should check:

* import status
* sync status
* last successful update
* dashboard refresh timing
* whether the data exists but is not visible yet

This case helped me understand that SaaS systems often use background jobs, and support needs to explain processing delays clearly to customers.
