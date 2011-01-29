!SLIDE subsection
# Application Cache #

!SLIDE bullets incremental
# What #
* Stores HTML, CSS, JavaScript, images, etc. 
* Browser looks here first for resources
* Contents specified in a cache manifest file
* Updated whenever the cache manifest changes

!SLIDE smbullets
# Support #
* Firefox
* Safari
* Chrome
* iPhone
* Android

!SLIDE bullets incremental
# Cache Manifest
* Lists all URLs to cache
* Content-Type must be <code>text/cache-manifest</code>
* Files listed are **only** accessed from the cache
* Can be generated programmatically

!SLIDE html
# Specify the manifest
    @@@ html
    <!DOCTYPE html>
    <html manifest='/cache.manifest'>


!SLIDE code

    CACHE MANIFEST
    # Updated: 2011-01-31 11:10:31 -0500

    NETWORK:
    *

    CACHE:
    http://ajax.googleapis.com/jquery.js
    /home
    /javascripts/application.js
    /stylesheets/application.css
    /images/logo.png
    /data.json
    
    FALLBACK:
    /offline.html

!SLIDE
# First page load

!SLIDE
# Just like a normal web page

!SLIDE
# In the background downloading files

!SLIDE
# Second page load

!SLIDE
# Displayed from cache *immediately*

!SLIDE
# Has the cache manifest changed?

!SLIDE
# Download new files

!SLIDE
# Refresh or <code>swapCache()</code>

!SLIDE javascript smaller
# Status and Events
    @@@ javascript
    var appCache = window.applicationCache;
    
    if (appCache.status === appCache.UPDATEREADY ||
        appCache.status === appCache.DOWNLOADING) {
          
      handleDownloading();
      
    }
    
    if (appCache.status === appCache.UPDATEREADY) {
      
      handleOfflineReady();
      
    } else {
      
      appCache.addEventListener('cached', handleOfflineReady);
      appCache.addEventListener('updateready', handleOfflineReady);
      appCache.addEventListener('downloading', handleDownloading);
      appCache.addEventListener('error', handleCacheError);
      
    }
    
!SLIDE bullets incremental
# My Uses
* Allow users to enter data from locations with no network
* Users not affected by intermittent WiFi connection
    
!SLIDE
# Issues

!SLIDE bullets incremental
# Simulating Offline
* Turn off WiFi on laptop
* Disable network in a Virtual Machine
* "Offline" mode in Firefox

!SLIDE bullets incremental
# Annoying Double Refresh
* Firefox - ignore request to store data
* ![Firefox](firefox_offline.png)

!SLIDE bullets incremental
# What's going on with the cache?
* Google Chrome - Developer Tools
* Displays status updates 
* Easily browse Local Storage and Application Cache

!SLIDE bullets incremental
# Manifest errors are bad
* Silent failure
* Had to restore an iPad after mobile Safari cached a bad manifest
* Firefox - easiest to blow away offline cache

!SLIDE bullets incremental
# Expires headers
* Used Rails' cache-busting timestamp in the manifest
* <code>/javascripts/application.js?1291049950</code>

!SLIDE bullets incremental
# Cache not updated until ALL files are downloaded
* Displayed a modal dialog while downloading new version

!SLIDE bullets incremental
# Not available in IE8
* Used Google Gears

!SLIDE bullets
# Example site
* <http://rubyconf2010.busyconf.com>







