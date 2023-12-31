# micropython-projects

## ESP32-C3 Basic Setup

### Project Ideas

Using a MicroPython-enabled ESP32-C3 for penetration testing projects can be quite creative and educational, as it allows you to explore both the hardware and software aspects of cybersecurity. Here are some project ideas:

1. **Wi-Fi Network Scanner**: Develop a script in MicroPython that enables the ESP32-C3 to scan for nearby Wi-Fi networks. This can be used to identify open networks or networks using weak encryption.

2. **Deauthentication Attack Demonstrator**: Create a program that can send deauthentication packets to Wi-Fi clients, effectively disconnecting them from their network. This project is purely for educational purposes and should be tested only in controlled environments with permission.

3. **Bluetooth Sniffer**: Utilize the ESP32-C3’s Bluetooth capabilities to detect and analyze Bluetooth devices in the vicinity. This can be used for identifying potentially vulnerable Bluetooth-enabled devices.

4. **RFID Cloner**: With additional hardware like an RFID reader/writer module, you can create a device that can clone RFID tags. This can be used to demonstrate the vulnerabilities in certain RFID-based security systems.

5. **Packet Sniffer**: Develop a tool that can capture and analyze packets on a network. This requires a deeper understanding of network protocols and can be a great learning experience.

6. **Keylogger**: Build a hardware-based keylogger using the ESP32-C3, which could be used to demonstrate the risk of unattended USB devices in computers.

7. **Simple Web Server for Phishing**: Create a simple captive portal or a mock login page to demonstrate how phishing attacks can be conducted through unsecured Wi-Fi networks.

8. **IoT Security Testing Device**: Program the ESP32-C3 to interact with IoT devices, attempting to exploit common vulnerabilities like default credentials or unencrypted communications.

9. **Network Jammer**: Develop a script that jams certain Wi-Fi channels. This should be used responsibly and legally, as it can disrupt legitimate network traffic.

10. **Cryptographic Algorithm Tester**: Implement basic cryptographic algorithms and use the ESP32-C3 to test their strength by attempting to break encryption under controlled conditions.

11. **Automated Pen Testing Tool**: Combine several of the above functionalities into a single automated tool that performs a series of penetration tests on a network.

12. **Mobile Command Center**: Integrate the ESP32-C3 with a mobile app or a remote server, allowing you to control and receive data from your penetration testing tools remotely.

#### Resources

- https://github.com/NicheSecTech/esp32-micropython-wifi-sniff-inject


### Download latest firmware

- https://micropython.org/download/ESP32_GENERIC_C3/
  - Example: `ESP32_GENERIC_C3-20231227-v1.22.0.bin`

### Install esptool python package

- `pipenv install esptool`

- Connect the esp32c3 chip to your computer.
- Run esptool.py commands:
  - `pipenv run esptool.py --chip esp32c3 --port /dev/ttyACM0 erase_flash`
  - `pipenv run esptool.py --chip esp32c3 --port /dev/ttyACM0 --baud 921600 --before default_reset --after hard_reset --no-stub  write_flash --flash_mode dio --flash_freq 80m 0x0 ESP32_GENERIC_C3-20231005-v1.21.0.bin`

### Install rshell python package

- `pipenv install rshell`

- Connect to the esp32c3 chip using rshell:
  - `pipenv run rshell --baud 921600 -p /dev/ttyACM0`