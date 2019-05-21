# windows-10_hyper-v_ubuntu-19.04_enable-sounds
Enable sounds for ubuntu 19.04 vm when using hyper-v on Windows 10

# Step 1 - install dependencies
```bash
$> sudo su
$> apt install build-essential dpkg-dev
$> apt install pulseaudio
$> apt build-dep pulseaudio
$> apt-get install libpulse-dev
$> apt install git
```

Open `Software & Updates`, go to tab `ubuntu software` and check `source code`

![search](https://github.com/baal-cadar/windows-10_hyper-v_ubuntu-19.04_enable-sounds/blob/master/software_and_updates_0.png)
![check](https://github.com/baal-cadar/windows-10_hyper-v_ubuntu-19.04_enable-sounds/blob/master/software_and_updates.png)

# Step 2
```bash
$> cd /tmp
$> apt source pulseaudio
$> cd /tmp/pulseaudio-12.2/
$> ./configure
```

# Step 3
```bash
$> cd ~
$> git clone https://github.com/neutrinolabs/pulseaudio-module-xrdp.git
$> cd pulseaudio-module-xrdp/
$> PULSE_DIR=/tmp/pulseaudio-12.2/ ./bootstrap 
$> PULSE_DIR=/tmp/pulseaudio-12.2/ ./configure 
$> make
$> sudo make install
```

If you want to check installation:
```bash
$> ls $(pkg-config --variable=modlibexecdir libpulse)
```

# Step 4
Restart vm

# Step 5
Login, go to page with some music, for example: 
* https://youtu.be/s0aDp1CFZ7Q?t=744

Should work by now.

You can also check activity using pavumeter. 

```bash
$> apt install pavumeter
$> pavumeter
```
