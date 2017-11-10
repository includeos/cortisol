# cortisol
Cortisol is a tool to run arbitrary performance benchmarks and log data to a google sheet

IncludeOS uses this internally to track performance over time. Tests can be written in any language.

Cortisol uses [gspread] to log data to Google Sheets.


## Tests

The test is given a parameter, typically test host to run against. The first line of output is the primary metric delivered by the test. Any following output will be added to the sheet as unprocessed text.


## Authentication and authorization

We use a Google API Service Account to auth/authz against the Google Sheet API. Each service account has a client_email which you'll find in the JSON file describing the service account.  Share your sheet with this email. It'll look something like this: cortisol@random-string-238237.iam.gserviceaccount.com


How to set up:
 * Set up the Service Account
 * Place the JSON file in the directory, naming it cortisol-service-acct.json
 * Create a sheet
 * Make sure the cell A1 contains the magic string ('This sheet is machine generated') so cortisol will allow itself to write to the sheet
 * Place tests in the tests/ folder
 * Set up tests.json and enter your tests and your targets
 * Do a test run, fix any errors
 * place cortisol in a cron job



[gspread]: https://github.com/burnash/gspread