# Device Settings
![Device Settings]()
The Device Settings section is for the configuration of the devices used in this project, such as the cameras and microComputers that are currently being used.
## microComputers
![micro Computer Settings]()
The microComputers refers to the Raspberry pi that is used to run the edge, however the edge can also be run on any computer. However as a group we recommend the use of a microComputer such as the Raspberry pi, due its small form factor it fits well in the tightly packed laser lab.

`The connected microComputers can be configured to:`
- Be selected to filter the select options for all the connected cameras in the system in the camera configuration below.
- Be renamed, as it allows the user to give a meaningful identifier to the device 
- Have the vision processing technique to be selected. Note: this will select the processing technique for all cameras connected to the microComputer.

## Cameras
The cameras that can be configured are the ones that are connected to he system, and have their state as active.

`The connected Cameras can be configured to:`
- Rename the selected camera to a more meaningful name such as what it is observing
- Change the selected camera controls to for tweaking to help improve the vision processing. `Some camera controls to consider are:`
  - PUT IMPORTANT CAMERA CONTROLS HERE
![Camera Controls]()
- Set the deviation thresholds for the selected camera, if a camera is miss behaving and needs a custom deviation ranges to keep them in check.
![Camera Deviation]()
- The range (min - max) of the Deviation threshold input slider can be configured to suit the needs of the cameras threshold setup, which allows for the fine tuning of the deviation thresholds.
![Deviation Slider Range]()
