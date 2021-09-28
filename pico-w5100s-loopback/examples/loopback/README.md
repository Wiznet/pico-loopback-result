# How to Test Loopback Example


## Step 1: Prepare software

The following serial terminal program is required for loopback test, download and install from below links.

- [**Tera Term**][link-tera_term]
- [**Hercules**][link-hercules]



## Step 2: Prepare hardware

1. Combine RP2040-HAT-C with Raspberry Pi Pico.

2. Connect ethernet cable to RP2040-HAT-C ethernet port.

3. Connect Raspberry Pi Pico to desktop or laptop using 5 pin micro USB cable.



## Step 3: Setup Loopback Example

To test the loopback example, minor settings shall be done in code.

1. Set SPI port and pin.

Set the SPI interface you use.

```cpp
/* SPI */
#define SPI_PORT spi0

#define PIN_SCK 18
#define PIN_MOSI 19
#define PIN_MISO 16
#define PIN_CS 17
#define PIN_RST 20
```

2. Set network configuration such as IP.

Set IP and other network settings to suit your network environment.

```cpp
/* Network */
static wiz_NetInfo g_net_info =
	{
		.mac = {0x00, 0x08, 0xDC, 0x12, 0x34, 0x56}, // MAC address
		.ip = {192, 168, 1, 15},                     // IP address
		.sn = {255, 255, 255, 0},                    // Subnet Mask
		.gw = {192, 168, 1, 1},                      // Gateway
		.dns = {8, 8, 8, 8},                         // DNS server
		.dhcp = NETINFO_STATIC                       // DHCP
};
```



## Step 4: Build

1. After completing the loopback example configuration, click 'build' in the status bar at the bottom of Visual Studio Code or press the 'F7' button on the keyboard to build.

2. When the build is completed, 'w5x00_loopback.uf2' is generated in 'pico-examples/build/examples/loopback/' directory.



## Step 5: Upload and Run

1. While pressing the BOOTSEL button of Raspberry Pi Pico power on the board, the USB mass storage 'RPI-RP2' is automatically mounted.

![][link-raspberry_pi_pico_usb_mass_storage]

2. Drag and drop 'w5x00_loopback.uf2' onto the USB mass storage device 'RPI-RP2'.

3. If the loopback example works normally, you can see the result like the picture below.

![][link-loopback_test_result]



<!--
Link
-->

[link-tera_term]: https://osdn.net/projects/ttssh2/releases/
[link-hercules]: https://www.hw-group.com/software/hercules-setup-utility
[link-raspberry_pi_pico_usb_mass_storage]: https://github.com/Wiznet-OpenHardware/RP2040-HAT-C/blob/main/static/images/raspberry_pi_pico_usb_mass_storage.png
[link-loopback_test_result]: https://github.com/Wiznet-OpenHardware/RP2040-HAT-C/blob/main/static/images/loopback_test_result.png
