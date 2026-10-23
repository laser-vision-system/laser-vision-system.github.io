# GUI Quickstart
## NavBar
![NaveBar](./images/navbar.png)
The NavBar short for navigation bar, it is used to switch between different sections of the application. The NavBar uses its icons to indicate the users location on the application having the icon changes to show a red light, this is a reference to a motif that is shared by some camera when they are indicating that they are recording. It fits well with the overall theme of the project as we are using machine vision in a system where the cameras should always be running.

From the NavBar the user is able to get to the 3 main locations:
- The Homepage
- Device Settings
- Global Settings 

## Homepage
The Homepage is the main dashboard for the project, it shows the current deviation values for the cameras which have been calibrated in a clear and easy to understand layout.

`The key features of the homepage include:`
- `Deviation Alerts`
  - The deviation alters single to the user via a colour coded message that cameras detected deviation is out of the waring or alter thresholds.
- `Connected and Disconnected Devices`
- `Device Management`
- `Deviation Detection`
- `Camera Information`
- `Camera Feed `

## Device Settings
The Device Settings section is for the configuration of the devices used in this project, such as the cameras and microComputers that are currently being used.
### microComputers
The microComputers refers to the Raspberry pi that is used to run the edge, however the edge can also be run on any computer. However as a group we recommend the use of a microComputer such as the Raspberry pi, due its small form factor it fits well in the tightly packed laser lab.

`The connected microComputers can be configured to:`
- Be selected to filter the select options for all the connected cameras in the system in the camera configuration below.
- Be renamed, as it allows the user to give a meaningful identifier to the device 
- Have the vision processing technique to be selected. Note: this will select the processing technique for all cameras connected to the microComputer.

### Cameras
The cameras that can be configured are the ones that are connected to he system, and have their state as active.

`The connected Cameras can be configured to:`
- Rename the selected camera to a more meaningful name such as what it is observing
- Change the selected camera controls to for tweaking to help improve the vision processing. `Some camera controls to consider are:`
  - PUT IMPORTANT CAMERA CONTROLS HERE
- Set the deviation thresholds for the selected camera, if a camera is miss behaving and needs a custom deviation ranges to keep them in check.
- The range (min - max) of the Deviation threshold input slider can be configured to suit the needs of the cameras threshold setup, which allows for the fine tuning of the deviation thresholds.
## Global Settings
The Global Settings section is for the configuration of the underlying aspects of the system. It is split into two sections one for the GUI and the other for the server which includes the default server settings.

### Global GUI settings
`The global settings for the GUI include:`
- A toggle for the theme of the user interface, it allows the user to switch between light and dark mode. ( We recommend the dark mode)
- A toggle for the viewing of the camera feed throughout the whole application. which helps to declutter.

### Global Server Settings
`The global settings for the server defaults include:`
- Web-Socket poll interval 
- Update Delay
- Camera Error Decrement
- Camera Error Increment 
- Camera Error Threshold
