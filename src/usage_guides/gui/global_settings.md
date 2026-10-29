# Global Settings

The Global Settings section is for the configuration of the underlying aspects of the system. It is split into two sections: one for the GUI and the other for the server which includes the default server settings.

## GUI settings

![GUI Settings](./images/gui_settings.png)
`The global settings for the GUI include:`

- A toggle for the theme of the user interface, it allows the user to switch between light and dark mode. (Dark mode is recommended.)
- A toggle for the viewing of the camera feed applicable to the whole application. This helps to declutter the UI.

## Server Settings

![Global Settings](./images/server_settings.png)

`The global settings for the server defaults include:`

- Web-Socket poll interval is the period between polling done on the 
- Update Delay is the delay between running the main loop, for faster edge analysis it can be lowered, please note that this will not increase the performance on the edge just the delay between each cycle of analysis. This can be helpful for saving bandwidth over the network at a larger scale, or over long periods of time where image analysis is only needed once every couple of seconds.
- Camera Error Decrement 
- Camera Error Increment 
- Camera Error Threshold
