BLE demo app (Peripheral) for Nordic nRF52811 SoC
===============================

## Brief Introduction
This is a demo BLE application for the NordicSemiconductor nRF52811.
Built upon the nRF52 SDK and based on the Nordic_Blink (ble_app_blinky).
It supports all dev/eval boards with an nRF52811 SoC on board.

## Development tools
1. The GNU Arm Embedded Toolchain and Make are required for building.
2. Meanwhile, the settings for Visual Studio Code is also provided for convenience.
3. Also you need a programmer/debugger/probe, e.g., JLink
4. A Java runtime with GUI support is required for the CMSIS Configuration Wizard (sdk_config).

### Environment variables
No matter you prefer an IDE or not.
Please set up the following environment variables before you start.
1. ARM_GCC={the root directory of the Arm Embedded Toolchain}
2. nRF_SDK={the root directory of the nRF52 SDK}

## Build
This is how you build the hex file
### Commandline
```sh
cd armgcc
make
# You may also use the make clean to removed the binaries
make clean 
```

### Vscode
Run the task called **build**.  
There's also a task called **clean** for cleanning up.

## Flashing the SoC
This is how you download your program to the SoC.
The soft device and the user program are separated.
You may flash either of them.

### Commandline
```sh
cd armgcc
# Usually you need run flash_softdevice in very rare cases.
make flash_softdevice

# Download the user program onto the target SoC
make flash
```
### Vscode
Run the task called **flash** to download your user program onto your target SoC.  
Run the task called **flash_softdevice** to re-program soft device of your target SoC.

## SDK Config
To modify the `config/sdk_config.h`, we suggest use the CMSIS Configuration Wizard.
Here's how to launch the wizard.

### Commandline
```sh
cd armgcc
make sdk_config
# After a while, the wizard GUI is poped up.

```
### Vscode
Run the task called **sdk_config** to start the wizard.  


## Debugging
The debugging is done with a hardware probe, also known as debugger or programmer.
A gdb runs in server mode sending commands and fetching the data via the probe.
You will need a gdb client, which supports the arm architecture to connect to the server and debug.

### Commandline
Omitted, as it's really inconvenient.  
For detail, please check the documents of your probe or GNU.

### Vscode
The debug setting for vscode is provoided in the `.vscode/launch.json`.  
Use "Run > Start Debugging" to debug your app with vscode.