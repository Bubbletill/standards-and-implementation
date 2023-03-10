# System Setup
The root of all Bubbletill files should be located at `C:\bubbletill`.

# POS Devices
Bubbletill POS devices are designed to run on Windows 10, with this guide being written for version 20H2.
## Inside the root folder
- POS jar called `pos.jar`
- BO jar called `bo.jar`
- Folder for all of Shell's files: `C:\bubbletill\shell`.
- Data file called `data.json`.

### Data File
The data file contains all the information about the current device, including register and store number, controller URI, etc. Here is an example file:
```json
{
  "storeno": 1,
  "regno": 1,
  "token": "bubbletilld3m0one",
  "backend": "http://yourcontroller.com:5000",
  
  "dbUsername": "bubbletill",
  "dbPassword": "verysecure"
}
```

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

If the right password is entered, the shell will close and Windows Explorer will appear. Once any maintenance has been done, logging out and logging back in will restore the Shell.


Changing the password will require Visual Studio and knowledge of C#. From BT-SHELL's source code, edit the `passwordHash` value within `Shell.cs`. To get the hash for your password, edit the `Shell_Keydown` function and add `Clipboard.SetText(hashedInputStr);` after `hashedInputStr` is assigned. Ensure that `passwordOK` is set to `true` to ensure you can break from the shell. It is also recommended to change `passSalt` to your own custom string. Once you enter the password within the shell, the hash will be copied to your clipboard. You can then update `passwordHash` to that hash and undo any other changes.

# The Controller
## Inside the root folder
- BO jar called `bo.jar`
- Folder for all of Backend's files: `C:\bubbletill\backend`.
- Data file called `data.json`. The data file structure is the same as above, however the register number should be set to -1.

Further instructions coming soon.
