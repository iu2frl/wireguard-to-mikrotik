# wireguard-to-mikrotik

Converts Wireguard conf to Mikrotik command line instructions

## Features

- Converts WireGuard tunnel configurations in INI format to Mikrotik terminal commands.
- Generates QR codes for easy configuration on mobile devices.
- Processes all data locally in the browser, ensuring privacy and security.
- Provides a user-friendly interface with clear instructions.

## Usage

1. Open the `index.html` file in a web browser.
2. Paste your WireGuard tunnel configuration in INI format into the provided text area.
3. Click the "Translate" button to generate the Mikrotik command.
4. The resulting command will appear below the text area.
5. A QR code for the configuration will also be generated for mobile device scanning.

## Notes

- Ensure proper firewall configuration and adhere to the highest safety standards when using the generated commands.
- No data is sent or stored on the server or browser; all processing is done locally.

## Files

- `index.html`: The main HTML file providing the user interface.
- `converter.js`: The JavaScript file containing the logic for parsing INI configurations, generating Mikrotik commands, and creating QR codes.

## Example

### Input (WireGuard INI Configuration)

```ini
[Interface]
PrivateKey = <private-key>
Address = 192.168.1.1/24
ListenPort = 51820

[Peer]
PublicKey = <peer-public-key>
PresharedKey = <preshared-key>
Endpoint = 192.168.1.2:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
```

### Output (Mikrotik Command)

```bash
/interface/wireguard/add name="wg_tunnel_123" listen-port=51820 private-key="<private-key>"
/ip/address/add address="192.168.1.1/24" interface="wg_tunnel_123"
/interface/wireguard/peers/add interface="wg_tunnel_123" endpoint-address="192.168.1.2" endpoint-port="51820" public-key="<peer-public-key>" preshared-key="<preshared-key>" persistent-keepalive=25s allowed-address="0.0.0.0/0"
```

### QR Code

The QR code for the configuration will be displayed below the generated command.

## License

This project is licensed under the GNU GPL v3 License. See the `LICENSE` file for details.
