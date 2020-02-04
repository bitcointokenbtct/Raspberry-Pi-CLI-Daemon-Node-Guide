<img src="https://raw.githubusercontent.com/bitcointokenbtct/Official-Images/master/github-header-raspi.jpg">

Bitcoin Token Raspberry Pi CLI Daemon Setup Guide
==========================

## Introduction

The following guide will provide the steps needed to run a Bitcoin Token node on your Raspberry Pi computer.

## Hardware and Operating System

Recommended hardware:

https://www.amazon.com/dp/B01N13X8V1/ - Raspberry Pi 3 Model B<br>
https://amzn.to/2BNQHfm – Kingston Canvas React™ 32GB microSD card<br>
http://a.co/2c9FFaf – 8-Port Desktop USB Charger Charging Station<br>
http://a.co/8i5RHU3 – Short USB Cable, (the 10 pack is a good value)<br>
https://www.amazon.com/dp/B016A90URW/ - 1 foot ethernet (the 10 pack is a good value)

If you do not have an OS loaded on your SD card for your Raspberry Pi computer, then you need to download the image file for Rasbian and write it to your SD card.

Rasbian Download: https://www.raspberrypi.org/downloads/raspbian/

To write the downloaded image file to your SD card you will need this software: https://etcher.io (follow the steps in the software)


## Download and Install

**Step 1:** Open the Terminal Window

To open the terminal on most Raspberry Pi devices, click on the 4th icon to the left on the top bar.

**The remaining steps will all be within the terminal window.**

**Step 2:** Download the tarball
```
wget https://github.com/bitcointokenbtct/Bitcoin-Token-Core/releases/download/v1.1/btct-1.1-arm-linux-gnueabihf.tar.gz
```

**Step 3:** Untar the downloaded repository 
```
tar xzf btct-1.1-arm-linux-gnueabihf.tar.gz
```

**Step 4:** Copy the files to the local bin. **Requires sudo**
```
sudo cp -R btct-1.1/bin/* /usr/local/bin/
```

**Step 5:** Create the default config file and add the command to start as daemon.
```
mkdir ~/.btct && touch ~/.btct/btct.conf && echo "daemon=1" > ~/.btct/btct.conf
```

**Step 6:** Start the BTCT daemon.
```
btctd
```

The daemon will start and the blockchain will begin to download. Your wallet will be established also.

If you want to watch the progress or monitor the blocks, you can monitor the debug.log.

```
tail -f ~/.btct/debug.log
```

If you would like the node daemon to start with the computer, you can add the following command to your crontab.

**Open the Crontab**
```
crontab -e
```

**Add the following entry**
```
@reboot /usr/local/bin/btctd
```

## CLI Commands

Utilizing the functionality of the wallet when the node is running as a daemon is very easy. Below you will find
some popular commands that can help you fully utilize your wallet and all features you can find in a GUI version.

```
btct-cli help
```

```
btct-cli getinfo
```

```
btct-cli getbalance
```

```
btct-cli getnewaddress ""
```

```
btct-cli sendtoaddress BSomeBTCTAddress 10000
```
