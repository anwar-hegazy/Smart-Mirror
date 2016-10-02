# Smart-Mirror
Raspberry powered mirror which can display the news, weather, and time.

## Installation and Updating
### Code
If you have [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed, clone the repository.

```
git clone git@github.com:netnutmike/Smart-Mirror.git
```

**Alternatively, you can download a zip file containing the project (green button on the repository page)**

Navigate to the folder for the repository

```
cd Smart-Mirror
```

### Install your dependencies 
make sure you have [pip](https://pip.pypa.io/en/stable/installing/) installed before doing this

```
sudo pip install -r requirements.txt
```

```
sudo apt-get install python-imaging-tk
```

### Add your api token

```
vi smartmirror.py or nano smartmirror.py if you are more comfortable with nano.
```

replace `weather_api_token` with the token you got from forecast.io

## Running
To run the application run the following command in this folder

```
python smartmirror.py
```

## Setting up auto-start
To get your raspberry pi to automatically start the graphical user interface and automatically start the smart mirror application, there are 2 steps.

### Starting the Graphical User Interface
If your raspberry pi does not automatically start in the graphical user interface, you can change that by running:
```
sudo raspi-config
```

  Choose Boot Options and select boot into Desktop GUI with automatic login.
  
### Automatically starting the Smart Mirror program

   Copy the file called smart-mirror.desktop to ~/.config/autostart.  The autostart directory may not exist and might need to be created.
   
   ```
   mkdir ~/.config/autostart
   cp ~/Smart-Mirror/smart-mirror.desktop ~/.config/autostart
   ```
   
   You should edit the smart-mirror.desktop file and make any changes neccessary for your system.
   
   ```
   vi ~/.config/autostart/smart-mirror.desktop
   ```
   
   If you followed the instructions exactly, no editing of this file should be needed.
   

## Rotating the display
If your monitor is turned on it's side to present a longer mirror you will need to tell the raspberry pi to display the monitor in portrait mode.  

```
sudo vi /boot/config.txt
```

Go to the bottom of the file and add this line:
```
display_rotate=1
```
You will need to reboot for this change to take effect.

## Turning off the Screen Saver
More than likely you are going to want to disable the screen saver that is on my default on the Raspberry Pi.  It is not obvious how to do that in the GUI.  Below are 3 lines you can copy and paste into /etc/xdg/lxsession/LXDE/autostar

Open the file for editing:
```
sudo vi /etc/xdg/lxsession/LXDE/autostart
```

Copy and paste to the bottom after the last line.
```
@xset s noblank 
@xset s off 
@xset -dpms
```
