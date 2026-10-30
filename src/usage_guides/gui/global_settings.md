# Global Settings

The Global Settings section is for the configuration of the underlying aspects of the system. It is split into two sections: one for the GUI and the other for the server which includes the default server settings.

## GUI settings

![GUI Settings Image](./images/gui_settings.png)
`The global settings for the GUI include:`

- A toggle for the theme of the user interface, it allows the user to switch between light and dark mode. (Dark mode is recommended.)
- A toggle for the viewing of the camera feed applicable to the whole application. This helps to declutter the UI.

## Server Settings

![Global Settings Image](./images/server_settings.png)

`The global settings for the server defaults include:`

- Web-Socket poll interval is related to the old websocket which was single threaded, the new multi-threaded, this has now been (`depreciated`). 
- Update Delay is the delay between running the main loop, for faster edge analysis it can be lowered, please note that this will not increase the performance on the edge just the delay between each cycle of analysis. This can be helpful for saving bandwidth over the network at a larger scale, or over long periods of time where image analysis is only needed once every couple of seconds.
- Camera Error Decrement is the value that is reduce from the internal behaviour counter that each camera has. This decrement occurs when the camera is behaving correctly.
- Camera Error Increment is the value that the internal behaviour counter increases by. This occurs when the camera is misbehaving.
- Camera Error Threshold is the limit when passed the system will mark the camera as broken and can be found in the disconnected tab in the homepage.
