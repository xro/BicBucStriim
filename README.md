BicBucStriim
============

BicBucStriim streams books, digital books. It fills a gap in the functionality of current NAS devices that provide access to music, videos and photos -- but not books. BicBucStriim fills this gap and provides web-based access to your e-book collection.

BicBucStriim was created when I bought a NAS device (Synology DS 512+) to store my media on it. NAS devices like the Synology DS typically include media servers that publish audio, video, photos, so that you can access your media from all kinds of devices (TV, smart phone, laptop ...) inside the house, which is very convenient. Unfortunately there is nothing like that for e-books. So BicBucStriim was created.

BicBucStriim is a simple PHP application that runs in the Apache/PHP environment provided by the NAS. It assumes that you manage your e-book collection with [Calibre](http://calibre-ebook.com/). The application reads the Calibre data and publishes it in HTML form. To access the e-book catalog you simply point your ebook reader to your NAS, select one of your e-books and download it. 

Features & Issues
-----------------

* shows the most recent titles on the index page
* provides listing/filtering/searching of book titles, authors, tags and series
* shows detail pages (including download & custom columns) for authors and books
* speaks Dutch, English, French, German
* is ready for mobile clients (tested with Kindle, iPhone, iPad)
* provides access restrictions for users (optional, think "parental control")
* provides OPDS book catalogs for reading apps like Stanza
* has an admin GUI for configuration
* supports e-mailing of books


* no support for Calibre's virtual libraries
* only simple custom columns supported


Install
-------

There are 3 options for installation:

1. [Download](http://projekte.textmulch.de/bicbucstriim/downloads/) an installation archive. These are stable releases with a reduced footprint, unnecesary files are removed.
2. Install directly from Github by cloning a [release tag](https://github.com/rvolz/BicBucStriim/releases). These are also stable releases, but contain all files in the repository.
3. Live dangerously and clone/fork the Github master. Please be aware that this branch contains most often a version under development, which could be slow or partially broken.

The easy way assumes that BicBucStriim lives right below the web root of your device and can be addressed like `http://<your ip>/bbs/`:

* Unarchive the downloaded archive below the web server root of your NAS (e.g. "/volume1/web" on a Synology device).
* Rename the newly created directory (e.g. BicBucStriim-1.1.0.zip) to "bbs".
* The "data" directory and its contents must be writeable for all. Depending on your method of unarchiving this might be already the case. However, in case you experience access error just use a terminal to correct this: `chmod -R ga+w data`. 
* BicBucStriim should now be working, start your web browser and navigate to `http://<address of your NAS>/bbs/`
* Login as the administrator with the default login *admin/admin* (don't forget to change the password afterwards).
* A freshly installed BicBucStriim app will show you the admin section, where you will have tell the app where your Calibre library is located. Everything else is optional. Just have a look.
* OPDS catalogs are availabe at http://.../bbs/opds/


Upgrading
---------

If you are already using BicBucStriim and don't want to lose your configuration and thumbnails:

* Backup your old BicBucStriim installation, eg. `mv bbs bbs.old`
* Install the new version
* Remove the data directory, eg. `rm -rf bbs/data`
* Copy our old data directory, eg. `cp -R bbs.old/data bbs`
* Use `chmod -R ga+w bbs/data` to correct the permissions after copying

After that BicBucStriim should work again.

Troubleshooting
---------------

If you encounter problems, use the installation test to check your environment. Invoke this test by navigating to `http://<NAS address>/bbs/installcheck.php`. This test checks for problems that users experienced in the past.


Requirements
------------
* Apache web server with PHP 5.3+, including support for mcrypt and sqlite3
* Optional: if PHP module *intl* (php5-intl) is installed, book languages will be displayed

License
-------

BicBucStriim itself is licensed under the MIT license, for the licenses of the libraries used see the file NOTICE.

(The MIT License)

Copyright (c) 2012-2013 Rainer Volz

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


