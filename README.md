# M5PaperS3 TRMNL Firmware

Arduino firmware for using the M5PaperS3 e-ink device as a TRMNL display.

## Features
- Full M5Unified library support (M5EPD deprecated)
- PNG and BMP image support
- Deep sleep power management with RTC persistence
- Battery voltage monitoring
- Automatic WiFi retry logic
- Wake on button press or timer
- [ ] Use touchscreen to update content on screen

## Hardware Requirements
- M5PaperS3 e-ink display (960x540)
- WiFi network access

## Installation

### PlatformIO
1. Clone this repository
2. Add `src/secrets.h`
  1. Set `#define SSID "YourWiFi"`
  2. Set `#define WIFI_PASSWORD "YourWiFiPassword"`
  3. Set `#define SERVER_URL "http://YourTerminusInstance/api/display"`
3. `pio run` or `pio run --target upload -e PaperS3`

## Configuration
Edit these values in the code:
- `WIFI_SSID` - Your WiFi network name
- `WIFI_PASS` - Your WiFi password

## Usage
The device will:
1. Wake up (timer or button press)
2. Connect to WiFi
3. Fetch display from TRMNL API
4. Render image to e-ink screen
5. Enter deep sleep until next refresh

## Troubleshooting
- **WiFi won't connect**: Check credentials, device will auto-retry 3x
- **Image won't load**: Verify TRMNL API key and network connectivity
- **Battery drain**: Normal refresh rate is 15 minutes (900s)

## Credits
Built for the [TRMNL BYOD program](https://docs.trmnl.com/go/diy/byod)

## License
MIT
