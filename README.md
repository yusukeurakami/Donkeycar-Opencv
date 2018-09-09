# Donkeycar-Opencv
Following is how I install opencv in my Raspi and Macbook


## Install Raspi

Don't forget upgrade and update!

```bash
sudo apt upgrade
sudo apt update
```

```bash
sudo apt install python-opencv
pip install opencv-python
```

Try following if doesn't work.

```bash
pip install opencv-contrib-python
pip3 install opencv-python
```

you might come up with error message like following.
```bash
ImportError: libhdf5_serial.so.100: cannot open shared object file: No such file or directory
```

Then try corresponding dependancies from following list (Or blindly try all!) and install them.
```bash
sudo apt install libhdf5-100
sudo apt install libharfbuzz0b
sudo apt install libwebp6
sudo apt install libjasper1
sudo apt install libilmbase12
sudo apt install libopenexr22
sudo apt install libgstreamer1.0-0
sudo apt install libavcodec-extra57
sudo apt install libavformat57
sudo apt install libswscale4
sudo apt install libgtk-3
sudo apt install libgtk-3-0
sudo apt install libqtgui4
sudo apt install libqt4-test
```

## Install it on MacbookPro
More suffering than Raspi even using Brew.

Just to make sure that the everything is updated.
```
brew upgrade
brew update
brew install python python3
brew link python
brew link python3
```

Check the Python version is 2.6 or 2.7, 3.5 or 3.6.
```
python -V
python3 -V
```

Adding this line to end of .bash_profile will make python command point to python2.
```
export PATH="/usr/local/opt/python/libexec/bin:$PATH"
```

Time to install the software we wanted.
```
brew install opencv
```

Add OpenCV’s site-packages path to global site-packages.
When brew is done compiling and installing OpenCV3, we will update path of site-packages directory which contains cv2.so file to Homebrew Python’s site-packages directory. Depending upon the Python version you have (2.6/2.7 or 3.5/3.6) these paths would be different.
```
############ For Python 2 ############
# This is a single line command.
echo /usr/local/opt/opencv/lib/python2.7/site-packages >> /usr/local/lib/python2.7/site-packages/opencv3.pth
 
############ For Python 3 ############
# This is a single line command
echo /usr/local/opt/opencv3/lib/python3.6/site-packages >> /usr/local/lib/python3.6/site-packages/opencv3.pth
```

I guess it won't work in most of the case...

Try 
```
brew info opencv --with-python3
```
and look for the insufficient dependencies.

Also try,
```
brew doctor
```

You might get following
```
Warning: You have unlinked kegs in your Cellar
Leaving kegs unlinked can lead to build-trouble and cause brews that depend on
those kegs to fail to run properly once built. Run `brew link` on these:
  python@2
  cmake
  python
```



