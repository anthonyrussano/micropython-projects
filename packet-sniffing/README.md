# Packet Sniffing Project

## `sniffer_injection.py`

This script is designed to run on an ESP32-C3 device, which is a popular microcontroller with Wi-Fi capabilities. The script performs several functions related to Wi-Fi packet sniffing and packet injection. Here's a breakdown of its components and functionality:

1. **Setting CPU Frequency**:
   ```python
   machine.freq(240000000)
   ```
   This line sets the CPU frequency of the ESP32-C3 to 240 MHz.

2. **Wi-Fi Sniffing Function (`wifi_sniff`)**:
   - A function `wifi_sniff` is defined to sniff Wi-Fi packets.
   - It creates a UDP server socket bound to the localhost (`127.0.0.1`) and port `20001`.
   - It continuously receives packets from this socket and prints the received data.
   - After receiving 100 packets, it prints the current time in milliseconds and the total number of bytes received.

3. **Starting Sniffing Thread**:
   ```python
   _thread.start_new_thread(wifi_sniff, ())
   ```
   This line starts a new thread for the `wifi_sniff` function, enabling concurrent execution with the main program.

4. **Configuring Wi-Fi Interface**:
   - The script first deactivates both the Access Point (AP) and the Station (STA) interfaces of the ESP32-C3.
   - It then activates the STA interface and sets up a sniffer on channel 8 using `sta.sniffer(ch=8)`.
   - The sniffer is then stopped with `sta.sniffer_stop()`.
   - This is repeated once more.

5. **Packet Injection**:
   - The script constructs a raw Wi-Fi beacon frame (`buf`) representing a network with the SSID "ESPTEST" on channel 8.
   - It then injects this beacon frame 100 times with a delay of 0.1 seconds between each injection using `sta.inject()`.

6. **Usage of Wi-Fi Sniffer and Packet Injection**:
   - The script demonstrates both the ability to sniff Wi-Fi packets and to inject custom packets into the network.
   - The sniffing part is run in a separate thread, allowing the main program to handle packet injection simultaneously.

7. **Socket Communication**:
   - It's important to note that the script binds a UDP socket to the localhost address. This suggests that it expects to receive UDP packets sent locally, possibly from another process or script running on the same ESP32-C3 device.

8. **Practical Application**:
   - This script could be used for network analysis, testing, or educational purposes. It demonstrates low-level manipulation of Wi-Fi packets and the ESP32-C3’s capabilities in handling Wi-Fi traffic.