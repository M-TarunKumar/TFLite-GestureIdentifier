# TFLite-GestureIdentifier
CNN Model that processes images streamed from Raspberrypi camera and identifies the gesture used in the image.

Default settings are suitable for Raspberry Pi3 and was successfully tested.

Although the TensorFlow model and nearly all the code in here can work with
other hardware, the code in `classify_picamera.py` uses the [`picamera`](
https://picamera.readthedocs.io/en/latest/) API to capture images from the Pi
Camera. So you can modify those parts of the code if you want to use a different
camera input.

## Set up your hardware

Before you begin, you need to [set up your Raspberry Pi](
https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up) with
Raspberry Pi OS (preferably updated to Buster).

You also need to [connect and configure the Pi Camera](
https://www.raspberrypi.org/documentation/configuration/camera.md).

And to see the results from the camera, you need a monitor connected
to the Raspberry Pi. It's okay if you're using SSH to access the Pi shell
(you don't need to use a keyboard connected to the Pi)—you only need a monitor
attached to the Pi to see the camera stream.


## Install the TensorFlow Lite runtime

In this project, all you need from the TensorFlow Lite API is the `Interpreter`
class. So instead of installing the large `tensorflow` package, we're using the
much smaller `tflite_runtime` package.

To install this on your Raspberry Pi, follow the instructions in the
[Python quickstart](https://www.tensorflow.org/lite/guide/python#install_tensorflow_lite_for_python).
Return here after you perform the `apt-get install` command.


## Download the example files

First, clone this Git repo onto your Raspberry Pi like this:

```
git clone https://github.com/M-TarunKumar/TFLite-GestureIdentifier.git
```

Then use Tensorflow script to install a couple of Python packages, and
download the model and labels file:

```
cd examples/lite/examples/image_classification/raspberry_pi

# The script takes an argument specifying where you want to save the model files
bash download.sh /tmp
```


## Run the example

```
python3 classify_picamera.py \
  --model gesture_detector.tflite \
  --labels labels.txt
```

You should see the camera feed appear on the monitor attached to your Raspberry
Pi. Try out any of the listed hand gestures in front of the camera and
you'll see the predictions printed. It also prints the amount of time it took
to perform each inference in milliseconds.

For more information about executing inferences with TensorFlow Lite, read
[TensorFlow Lite inference](https://www.tensorflow.org/lite/guide/inference).

# Develop
Please send pull requests for improvements and bug fixes in [this](https://github.com/M-TarunKumar/TFLite-GestureIdentifier) github repository.

# License
Python files in this repository are released under the [GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/) 

# Reference
[TensorFlow Lite Python classification example with Pi Camera](https://github.com/tensorflow/examples/tree/master/lite/examples/image_classification/raspberry_pi)

