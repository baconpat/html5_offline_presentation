!SLIDE subsection
# Web Storage #

!SLIDE bullets incremental
# What #
* Store key/value pairs within the browser
* Domain specific
* Great for JSON data
* 5 megabytes

!SLIDE smbullets
# Support #
* IE 8.0+
* Firefox 3.5+
* Safari 4.0+
* Chrome 4.0+
* Opera 10.5+
* iPhone 2.0+
* Android 2.0+

!SLIDE bullets incremental
# Session Storage
* Single browser tab
* Lost when tab closes
* <code>sessionStorage</code>

!SLIDE bullets incremental
# Local Storage
* Domain specific
* Long term storage
* <code>localStorage</code>

!SLIDE javascript
# Write a value
    @@@ javascript
    localStorage['color'] = "green";
    
    localStorage.user = JSON.stringify(obj);

!SLIDE javascript
# Read Values
    @@@ javascript
    var color = localStorage['color'];
    
    var user = JSON.parse(localStorage.user);

!SLIDE javascript
# Other
    @@@ javascript
    localStorage.clear()

    localStorage.removeItem(key)
    
    localStorage.length
    
    localStorage.key(i)
    
!SLIDE bullets incremental
# My Uses
* Cache application data (JSON)

.notes No need to hit the server once the data was stored in the browser

* Save user changes while offline
    
!SLIDE subscection
# Issues

!SLIDE bullets incremental
# Multi-user computer
* Clear data on logout/login

!SLIDE bullets incremental
# "Schema" changes
* Migrations

!SLIDE bullets incremental
# Private information
* Client side encryption

!SLIDE bullets incremental
# Synchronization
* Stayed *offline* until the user initiated a save operation
* Most recent data wins



