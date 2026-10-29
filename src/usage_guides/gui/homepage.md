# Homepage

![Homepage]()
The Homepage is the main dashboard for the laser vision system. On it, you will find all information needed for standard operation.

## Alerts

At the top of the page is the alerts section.

It displays important information such as deviation warnings or device disconnection events. This section can be collapsed if necessary.

## Main Section

The main body of the page is information about all devices known by the system.

The first tab shows all currently connected devices while the second tab shows devices that have been disconnected or have encountered an issue that prevents them from operating.

### Connections

This tab shows all currently connected devices.

The cameras are grouped by the edge computing device that they are connected to.

Each connected camera that has been calibrated will show the current deviation value and be coloured to alert if the deviation has drifted outside a set threshold using a stoplight colour system.

There is a button for each edge computing device to quickly access configuration options for it.

You can select a camera to view more details about it and calibrate the deviation measurement.

### Disconnections

This tab shows devices that are no longer connected to the system.

Each device has a button to forget the camera completely. Faulty cameras have a button to manually force a reconnection attempt.
