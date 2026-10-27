# DeHub downloads

DeHub is a self-hosted media library for movies, series, and anime. Run it on one computer, then watch from a browser or the Android app on other devices in your home.

**[Open the latest release](https://github.com/IWLED/DeHub-releases/releases/latest)** to download the file for your device.

## Which file should I choose?

| Device | File in the release | What it does |
| --- | --- | --- |
| Windows PC hosting your library | `DeHub-Server-<version>-windows-x64-setup.exe` | Runs in the background; use a browser on this or other devices. |
| Windows PC with a desktop window | `DeHub-Desktop-<version>-windows-x64-setup.exe` | Runs the server and interface in one app. |
| Linux server (Intel/AMD) | `dehub-server-<version>-linux-x86_64.tar.gz` | Server archive with an `install.sh` script. |
| Linux server (ARM64) | `dehub-server-<version>-linux-aarch64.tar.gz` | Server archive for 64-bit ARM devices. |
| Linux desktop (Intel/AMD) | `DeHub-Desktop-<version>-linux-x86_64.AppImage`, `DeHub-Desktop-<version>-linux-amd64.deb`, or `DeHub-Desktop-<version>-linux-x86_64.rpm` | Desktop app; choose the package for your distribution. |
| Android phone or tablet | `DeHub-<version>-android.apk` | Client app; needs a DeHub server. The latest APK may be in an earlier release. |
| Android TV / Google TV | `DeHub-TV-<version>-android.apk` | TV client with remote control navigation; needs a DeHub server. |
| Docker host | `ghcr.io/iwled/dehub:latest` | Server container; configure persistent data and media volumes. |

**Server** hosts your library. **Desktop** includes the server and opens its own window. `x64`, `x86_64`, and `amd64` all mean 64-bit Intel/AMD; `aarch64` means ARM64.

Set up the server on one device, then open `http://<server-address>:3000` from other devices on the same network. For a Windows server without an installer, choose `dehub-server-<version>-windows-x86_64.zip` under release assets.

The installed app can update from **Settings → Updates**. Each release includes `SHA256SUMS` for verifying downloads.
