# Create an custom Windows 10 multi-session image

1. Go to **Virtual Machine**
2. click on **Ad**

<img src="https://github.com/v8techit/Windows-Virtual-Desktop/blob/master/Media/Add_VM.PNG"/>

3. Click on **Browse all public and private images**

<img src="https://github.com/v8techit/Windows-Virtual-Desktop/blob/master/Media/Browse_Images.png"/>

4. Select **Windows 10 Enterprise multi-session + Office 365 ProPlus**

<img src="https://github.com/v8techit/Windows-Virtual-Desktop/blob/master/Media/Select_Image.PNG"/>

# Install OneDrive Per-Machine

By default, the OneDrive sync client installs per user on Windows, meaning OneDrive.exe needs to be installed for each user account on the PC under the %localappdata% folder. With the new per-machine installation option, you can install OneDrive under the “Program Files (x86)” directory, meaning all profiles on the computer will use the same OneDrive.exe binary.

You can download the new per-machine version of OneDrive below:
