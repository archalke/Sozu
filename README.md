# Sozu: Self-Powered Radio Tags for Building-Scale Activity Sensing

## About
Sozu a low-cost self-powered activity sensing system, which can detect a wide range of events wirelessly, through walls and floors, at a whole-building scale. Instead of running on batteries, Sozu tags leverage energy from activities that they sense, and convert this energy into RF broadcasts, acting like miniature radio stations. More information about this project can be found below:

[[Project video]](https://yangzhang.dev/research/Sozu/Sozu.pdf) [[Paper]](https://yangzhang.dev/research/Sozu/Sozu.pdf) [[Citation format]](https://doi.org/10.1145/3332165.3347952)

## Sozu Toolkit
To facilitate others' hands-on experience with Sozu, we created a toolkit which consists of a solar powered Sozu tag, an RTL-SDR, a set of antennas, demo code, and a quick start guide:


### Step 0: Make sure you have everything
You will find the following parts in the box:
*  A Sozu tag powered by a small [solar panel](https://www.digikey.com/product-detail/en/panasonic-bsg/AM-8801CAR/869-1016-ND/2165201)
*  One alligator clip
*  [RTL-SDR + antenna](https://www.amazon.com/dp/B011HVUEME/ref=cm_sw_em_r_mt_dp_U_lSCGCbVDHKKQQ)

### Step 1: Connect the SDR with antenna (two long ones), and connect it to the laptop:

<img src="./toolkit/images/assembleantenna.gif" alt="" width="499"/>

### Step 2: Install software

Sozu receiver is based on SDR. In this tutorial, we will use RTL-SDR. The easiest way to get data out of RTL-SDR is to use [pystlsdr](https://nocarryr.github.io/pyrtlsdr/) -- A Python wrapper for librtlsdr (a driver for Realtek RTL2832U based SDR’s). Python3 is required (3.7.4 was tested).

Steps to below to install librtlsdr and run Sozu demo code:

1. Install pyrtlsdr via [pip](https://pip.pypa.io/en/stable/):  

```bash
pip install pyrtlsdr
```

2. Install librtlsdr via [brew](https://brew.sh):  

```bash
brew install librtlsdr
```


3. Download Project Sozu source code from the [Github Page](https://github.com/FIGLAB/Sozu) or

```bash
git clone git@github.com:figlab/Sozu.git
```

4. Now plug in the SDR with the antenna connected (through USB) and get the RF signal from your environment by running the python code (./toolkit/software/Python/demo_waterfall.py):

```bash
python demo_waterfall.py
```
<img src="./toolkit/images/waterfall.gif" alt="" width="499"/>

If you can see the above output on your python window, you are ready to receive RF signals from Sozu tags!

### Step 3: Deploy Sozu tag in the environment
1. Deploy harvesters in the environment (if you are looking for examples, we have a [webpage](https://FIGLAB.com/) which shows how we harvest energy from a wide range of objects)

2. Make sure harvester provides higher than 1.5 Volts from the activity that you are interested in sensing using the multimeter.

3. Connect the energy harvester to the Sozu tag.

### Step 4: Locate the Sozu signal on the frequency spectrogram

1. Run the Python server code(./toolkit/software/Python/demo_waterfall_server.py):

<img src="./toolkit/images/pythonserver.gif" alt="" width="499"/>

2. Tune the center frequency of your SDR around the Sozu tag frequency (labeled on the back of the tag), until you see its signal on the waterfall chart:

<img src="./toolkit/images/search.gif" alt="" width="499"/>

After you have located the signal, you are ready to make applications out of it!

### Step 5 (optional):  Visualize and process Sozu signals with other programs

The Python code (./toolkit/software/Python/demo_waterfall_server.py) functions like a TCP server, ready to stream data out to any programs you want to use in your project. Here we demonstrate getting Sozu signals with Processing.

1. Download and install Processing from [https://processing.org](https://processing.org)

2. Run the Processing client code (./toolkit/software/Processing/client/client.pde). Now you should see the Sozu signal shown in the Processing app:

<img src="./toolkit/images/processing.gif" alt="" width="499"/>

### Request Sozu Toolkit
Please fill out the google form below for your toolkit request: https://forms.gle/UTFnRSarYxjS2oz19

For bulk orders and commercial collaborations, please email us at info@figlab.com
## Other Resources
### See what others created with Sozu
Auxiliary video of example projects: https://youtu.be/Q_soA7qurLE

### Sozu tags
PCB design files: https://github.com/FIGLAB/Sozu/tree/master/pcb

<img src="./images/tag_picture.jpg" alt="" width="499"/>
