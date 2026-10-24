# Installation and Startup

## Windows

1. Choose the processor architecture and edition. `windows-amd64` is for Intel/AMD 64-bit Windows; ARM64 and 32-bit machines have separate packages. Select **Browser** when the machine has a maintained modern browser, or **Desktop** to include the browser engine.
2. Extract the complete ZIP into a directory chosen by the machine administrator. Do not run the application from inside the ZIP.
3. Open `easyvox-ui.cmd`. Browser opens the machine's default browser; Desktop opens its own window.

There is no installer or uninstaller. Both ZIP editions contain `easyvox.exe`, two launchers and legal notices. Only Desktop contains a `WebView2` directory. Keep the complete extracted Desktop folder together. Browser contains no embedded engine, does not require an installed WebView2 runtime and does not download one at startup. Its executable uses only the local browser for its interface.

The Desktop ZIP is much larger because it includes the complete engine for its processor architecture. The exchange features are the same in both editions. Offline availability of the Desktop interface does not remove the need for connectivity to the exchange server. The bundled engine does not update itself: install newer Desktop packages to receive its updates. A maintained default browser receives updates through its normal administrator-managed update mechanism. Internet Explorer is not supported.

Alternative launchers:

- `easyvox-browser.cmd`: starts the local interface in the default browser in either edition. In Browser it is equivalent to `easyvox-ui.cmd`. Keep its console open; Ctrl+C stops the local server.
- `easyvox.exe`: runs the configured connections in console mode. Double-clicking does not open the configuration interface and may exchange files using the saved configuration.

The Desktop UI launcher uses local port 8089; Browser launchers use local port 8088. Do not start both launchers at the same time against the same exchange folders. The console remains available in both editions.

Neither edition modifies existing permissions or ACLs. Some Windows 10 environments require administrator-prepared read access for the embedded engine; see [Microsoft's fixed-runtime deployment guidance](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/distribution#the-fixed-version-runtime-distribution-mode). The administrator is responsible for any required permission preparation. Including an engine does not make unsupported operating-system versions compatible.

## macOS and Linux

Extract the package for the machine's processor. From the extracted directory, run:

```sh
./easyvox -ui -addr 127.0.0.1:8088
```

Open `http://127.0.0.1:8088/ui/` in a local browser. Press Ctrl+C in the terminal to stop the server. The application is bound to the loopback address; it is not intended to expose the configuration interface on a public network.

For a console execution:

```sh
./easyvox
```

## Shared Application Data

Default application-data directories:

| Platform | Directory |
| --- | --- |
| Windows | `%ProgramData%\VoxisTechnologies\EasyVoxClient` |
| macOS | `/Library/Application Support/VoxisTechnologies/EasyVoxClient` |
| Linux | `/var/lib/easyvox-client` |

The configuration file is `Configuration.json`. The application log is `Application.log` beside the selected configuration file. Local certificate material is kept in a `Certificates` subdirectory of the application-data directory unless explicitly overridden.

The application uses the rights of the account running it. It does not create user accounts, change ownership or modify existing directory permissions or ACLs. Ask the machine administrator to prepare access when needed, including access for a different scheduled-task account.

An explicit configuration file can be selected with `-config`:

```powershell
.\easyvox.exe -config "D:\EasyVoxData\Configuration.json"
```

```sh
./easyvox -config "/path/to/Configuration.json"
```

`-config` changes the selected configuration file, not the default certificate directory. `EASYVOX_CONFIG_DIR` overrides the default application-data directory; `EASYVOX_CERTIFICATES_DIR` independently overrides the certificate directory.

Back up the configuration and certificate material securely before moving to another machine. Keep real configuration files and private keys out of public repositories.
