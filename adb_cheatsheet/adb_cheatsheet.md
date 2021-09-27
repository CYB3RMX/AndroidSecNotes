# ADB CheatSheet for Pentesters

**Commands about Connections and Devices**
```bash
adb connect IP:PORT     # Connects devices with specified IP address and port.
                        # Example: adb connect 192.168.1.154:5555

adb disconnect IP:PORT      # Disconnect from given TCP/IP device.
                            # Example: adb disconnect 192.168.1.154:5555

adb reconnect   # Refreshes connection.

adb forward tcp:PORT_1 tcp:PORT_2   # This command will forward incoming requests on port PORT_1/tcp to port PORT_2/tcp.
                                    # Example: adb forward tcp:1337 tcp:4444

adb devices -l  # Gives information about connected devices.
                # Example output: 192.168.56.154:5555    device product:vbox86p model:Google_Pixel device:vbox86p transport_id:2
```

**Commands about Files**
```bash
adb push FILE FILE_PATH_IN_REMOTE_DEVICE    # Sends given file to remote device.
                                            # Example: adb push test.apk /sdcard

adb pull REMOTE_FILE PATH   # Gets remote file to local device.
                            # Example: adb pull /sdcard/test.apk /home/kali/Desktop/
```

**Commands about Application Installing/Uninstalling**
```bash
adb install APK_FILE  # This command will install given application to remote device.
                      # Example: adb install hackme.apk

adb uninstall PACKAGE_NAME  # This command will removes given application from remote device.
                            # Example: adb uninstall com.example.hackme
```

**Commands about Shell**
```bash
adb shell COMMAND_TO_EXECUTE    # Executes given command on remote device. (If no command given you will get interactive shell.)
                                # Example: adb shell "ls" --> Executes "ls" command on remote device.
                                # Example: adb shell --> You'll get shell.
```

**Getting Installed Applications/Packages**
```bash
adb shell 'pm list packages -f' | sed -e 's/.*=//' | sort
```

**Hacking Exported Activites and Services via ADB**
```bash
adb shell "am start -n com.example.hackme/com.example.hackme.LoginActivity" # This command spawns LoginActivity.

adb shell "am startservice -n com.example.hackme/com.example.hackme.BluetoothService" # This command starts bluetooth service.
```