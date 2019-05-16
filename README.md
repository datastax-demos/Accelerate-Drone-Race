# Drone Race Project for DataStax Accelerate

This is a python package which controls the DJI 'Tello' drone. The major portion of the source
code was ported from the driver of GOBOT project. See the original golang version and protocol in
detail, please refer their blog post at
https://gobot.io/blog/2018/04/20/hello-tello-hacking-drones-with-go

Much of the core of this project comes from: https://github.com/hanyazou/TelloPy

The app is simple - it controls the DJI Tello using any controller via the PyGame library (yup! It's basically a video game). There are two types of events that the drone collects:
1. In-flight data including speed, battery, wifi connectivity, etc.
2. Positional data relative to where the drone takes off (starting at 0,0,0). 

Both types of events are sent via REST API to the drone race UI (Sebulba, see below). The positional data is also written to a CSV file to make 3D plotting the flight path easy. 



![photo](files/da-mascot.png)



## How to install
General hardware/software requirements:
```
-DJI Tello Drone
-Controller: Any controller* should be plug and play. If you want to check to see if your controller is supported, run examples/controller_check.py
(For Accelerate, we'll be using PS4 controllers) 

-Python > 3.6
-Java 8.latest (Maven is required for Sebulba) 

-Works on Mac, Linux, or Windows**. 


*Xbox controllers will not work on recent versions of MacOS, even with 3rd party drivers. Xbox controlers work natively on Windows.
**Setting up video (PyAV) on Windows is extremely difficult. It's not recommended. 
```


For DataStax Accelerate, we are not using the video streaming functionality. It's in the code, commented out. Install just what's needed for Accelerate:

```
$ pip install -r requirements.txt
```

If you want the drone to write data to DSE, you'll want to download and setup Sebulba: https://github.com/phact/sebulba

If you'd like to mess around with video, you'll need to install the following:


```
$ brew install ffmpeg pkg-config
$ pip install tellopy
$ pip install av
$ pip install opencv-python
$ pip install image
```

## How to start the app
If you plan on writing to DSE, make sure Sebulba is up and running. When you scan a QR code, the number/badgeid will be written with each drone event. 

First, you'll want to run: `$ ./start-drone-app.sh`

This will start the Python application that controls the drone and sends telemetry data to the UI

Then, you'll want to turn on your Tello Drone and connect to its WiFi

![photo](files/tello-wifi.png)

Once you're connected, you're ready to take off! 


## Controls

See image below for controls 

![photo](files/controls.jpeg)
 

 
