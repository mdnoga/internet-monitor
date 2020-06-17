# Internet Monitor
Track internet connectivity

## What it does

At every run it writes to a text file timestamps for power and internet, whether the last run was scheduled or at boot and the last calculated periodicity.

If the script was run after a boot up, it will assume there was a power outage (the system is meant to run 24/7, for example a Raspberry Pi Zero) and send a notification, approximating the power outage duration through the last known timestamp and calculated periodicity of the runs.

Internet downtime is detected if the 2 timestamps written to the file differ and the downtime is approximated again through the calculated periodicity. It is possible that an internet downtime is missed if the script is run too rarely.

## How to run it

Install the module in a virtual environment with pip:

```
pip3 install Outage-Detector
```

Clone this git repo and running setup.py

```
git clone https://github.com/mdnoga/internet-monitor.git
python3 setup.py install
```

Then run the internet_monitor command line interface for the initialization process:

```
internet_monitor --init
```

## Todo:

- Add scheduling
  - Maybe create cron job(s)?
  - jobs details saved in datastore
- Add ways to be notified if outage is detected
  - email
  - IFTTT
  - SMS
