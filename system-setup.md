# System Setup
The root of all Bubbletill files should be located at `C:\bubbletill`.

# POS Devices
Bubbletill POS devices are designed to run on Windows 10, with this guide being written for version 20H2.
## Inside the root folder
- POS jar called `pos.jar`
- BO jar called `bo.jar`
- Folder for all of Local Server's files: `C:\bubbletill\localserver`.
- Folder for all of Shell's files: `C:\bubbletill\shell`.

## Accounts
There should be two user accounts:
- `Bubbletill` - user account that is set to login on start-up (see below) with the password `bubbletill`.
- `Parkgate` - administrator account

## Device Setup
### Registry edits
The following registry entries should set to enable auto-login of the Bubbletill user account:
Inside `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon`:
- DefaultUserName: `Bubbletill`
- DefaultPassword: `bubbletill`
- AutoAdminLogon: `1`

### Security Policy edits
To show Other User on the login screen:
Inside `Local Policies -> Security Options`:
- Don't display last signed-in: `Enabled`
- Don't display username at sign-in: `Enabled`


These are under `Interactive logon`

### Group Policy edits
To replace Explorer with BT Shell:
Inside `User Configuration -> System -> Custom User Interface`:
- Set to enabled and in the dialogue box type: `C:\bubbletill\shell\BT-SHELL.exe`

*Please note the security and group policy entries are not yet complete.*

## Breaking from the Shell
To break out of the Bubbletill Shell, press the following keybinds: `CTRL + SHIFT + ALT + X`. You will be prompted to enter a password, the default password being `bubbletill`.
<br>
Changing the password will require Visual Studio and knowledge of C#. From BT-SHELL's source code, edit the `passwordHash` value within `Shell.cs`. To get the hash for your password, edit the `Shell_Keydown` function and add `Clipboard.SetText(hashedInputStr);` after it is assigned. Ensure that `passwordOK` is set to `true` to ensure you can break from the shell. It is also recommended to change `passSalt` to your own custom string.

# Controller Server
## Inside the root folder
- BO jar called `bo.jar`
- Folder for all of Local Server's files: `C:\bubbletill\localserver`.
- Folder for all of Backend's files: `C:\bubbletill\backend`.

Further instructions coming soon.
