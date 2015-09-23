# Compass

Compass is a GPS tracking server that stores data in [flat files](https://github.com/aaronpk/QuartzDB).

## Setup

In the `compass` directory, copy `.env.example` to `.env` and fill in the details. Install the dependencies with composer.


## API

After you create a tracking database, you can visit the database's settings page to get a read or write token. These tokens are used with the API to update or retrieve data.

### Writing

To write to a database, make a POST request in JSON format with the following keys:

`POST /api/input`

* locations - a list of GeoJSON objects
* token - the write token for the database

The GeoJSON objects must have at least one property, "timestamp", which is can be any value that can be interpreted as a date. The object can have any additional properties you wish.

The open source iOS [GPS Logger](https://github.com/esripdx/GPS-Logger-iOS) will send data in this format by default.

### Reading

To read a database, make a GET request with the following keys:

`GET /api/query`

* token - the read token for the database
* date - specify a date to return all data on that day
* tz - timezone string (e.g. America/Los_Angeles) which will be used to determine the absolute start/end times for the day



## Credits

Compass icon by Ryan Spiering from the Noun Project.


## License

Copyright 2015 by Aaron Parecki

Compass is licensed under the [Apache 2.0 license](http://opensource.org/licenses/Apache-2.0)

Compass is built using the Lumen framework, which is licensed under the [MIT license](http://opensource.org/licenses/MIT)
