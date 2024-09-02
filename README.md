# ADSBTop

ADSBTop is a Python script designed to provide a comprehensive stats monitoring package for the console. It monitors `readsb` JSON files located in `/var/run/readsb` and updates the display whenever these files are updated. Additionally, it tracks basic configuration and records in an INI file (`/etc/adsbtop.json`), which is automatically created upon script initialization if it does not already exist.

![An image showing the User Interface](https://raw.githubusercontent.com/SusanTN/ADSBTop/main/adsbtop-screenshot.png)

## Installation Instructions for ADSBTop

Follow these steps to install and set up ADSBTop:

## Prerequisites

Ensure you have the following prerequisites installed and configured on your system:

- Python 3
- pip (Python package installer)
- ADSBExchange
- ReadSB 

## Download ADSBTop Script

Download the `adsbtop` script to your local machine from the GitHub repository `SusanTN/ADSBTop`.

Place the `adsbtop` script in your `/usr/local/sbin` directory on your Raspberry Pi. You can do this using the following command:

```
sudo mv path/to/adsbtop /usr/local/sbin/
```

## Make the Script Executable

Change the permissions of the adsbtop script to make it executable:

```
sudo chmod a+x /usr/local/sbin/adsbtop
```

## Install Required Python Modules

Ensure all required Python modules are installed by running the following pip command:

```
pip install sys json time os re tabulate watchdog textwrap threading datetime
```

##[Optional] Create and Configure the INI File

ADSBTop automatically creates a configuration file (/etc/adsbtop.json) upon its first run if it does not already exist. You can manually create and configure this file if needed:

If you wish to manually configure the file, use a text editor to add the following default configuration:

```
{
    "json_files": [
        "/var/run/readsb/aircraft.json",
        "/var/run/readsb/receiver.json",
        "/var/run/readsb/stats.json",
        "/var/run/readsb/status.json"
    ],
    "monitor_path": "/var/run/readsb/",
    "log_file": "adsb_stats.log",
    "box_width": 65,
    "expire_time": 3600,
    "adsbtop_version": "1.00",
    "record_max_range": 0,
    "record_max_range_timestamp": 0,
    "record_min_range": 0,
    "record_min_range_timestamp": 0,
    "record_max_aircraft": 0,
    "record_max_aircraft_timestamp": 0,
    "record_min_aircraft": 0,
    "record_min_aircraft_timestamp": 0,
    "record_max_uptime": 0,
    "record_max_uptime_timestamp": 0,
    "record_max_messages": 0,
    "record_max_messages_timestamp": 0,
    "record_max_messages_per_sec": 0,
    "record_max_messages_per_sec_timestamp": 0,
    "record_max_positions": 0,
    "record_max_positions_timestamp": 0
}
```

## Run ADSBTop

To start ADSBTop, simply run the script from the terminal:

```
adsbtop
```

Alternatively, you can use the full path to the script:

```
/usr/local/sbin/adsbtop
```

# Additional Note

The script retrieves the gain and AGC options from the /boot/adsbx-env file. Ensure this file is correctly configured with your desired settings.

# Troubleshooting

If you encounter any issues, verify the following:

 - Python 3 and pip are installed correctly.
 - All required Python modules are installed.
 - The script has executable permissions.
 - The configuration file (/etc/adsbtop.json) exists and is properly configured.

With these steps, ADSBTop should be installed and running, providing real-time stats monitoring for your ADS-B setup.
