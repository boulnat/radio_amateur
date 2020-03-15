Radio amateur:

plugin the nesdr smart

# verify that the nesdr is visiable
$ lsusb | grep Semi
Bus 001 Device 004: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T

$ lsmod | grep dvb
dvb_usb_rtl28xxu       40960  1
dvb_usb_v2             45056  1 dvb_usb_rtl28xxu
dvb_core              131072  2 dvb_usb_v2,rtl2832
rc_core                53248  3 dvb_usb_v2,dvb_usb_rtl28xxu
mc                     53248  6 videodev,dvb_usb_v2,videobuf2_v4l2,uvcvideo,dvb$

# disable the default module to load
$ sudo nano /etc/modprobe.d/blacklist-dvb.conf
blacklist dvb_usb_rtl28xxu
# tell the module to load the driver we want
$ sudo apt-get install rtl-sdr

# hookup an antenna on the device
# test the divce
<br>$ rtl_test</br>
Found 1 device(s):
  0:  Realtek, RTL2838UHIDIR, SN: 00000001

Using device 0: Generic RTL2832U OEM
Detached kernel driver
Found Rafael Micro R820T tuner
Supported gain values (29): 0.0 0.9 1.4 2.7 3.7 7.7 8.7 12.5 14.4 15.7 16.6 19.$
[R82XX] PLL not locked!
Sampling at 2048000 S/s.

Info: This tool will continuously read from the device, and report if
samples get lost. If you observe no further output, everything is fine.

Reading samples in async mode...

# try to listen to commerctial radio
rtl_fm -M wbfm -f 98.8M | play -r 32k -t raw -e s -b 16 -c 1 -V1 -

# setup QSSTV
Audio Interface – PulseAudio
Input and Output Audio Device – default -- Playback/recording through the Pulse$
Sound Input – From sound card
Sound Output – To sound card
Click OK. Next, run the Calibrate function and go make a cup of tea/coffee: Opt$

-- add image

# decode an image test
$ wget https://raw.githubusercontent.com/davidhoness/sstv_decoder/master/sstv_t$
Use VIS – on
Auto Slant – on
Autosave – on
Signals – Normal
Mode – Auto

click on play button then play the sound you downloaded

-- add image

# install a pretty interface GQRX
$ sudo apt-get install gnuradio gqrx-sdr

-- add picture

install software
$ sudo apt-get install rtl-sdr sox pulseaudio qsstv ntpdate -y

