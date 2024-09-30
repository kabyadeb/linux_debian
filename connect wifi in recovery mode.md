Connecting to a Wi-Fi network in recovery mode on Ubuntu involves a few steps using the command line. Here’s how to do it:

### 1. Boot into Recovery Mode

1. Restart your computer.
2. Hold the `Shift` key after the BIOS/UEFI screen to access the GRUB menu.
3. Select "Advanced options for Ubuntu" and then choose the recovery mode option.

### 2. Drop to Root Shell

- From the recovery menu, select "root" to access a root shell.

### 3. Identify Your Wireless Interface

- Check your network interfaces:
  ```
  ip a
  ```
- Look for an interface that resembles `wlan0` or similar.(Replace `wlan0` with your actual wireless interface name.)

### 4. Install `wpa_supplicant` (if necessary)

- If `wpa_supplicant` isn’t available, you might need to install it. However, installation in recovery mode is limited. You might need to ensure it's already present in your normal installation.

### 5. Create a Configuration File for Wi-Fi

- Create a configuration file for your Wi-Fi network:
  ```
  nano /etc/wpa_supplicant.conf
  ```
- Add the following lines, replacing `your_SSID` and `your_password` with your network details:
  ```plaintext
  network={
      ssid="your_SSID"
      psk="your_password"
  }
  ```
- Save and exit (in `nano`, use `CTRL + X`, then `Y`, and `Enter`).

After creating the `wpa_supplicant.conf` file, you need to use it to connect to the Wi-Fi network. Here are the next steps to get your network running:

### 6. Start `wpa_supplicant`

Now that you have created the Wi-Fi configuration file, you can start the `wpa_supplicant` service to connect to the network.

Run `wpa_supplicant` with the configuration file you created. Replace `wlan0` with your actual wireless interface name if it is different:

```bash
wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf
```

- `-B` makes `wpa_supplicant` run in the background.
- `-i wlan0` specifies the wireless interface.(🤔 it may differ in your computer system.)
- `-c /etc/wpa_supplicant.conf` specifies the path to the configuration file.

### 7. Obtain an IP Address

Once the `wpa_supplicant` process is running, you need to obtain an IP address using the DHCP client.

     Run the following command to request an IP address:

```bash
dhclient wlan0
```

This will assign your system an IP address if the connection to the network is successful.

### 8. Verify the Connection

You can check if you are connected to the network by pinging a remote server (like Google). For example:

```bash
ping google.com
```

If the ping command returns responses, your internet connection is working.

[If you cannot ping `google com` ? check ](https://github.com/kabyadeb/linux_debian/blob/main/%23%23%23%20If%20you%20cannot%20ping%20%60google.md)

### 9. Exit Recovery Mode

Once connected to the Wi-Fi network, you can exit recovery mode ( if your work is done ) and reboot into normal mode if needed:

```bash
reboot
```

Your system should now boot normally with the network connection established.
