
# nwws-python-client

A simple product downloader for the NWWS-2 OI ([NOAA Weather Wire Service](http://www.nws.noaa.gov/nwws/) version 2 Open Interface) written in Python. The NOAA Weather Wire Service is a satellite data collection and dissemination system operated by the [National Weather Service](http://weather.gov), which was established in October 2000. Its purpose is to provide state and federal government, commercial users, media and private citizens with timely delivery of meteorological, hydrological, climatological and geophysical information. 

This script was developed and tested on [Ubuntu 16.04](http://ubuntu.com) using ***Python v2.7***. This client makes use of the [sleekxmpp](https://github.com/fritzy/SleekXMPP) Python library for connecting to the NWWS-2 OI XMPP-based server.

## How do I run it?

After cloning the latest [release](https://github.com/jbuitt/nwws-python-client), create a JSON config file using the following format:

```
{
  "username": "[username]",
  "password": "[password]",
  "resource": "[resource]",
  "archivedir": "/path/to/archive/dir",
  "pan_run": "/path/to/executable_or_script"
}
```

Where `[username]` and `[password]` are your NWWS-2 credentials obtained by signing up [on the NOAA Weather Wire Service website](http://www.nws.noaa.gov/nwws/#NWWS_OI_Request). You may use whatever you would like for `[resource]`. The `pan_run` variable is an optional Product Arrival Notification (PAN) script that you'd like to run on product arrival.

Now run the script:

```
$ python ./nwws2.py /path/to/config/file
```

Provided that you're able to connect to the NWWS and your credentials are accepted, you will start to see products appear in the supplied archive directory in the following format:

```
[archive_dir]/
   [cccc]/
      [cccc]_[ttaaii]-[awipsid].[ddHHMM]_[id].txt
```

The above variables have the following meaning:

* `cccc` - International four-letter location indicator of the station or centre originating or compiling the product
* `ttaaii` - tt - Report type, aa - Region of the report, ii - Report number. [more info](http://weather.unisys.com/noaaport/WMO_Header_Text.php)
* `awipsid` - [AWIPS](https://www.unidata.ucar.edu/software/awips2/) ID
* `ddHHMM` - Day, hour, and minute of product issuance
* `id` - Product NWWS ID

You can either run it via [screen](https://www.gnu.org/software/screen/)/[tmux](https://github.com/tmux/tmux/wiki) or use the included `nwws2` script to run it using [nohup](https://en.wikipedia.org/wiki/Nohup). The client will automatically reconnect to NWWS if the connection is dropped.

## Author

+	[jbuitt at gmail.com](mailto:jbuitt@gmail.com)

## License

See [LICENSE](https://github.com/jbuitt/nwws-python-client/blob/master/LICENSE) file.

