=== Custom Content by Country (by Shield Security) ===
Contributors: paultgoodchild
Donate link: https://icwp.io/d9
Tags: custom content, location, geolocation
Requires at least: 3.2.0
Tested up to: 6.1
Requires PHP: 5.4
Stable tag: 3.2.0

== Description ==

Custom Content by Country from the team behind [Shield Security](https://icwp.io/kx "Shield Security")
offers you the option to show/hide content to users based on their location (where provided).

With a simple shortcode you can specify, using a list of country codes whether to
display or hide a block of text/content.

To learn how to use the plugin, see the [comprehensive FAQ](https://wordpress.org/extend/plugins/custom-content-by-country/faq/)

== Frequently Asked Questions ==

= What is the Shortcode to use? =

[CBC] [/CBC]

= What options are available in the shortcode? =

Currently there are 4 options/parameters: *country*, *ip*, *show*, *message*, *html*

country: a comma-separated list of country codes, e.g. country="us, es, uk"

show: is a simple yes ('y') or no ('n'). e.g. to hide content, show="n"

message: is an optional piece of text you can display when the content that you're showing/hiding from a group of people isn't shown.
Instead of displaying absolutely nothing, you can display a message. e.g message="Sorry, this content isn't available in your region."

html: This is the html tag within which the content will be wrapped, e.g. DIV, SPAN, ...  If this isn't specified, SPAN is used.  If you
don't want any HTML wrapping specify html="none"

= How do I use the shortcode? =

To show the text "abcdefg" ONLY to visitors from the US and France, I would use the following shortcode:

[CBC country="us, fr" show="y"]abcdefg[/CBC]

To then hide the text "mnopqrst" ONLY from visitors in Spain, use the following shortcode:

[CBC country="es" show="n"]mnopqrst[/CBC]

= Can I filter for IP addresses instead of countries? =

Yes, instead of using the `country` field, use `ip` instead. e.g.

[CBC ip="1.2.3.4" show="y"]mnopqrst[/CBC]

Note 1: If you have "country" field supplied, it'll never consider IP addresses. So make sure to remove the country field.

Note 2: The plugin makes  attempt to verify the correct visitor IP address. This is up to you and your web hosting provider to ensure it's valid.

= What happens if I leave out the option "show"? =

Then 'show' will default to 'y' and proceed accordingly.

= What happens if I leave out the option "country" =

Nothing, it will just print the content to everyone.

= What is CloudFlare and how does it relate to this plugin? =

If your site isn't using CloudFlare, you really should consider it.

Separately, if you are using it on your site, you have a slight optimization where I use a parameter that
CloudFlare sends that gives the users location saving me an SQL query.

= Where does the plugin pull its IP location data? =

The plugin makes use of the location data provided by IP 2 Nation that is freely available. You don't need
to pay for this.

= Will this plugin slow my site down by making external queries to 3rd parties? =

No. The plugin, upon activation, will ask you to install the necessary data into your own WordPress database.
If you don't install this data, you cannot use the plugin.

= Where can I find a list of the country codes? =

I believe the country codes are ISO 3166 country codes. You can find a list here: https://en.wikipedia.org/wiki/ISO_3166-1

= Are the any other shortcodes available in this plugin? =

Yes, I have provided 2 extra shortcodes. They are:

[CBC_COUNTRY /]  takes no parameters and is used as-is. This will print the visitor's full country name.

[CBC_IP /]  takes no parameters and is used as-is. This will print the visitor's full IP address (or their proxy server).

= Can I nest shortcodes - i.e. put a shortcode within the custom content? =

Yes. I'm still baffled why other plugin authors find this a challenge.

= I want to use CSS to style the output, is there way I can do that? =

Yes. Again, I'm still baffled why other plugin authors find this a challenge.

Any output from the plugin is wrapped in html SPANs with corresponding classes:

CBC has class 'cbc_content'
CBC_COUNTRY has class 'cbc_country'
CBC_IP has class 'cbc_ip'

There is also the option within the each shortcode itself to specify ID and STYLE just like you would HTML elements.

e.g. [CBC country="gb" show="y" id="my_cbc_id" style="color:yellow;"]Custom Content for GB[/CBC]

= How does the W3 Total Cache option work exactly? =

W3 Total Cache allows you to (programmatically) set caching options on a per-page basis. This means we can say for any WordPress page/post that is loaded, to allow
caching, or not.

As of version 2.11, I have added the global plugin option to turn off page caching for ONLY those pages that use this shortcode.  If you use this shortcode throughout
your website using your theme, and you enable this option, you will effectively turn off page caching for your entire site.

Remember this only affects page caching. It doesn't affect any browser caching, database or object caching etc.  If you don't know what this means, read the FAQ on
the W3 Total Cache plugin for more info.

= Do you make any other plugins? =

We created the [Shield Security](https://icwp.io/kx "Shield Security") plugin for people who want better WP Security.

We also created the [Manage Multiple WordPress Site Better Tool: iControlWP](https://icwp.io/60) for people with multiple WordPress sites to manage.

Yes, we created the only [Twitter Bootstrap WordPress](https://icwp.io/61 "Twitter Bootstrap WordPress Plugin")
plugin with over 122,000 downloads so far.

= What "country code" can I use to test locally if I'm accessing a server on our network? =

If your local network address is defined as "Private" according to the database, the country code to use in this case is: 01

This isn't fully tested and shouldn't be used as-is in production, but it seems to hold up.  Feedback welcome.

== Changelog ==

= 3.2.1 =
*released 4th January 2023*

* .1 UPDATED: Use Handlebars JS to render templates.
* .1 UPDATED: Gut and clean plugin.
* .1 UPDATED: GeoIP DB.
* .1 REMOVED: Completely removed the Amazon Affiliate links functionality.

= 3.1.0 =
*released 22nd June 2022*

* .3 SECURITY:  Fix for reported CSRF security vulnerability [more info](https://patchstack.com/database/vulnerability/custom-content-by-country/wordpress-custom-content-by-country-plugin-3-1-2-broken-access-control-vulnerability).
* .2 FIXED:  Prevent an error if our plugin can't detect a valid IP address.
* .2 FIXED:  Remove unnecessary admin notice.
* NEW:       Make use of 3rd party plugins for Geolocation data if you're using them. i.e. [Geolocation IP Detection](https://wordpress.org/plugins/geoip-detect/)
* CHANGED:   Use CloudFlare Country Code header if 3rd party data isn't available before other lookups.
* FIXED:     Prevent conflict with other plugins by only including the libraries if they're absolutely required.

= 3.0.0 =
*released 17th June 2022*

* NEW:  Completely gutted the plugin and start using GeoIP DB locally.
* NEW:  Final release to support PHP 5.x.

= 2.19 =
*released 17th June 2022*

* NEW:  Added support for using IP addresses instead of just country codes.

= 2.18.200520 =
*released 21st June 2020*

* UPDATED:  Move to minimum PHP 5.4 and cleaned some code.
* UPDATED:  Updated Geo location database to latest available version: 2020-05-20.

= 2.18.180726 =
*released 30th August 2018*

* UPDATED:  Updated Geo location database to latest available version: 2018-07-26.

= 2.18.170521 =
*released 16th June 2017*

* UPDATED:  Database import method more efficient
* UPDATED:  Updated Geo location database to latest available version: 2017-05-21.

= 2.17.161112 =
*released 17th November 2016*

* UPDATED:  Updated Geo location database to latest available version: 2016-11-12.

= 2.17.160707 =
*released 27th, July 2016*

* UPDATED:  Updated Geo location database to latest available version: 2016-07-07.

= 2.17.160525 =
*released 2nd, June 2016*

* UPDATED:  Updated Geo location database to latest available version: 2016-05-25.

= 2.17.150725-1 =
*released 10th, August 2015*

* UPDATED:  Support WordPress v4.4

= 2.17.150725-0 =
*released 10th, August 2015*

* FIXED:  PHP Warning notice in settings page.

= 2.17.150725 =
*released 26th, July 2015*

* UPDATED:  Updated Geo location database to latest available version: 2015-07-25.

= 2.17.150613-0 =
*released 15th, June 2015*

* UPDATED:  Updated Geo location database to latest available version: 2015-06-13.

= 2.17.150218-1 =
*released 16th, April 2015*

* UPDATED:  Updated Geo location database to latest available version: 2015-02-18.
* FIX:      ISO Country Codes for Mexico (MX), and Maldives (MV)

= 2.16.140816-1 =

* CHANGED:  WordPress 4.0 compatibility.
* CHANGED:  Changed plugin version to be shorter (YYMMDD)

= 2.15.20140816-4 =

* FIXED:    Manually updated the database data to correctly store ISO Codes for Countries. [ref](https://en.wikipedia.org/wiki/ISO_3166-1)

= 2.15.20140816-2 =

* FIXED:    Manual tweak to the ip2nations database to correctly reflect the ISO country code for Sweden [ref](https://wordpress.org/support/topic/what-are-the-country-codes)
* CHANGED:  Plugin version now highlights the date of the ip2nations database (YYYYMMDD)
* ADDED:    Automatic plugin updates for updated ip2nations db, minor releases, bug fixes [as per my own article](https://icwp.io/62)
* CHANGED:  Plugin refactor to bring it closer in-line with developments made on [Simple Firewall](https://wordpress.org/plugins/wp-simple-firewall/) and [Twitter Bootstrap](https://wordpress.org/plugins/wordpress-bootstrap-css/) plugins

= 2.14 =

* UPDATED:  IP2Nations database to latest version from 16th August 2014
* UPDATED:  Major code refactor for better maintenance going forward.
* FIXED:    Developer mode (using cookies to optimize performance) setting was ignored in some cases.
* CHANGED:  Developer mode is enabled by default.

= 2.13 =

* UPDATED: IP2Nations database to version 22nd June 2014
* FIX: IP Address detection in cases where it's populating with Port number.
* FIX: shortcode usage of ' html="none" '
* ADDED: option to manually force the display of the database install option.

= 2.12 =

* UPDATED: IP2Nations database to version 22nd March 2014

= 2.11 =

* ADDED: Feature to allow you to by-pass W3TC Total Cache PAGE CACHING for pages that use this shortcode. See FAQs.

= 2.10 =

* ADDED: A global plugin option to turn HTML printing off. You can turn it off globally, and then override for individual shortcodes using the HTML (v2.9) parameter as and when you need it.

= 2.9 =

* UPDATED: IP2Nations database to version 15th January 2013
* ADDED: Ability to not print shortcode with surrounding HTML.  Simply use parameter html="none"

= 2.8 =

* FIXED: Call time by reference errors.
* ADDED: data-detected-country field to the HTML spans that are generated so you can see the exact country code being detected each time.

= 2.7 =

* Added a Developer Mode - turn this on to STOP the performance optimization whereby country code data is stored in a cookie to reduce repeat MySQL queries.
* Ensured that there would be no PHP warning errors associated with WORPIT_DS definition

= 2.6 =

* CHANGED: Now to prevent warnings with settings cookies, the cookie setting has been moved higher up in processing before http headers have been set.
(in response to: https://wordpress.org/support/topic/plugin-custom-content-by-country-from-worpit-warning-cannot-modify-header-information)

= 2.5 =

* ADDED: A dismiss button for those who have manually installed the IP 2 Nations database.

= 2.4 =

* ADDED: Now uses a 24hour cookies to store country code and country name to reduce repeated SQL queries. That is, every visitor that triggers this shortcode will incur only 1 MySQL query on the site.

= 2.3 =

* UPDATED: The IP2Nations IP-to-Country database to latest release (August 22, 2012)

= 2.2 =

* FIXED: Bug with undefined function error (thanks Merle!)

= 2.1 =

* FIXED: Bug with incomplete internationalisation functions. Will complete for a later release.

= 2.0 =

* UPDATED: the IP 2 Nation database to the version released 3rd June 2012. You will be prompted to run the database upgrade after the plugin is installed.
* ADDED: Plugin options/settings page - you must enable any of the 2 main features to use anything from the plugin. This is in order to maximum plugin
performance so only the absolutely necessary code is used.
* ADDED: Automatic Amazon Affiliate links using shortcode: [CBC_AMAZON] . You can also specify Amazon associate tags for each Amazon website
and the plugin will automatically use it with the appropriate site and generate an affiliate link for your product ASIN depending on where the visitor is from.
* ADDED: Plugin now conforms to iControlWP standard plugin structure. Faster, stable and automatically generates options pages.

= 1.1 =

* ADDED: Shortcode [CBC_CODE /] - which will print your country code.
* ADDED: Special case for local testing, where if your IP Address is detected as 127.0.0.1, country and country code will be detected as 'localhost'.
* Tidied up the code A LOT.
* Improved the Admin Notices and DB update process, and is now using the correct WordPress action hooks.
* Added special case for local testing, where if your IP Address is detected as 127.0.0.1, country and country code will be 'localhost'.
* Began coding for adding some nice features later.

= 1.0 =

* First Release