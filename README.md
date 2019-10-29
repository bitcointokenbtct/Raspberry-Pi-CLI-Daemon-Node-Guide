Bitcoin Token Raspberry Pi Setup Guide
==========================

## Introduction

The following guide will provide the steps needed to run a Bitcoin Token node on your Raspberry Pi computer.

## Download and Install

**Step 1:** Open the Terminal Window

To open the terminal on most Raspberry Pi devices, click on the 4th icon to the left on the top bar.

**The remaining steps will all be within the terminal window.**

**Step 2:** Download the tarball
```
wget https://github.com/bitcointokenbtct/Bitcoin-Token-Core/releases/download/v1.0.1/btct-arm-linux-gnueabihf.tar.gz
```

**Step 3:** Untar the downloaded repository 
```
tar xzf btct-arm-linux-gnueabihf.tar.gz
```

**Step 4:** Copy the files to the local bin. **Requires sudo**
```
sudo cp -R btct/bin/* /usr/local/bin/
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
