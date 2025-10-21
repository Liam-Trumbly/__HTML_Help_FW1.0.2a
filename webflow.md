Help me to build a website that will host locally on my computer.  Each Page will have the same general format:

Column 1:                      Column 2
------------------------------|--------------------------------------------------------|
Bkg (002752)                  |  Bkg (00458f)                                          |
Small PNG logo                |  "SP Framework Help File"                              |
------------------------------|--------------------------------------------------------|
Bkg (ffffff)                  | Bkg (ffffff)                                           |
"Table of Contents"           | Main Header for support Topic                          |
List Main Pages and topics    | Support Info                                           |
"Quick Search"                |                                                        |
search bar                    |                                                        |
---------------------------------------------------------------------------------------|

Please use the following structure:

# Home (Main Page)
## About The Framework
 - Goals and Architecture
 - Who this framework is for
 - support tiers
   - Programmer / Sandbox Developer
   - AV Maintenance
   - AV Tech / Enduser
 - Recommended Training Path

# Defining a Sandbox (Page 2)
## Determine Equipment Footprint
   - Define possible cameras
 displays
 codecs
 matrix switchers
 DSPs
 etc.
## Determine Sandbox Walls
   - Min - Max number of displays
   - Min - Max AV Sources
   - Supported Classifications
 
# GUI Best Practices (Page 3)
 ## Naming Convention
   - Buttons
 Labels
 Sliders
 Levels
   - Graphics
   - Pages and Popups
   - Defualt Load Page
## Avoid Name / ID conflicts
    - Reserved IDs / Names

# Framework Essentials (Page 4)
| Function                   | Description                                                                            |
|:---------------------------|:---------------------------------------------------------------------------------------|
| /// HOST MANAGEMENT ///////                                                                                         |
| register_host              | Creates a global Tie-in for Processors and SPDs.                                       |
| gHost                      | Retrieve a host from the host database.                                                |
| getDefaultHost             | Retrieve the default UIHost from the configuration.                                    |
| registerAllHosts           | Helper to register_host - Pulls host definitions from the sandbox config.              |
| anyUI_Host                 | Retrieves the UI host from the tlpDB based on the ui_name provided.                    |
| /// GLOBAL FUNCTIONS //////                                                                                         |
| register_gFunc             | Creates a global Tie-in for functions to recall from any Function File.                |
| gFunc                      | Call a global function with the given ID and pass in arguments and Keyword args.       |
| gFuncLoader                | Allows you to 'load' a global function from one file (including args & kwargs)
 but    |
|                            | execute it in another.                                                                 |
| /// GLOBAL TIMERS /////////                                                                                         |
| register_gTimer            | Creates a global Tie-in for Extron Timer Class.                                        |
| gTimer                     | Call a global Timer.                                                                   |
| /// UI HOSTS / TLPs ///////                                                                                         |
| TLP_Loader                 | Used to load a series of TLP Panels by alias.                                          |
| getDefaultUIHost           | Retrieve the default UIHost (TLP) from the framework configuration.                    |
| getUIHostAlias             | Used to return the deviceAlias of a button's TLP (UIHost).                             |
| /// TRACE / PRINT TOOLS ///                                                                                         |
| dvTrace                    | dvTrace is used in place of print
 and allows you to print to the standard print       |
|                            | window
 but also to a TCP Port for better debugging
 formatting
 and filtering.        |
| /// CONSOLE MANAGEMENT / TEXT / BOOT TOOLS ///                                                                      |
| consoleWindow              | Scrollable Horiz/Vert text scroll for reviewing files and text.                        |
| rolling_text_scroll        | Scrolling text for boot-up that auto-dumps old lines once threshold is met.            |
| BootTimerPunchIn           | Punches in the boot timer for a given page and records the current time.               |
| BootTimerPunchOut          | Punches out the boot timer for a given page and completes the loading tracking process.|
| IpcpInfoBlock              | Generates a formatted information block for a given Host / processor.                  |
| aboutFramework             | Create an 'about' message using a template and substitute values into it.              |
| /// BUILDING UI ELEMENTS ///                                                                                        |
| MultiButtonMake            | Creates a button with the specified name on each desired UIHost panel in the tlpDB.    |
| MultiLevelMake             | Creates a Level with the specified name on each desired UIHost panel in the tlpDB.     |
| MultiSliderMake            | Creates a Slider with the specified name on each desired UIHost panel in the tlpDB.    |
| MultiLabelMake             | Creates a Label with the specified name on each desired UIHost panel in the tlpDB.     |
| MultiMESetMake             | Creates a unique MESet for each panel defined in UIHosts. If UIHosts is not specified
 |
|                            | an MESet is created for every panel in the tlpDB.                                      |
| /// ACCESS UI ELEMENTS ///                                                                                          |
| anyBtn                     | Returns a list of all button objects in uiDB with a given name.                        |
| anySlider                  |                                                                                        |
| anyMESet                   | Returns a list of all MESet objects in meDB with a given name.                         |
|                            | Allows monitoring of MESets by name across different panels.                           |
| /// ME SET TOOLS /////////                                                                                          |
| LocalMESetCurrent          | Sets the currently pressed MESet to "Set Current" based on the provided button object. |
| MultiMESetCurrent          | Iterates through the meDB and sets all MESets with the specified name to the current   |
|                            | button defined.                                                                        |
| MultiMESetStates           | Sets the state for buttons within specified MESets across various panels.              |
| meDB_GetCurrent            | Retrieves the current button object from the specified MESet in the meDB.              |
| /// UI ELEMENT SET TOOLS ///                                                                                        |
| MultiSliderSetRange        | Sets distributed ranges to sliders with the same name according to the distro list.    |
|                            | The distro list is made of panel string aliases.                                       |
| MultiSetText               | Sets text for UI objects across specified panels.                                      |
| MultiSetPulse              | Pulses the state of all buttons with a given name across specified UI hosts.           |
| MultiSetState              |                                                                                        |
| MultiSetBlinking           | Sets blinking state to all buttons with the given name or pattern across specified     |
|                            | UI hosts.                                                                              |
| MultiSetVisible            |                                                                                        |
| MultiSetEnable             | Sets the enable state for all buttons with a given name across specified UI hosts.     |
|                            | Typically used for Buttons outside an MESet.                                           |
| MultiDisable               | Sets the state and enable/disable property for all buttons with the same name or       |
|                            | pattern across specified UI hosts. Includes support for buttons within MESets.         |
| /// PAGE / POPUP NAVIGATION //                                                                                      |
| MultiShowPage              | Shows a specified page on all panels within the given UI hosts. If UIHosts is not      |
|                            | provided
 it shows the page on all panels that have that page in the tlpDB.            |
| MultiShowPopup             | Shows a specified popup on all panels within the given UI hosts. If UIHosts is not     |
|                            | provided
 it shows the popup on all panels that support the target popup in the tlpDB. |
| MultiHidePopup             | Hides a specified popup on all panels within the given UI hosts. If UIHosts is not     |
|                            | provided
 it hides the popup on all panels that support the target popup in the tlpDB. |
| MultiHideAllPopups         | Hides all popups on all specified panels. If UIHosts is None
 it hides all popups on   |
|                            | every panel that supports popups in the tlpDB.                                         |
| MultiHidePopupGroup        | Hides the specified popup group on all panels in the provided UIHosts. If UIHosts is   |
|                            | None
 it hides the popup group on every panel that has it in the tlpDB.                |
| MultiPlaySound             | Plays a specified sound on all panels in the provided UIHosts. If UIHosts is None
 it  |
|                            | plays the sound on every panel in the tlpDB.                                           |


 # Boot Agent (Page 5)
## Required Files
- Defining New Files
- Checking Files
## Boot Screen
 - Timing
 - Force Continue

# Matrix Configuration (Page 6)
 - CSV Import
   - matrix
   - ioKey
   - ioLocation
   - ioSecLvl
   - ioType
   - ioPort
   - ioTieType
   - uiLabel
   - uiIcon
   - ioCaveat
   - uiSrcPos
   - uiShareSrcPos
   - uiDestPos
   - uiGrpDestPos
   - uiVtcSrcPos
   - uiRoomSrcPos
   - uiWebHostPos
   - uiCamSrcPos
   - bidirectional
   - note


# Device Configuration (Page 7)
 - CSV Import
   - DeviceAlias
   - name
   - type
   - module
   - Host
   - Port
   - Mfg
   - Model
   - "serial Baud"
   - "serial Unidirectional"
   - "ir File"
   - "ip Hostname"
   - "ip IPPort"
   - "ip username"
   - "ip password"
   - arg1
   - arg2
   - notes
 
# Sandbox Config (Page 8)
 - Json Import
    