!SLIDE subsection
# Application Cache #

!SLIDE bullets incremental
# What #
* Stores HTML, CSS, JavaScript, images, etc. 
* Browser looks here first for resources
* Contents specified in a cache manifest file
* Updated whenever the cache manifest changes

!SLIDE bullets incremental
# Cache Manifest
* Lists all URLs to cache
* Content-Type must be <code>text/cache-manifest</code>
* Files listed are **only** accessed from the cache

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
    /home.html
    /javascripts/application.js
    /stylesheets/application.css
    /images/logo.png
    /data.json
    
    FALLBACK:
    /offline

!SLIDE bullets incremental
# First page load
* Loads and displays like a normal web page
* Downloads cache manifest
* Downloads and stores all specified files

!SLIDE bullets incremental
# Second page load
* Displays cached page immediately
* Checks to see if cache manifest file has changed
* Downloads new cache manifest
* Downloads and stores all specified files
* Refresh or <code>swapCache()</code> required to use the new data

!SLIDE javascript smaller
# Events
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
* Allow users to enter data while offline
    
!SLIDE 
# Issues

!SLIDE bullets incremental
# Not available in IE8
* Used Google Gears

!SLIDE bulles incremented
# Caching many files can take a while

!SLIDE smbullets
# Support #
* Firefox
* Safari
* Chrome
* iPhone
* Android




