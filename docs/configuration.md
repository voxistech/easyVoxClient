# Configuration and Operation

The interface supports English, Dutch and French. The console and notification emails use English.

## Connections

Create or edit a connection with the server address, account credentials and exchange root folder. Check the connection's enabled state before saving.

The connection editor has three tabs:

- **General:** server, account and default paths.
- **Partners:** optional per-partner aliases, transfer switches and directory overrides.
- **Validation:** effective directories and access checks for the current form values.

Synchronizing partners into the local configuration is optional. It is useful only when specific partner settings are needed. The directory test fetches the current partner list from the server without saving that list locally.

Default exchange paths are `root / alias / export` and `root / alias / import`. When no alias is configured, the server account name replaces the alias. Partner-specific paths take priority. For imports, a general default import path takes priority over the root/alias path when the partner has no specific import path.

An optional sent-file archive receives successfully uploaded files. With no archive configured, successfully uploaded files are deleted from the export directory. Review this setting before running a real exchange.

## Directory Validation

Opening the validation tab only inspects the locally known paths. The explicit test authenticates to retrieve server partners, creates missing directories, and creates then deletes an empty temporary file in each accessible directory. Created directories are kept for future exchanges.

Results are grouped into general directories, then individual partners with their export, import and optional archive paths. Existence, listing access, temporary-file creation and deletion are reported separately.

The test does not upload, download or modify existing message files. If partner retrieval fails, it does not create directories. Failed creation or cleanup is reported, including the path of a temporary file that could not be removed.

The results describe access for the account currently running the client. They do not guarantee access for another scheduled-task account or permissions on every existing file. Directory access may change after the test.

## Settings and Notifications

Proxy and SMTP settings are in Settings, with separate test buttons. For email, configure at least the SMTP server, port, sender and recipient, as well as any required authentication or transport settings. Select the desired error/status notification options and send a test email before relying on notifications.

## Execution

The Connections tab can start all enabled connections or a single selected connection. Results appear in Execution, where the run can be stopped. Starting a new execution clears the previous display.

Unsaved changes trigger a choice before execution. Closing the application also distinguishes an unchanged configuration from unsaved changes. Closing only the browser window is not a reliable way to stop a local background server; use the application's shutdown action or Ctrl+C in its console.

For scheduled console executions, use the same saved configuration and an account with access to the required paths. Console closing delay and retry settings are configurable. Do not schedule overlapping executions against the same export directories.

## Certificates

The Certificates tab generates local key material, a self-signed certificate and a certificate-signing request, with a validity choice from one to five years. It does not yet replace account/password authentication to the existing V2 server. A generated certificate is not automatically trusted by a server.

Private keys are stored locally and are not encrypted at rest by a system vault. Their protection and any extra access for scheduled-task accounts are the machine administrator's responsibility. Never upload these keys to this repository or send them to support.
