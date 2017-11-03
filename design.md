# raspberry-os
A setup of Raspbian that boots to Chromium in Kiosk mode and runs the `display` application.

### Todo
- Think about how to do first-time WiFi setup.

# display
Displays pictures from Facebook, Google Drive etc.
Displays calendar entries.
Permanent QR code & link to configurator
And other things?
Twitter feed?

### On first boot
- WiFi setup?
- Display QR code and url to `display-configurator` application.

# display-socket
Listens for connections from displays.  
When a connection is received
- create a queue on MQ for receiving and relaying commands to the display.
- send current configuration to device
 
### Commands expected from display
- Boot - when a display boots, do security check (validate known IP and location) and send configuration back.

### Commands sent to display
- ConfigureDisplay - update display configuration.

# display-configurator
PWA web app used to configure displays from a mobile device or PC.
### Use cases
- Log in with Facebook or Google.
- Assign a FB/Google account to existing account.
- Configure your displays.
  - From where to display pictures.
  - Modify picture display duration.
  - What calendars to show entries for.
 
# display-controller
Accepts commands from display-configurator and sends MQ messages.  
Saves and loads state in database.

# repository
Database facade