# EasyVox Client

Portable file-exchange client with a console mode and an embedded configuration interface.

**Current beta: 5.0.0021-beta.** This version is still being validated and is not a final stable release. Test it with non-production data before using it for production exchanges.

This distribution repository is intended for public documentation and packaged downloads only. Application source code, real configurations, passwords and private keys are not included.

## Documentation

- [Installation and startup](docs/installation.md)
- [Configuration and operation](docs/configuration.md)
- [Beta release notes](releases/5.0.0021-beta.md)

## Downloads

Twelve packages and `SHA256SUMS.txt` are provided with [EasyVox Client 5.0.0021-beta](https://github.com/voxistech/easyVoxClient/releases/tag/v5.0.0021-beta). This is a GitHub Pre-release, not a stable release.

### Which Windows Package?

| Edition | Choose it when | Interface | Download size |
| --- | --- | --- | --- |
| **Browser** | A modern default browser is already installed and regularly updated | Opens the local browser; no WebView2 included or required | A few MB |
| **Desktop** | No suitable modern local browser is available | Opens its own window using the included WebView2 engine | Several hundred MB |

Both editions have the same exchange, configuration and console features. Desktop is larger because it includes a complete browser engine, not because it includes additional exchange functionality. Browser is the lightweight choice for machines with a maintained browser. Internet Explorer is not suitable.

The Desktop engine is updated through newer Desktop packages, not automatically. Including it does not make unsupported Windows versions compatible. Both editions are portable ZIPs without installers or uninstallers.

| Platform | Processor | Package suffix |
| --- | --- | --- |
| Windows Browser | Intel/AMD 64-bit | `windows-amd64-browser.zip` |
| Windows Desktop | Intel/AMD 64-bit | `windows-amd64-desktop.zip` |
| Windows Browser | ARM 64-bit | `windows-arm64-browser.zip` |
| Windows Desktop | ARM 64-bit | `windows-arm64-desktop.zip` |
| Windows Browser | Intel/AMD 32-bit | `windows-386-browser.zip` |
| Windows Desktop | Intel/AMD 32-bit | `windows-386-desktop.zip` |
| macOS | Apple Silicon | `darwin-arm64.tar.gz` |
| macOS | Intel 64-bit | `darwin-amd64.tar.gz` |
| Linux | Intel/AMD 64-bit | `linux-amd64.tar.gz` |
| Linux | ARM 64-bit | `linux-arm64.tar.gz` |
| Linux | ARMv7 | `linux-armv7.tar.gz` |
| Linux | Intel/AMD 32-bit | `linux-386.tar.gz` |

The package names start with `easyvox-client-5.0.0021-beta-`. A `SHA256SUMS.txt` file accompanies the packages to check download integrity. Availability of a package does not imply that it has been tested on every operating-system version or device.

Desktop packages include the WebView2 runtime for the matching processor architecture. Keep their whole extracted directory, including `WebView2`, together. Browser packages have no `WebView2` directory and do not download one at startup. Open `easyvox-ui.cmd` to configure either edition. Required third-party legal notices are provided separately.

## Support

Contact [support@easyvox.eu](mailto:support@easyvox.eu). Include the application version and a description of the issue. Remove credentials, personal information and confidential filenames from logs before sharing them. Never send private keys.
