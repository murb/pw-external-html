ExternalHTML Loader
===================

Given an HTML URL, this module will pull it, and let you output it. This module
will also cache feeds that you retrieve with it.

Installing
----------

This module hasn't been submitted to the ProcessWire modules directory. To
install what you see here, simply add the zip provided by Github of the exact
contents of this module's master branch:

https://github.com/murb/pw-external-html/archive/master.zip

How to use it
-------------

To use this, you need to modify a template where you want to include some
external HTML.

Example #1: Using the predefined rendering
------------------------------------------

$html = $modules->get("ExternalHTML");
echo $html->render("https://murb.nl");


Example #2: Specifying options and using entry array titles
-----------------------------------------------------------

$html = $modules->get("ExternalHTML");
$html->cache = 0;

echo $html->render("https://murb.nl");

Options:
--------

Options should be set before calling load() or render().

// render only the body's contents (default = true)
$html->onlyBody = true;

// render only a fragment by selecting an parent element by id,
// it overrides the onlyBody parameter (default = '')
$html->fragmentId = "main";

// set the feed to cache for an hour (default = 1800 seconds)
// if you want to disable the cache, set it to 0.
$html->cache = 3600;

// fall back to using the cache's content on LoadError (default = true)
$html->useCacheOnLoadError = true;

// tell it to strip out any HTML tags (default = false)
$html->stripTags = false;

// tell it to encode any entities in the feed (default = false);
$html->encodeEntities = false;

Note that cleaning and fragmenting of the data is done before caching,
hence when building, make sure you disable cache.

Handling Errors
---------------

The $html->error property always contains a detailed
description of what error occurred:

if($html->error) { echo "<p>{$html->error}</p>"; }

I recommend only checking for or reporting errors when you are
developing and testing. On production sites you should skip
error checking/testing, as blank output is a clear indication
of an error. This module will not throw runtime exceptions so
if an error occurs, it's not going to halt the site.

Using Hanna Code?
-----------------

Use this snippet to create an external_html tag with all the options.

!HannaCode:external_html:eyJuYW1lIjoiZXh0ZXJuYWxfaHRtbCIsInR5cGUiOiIyIiwiY29kZSI6IlwvKmhjX2F0dHJcbmV4dGVybmFsX2h0bWxfdXJsPVwiaHR0cHM6XC9cL211cmIubmxcIlxuZXh0ZXJuYWxfaHRtbF9mcmFnbWVudF9pZD1cIm1haW4teWllbGRcIlxuZXh0ZXJuYWxfaHRtbF9vbmx5X2JvZHk9XCJ0cnVlXCJcbmV4dGVybmFsX2h0bWxfY2FjaGU9XCIxODAwXCJcbmV4dGVybmFsX2h0bWxfdXNlX2NhY2hlX29uX2xvYWRfZXJyb3I9XCJcIlxuZXh0ZXJuYWxfaHRtbF9zdHJpcF90YWdzPVwiZmFsc2VcIlxuZXh0ZXJuYWxfaHRtbF9lbmNvZGVfZW50aXRpZXM9XCJmYWxzZVwiXG5oY19hdHRyKlwvXG48P3BocFxuICAgICRodG1sID0gJG1vZHVsZXMtPmdldChcIkV4dGVybmFsSFRNTFwiKTtcbiAgICAkaHRtbC0+Y2FjaGUgPSAkZXh0ZXJuYWxfaHRtbF9jYWNoZTtcbiAgICAkaHRtbC0+ZnJhZ21lbnRJZCA9ICRleHRlcm5hbF9odG1sX2ZyYWdtZW50X2lkO1xuICAgICRodG1sLT5vbmx5Qm9keSA9ICRleHRlcm5hbF9odG1sX29ubHlfYm9keSA9PSBcInRydWVcIjtcbiAgICAkaHRtbC0+dXNlQ2FjaGVPbkxvYWRFcnJvciA9ICRleHRlcm5hbF9odG1sX3VzZV9jYWNoZV9vbl9sb2FkX2Vycm9yID09IFwidHJ1ZVwiO1xuICAgICRodG1sLT5zdHJpcFRhZ3MgPSAkZXh0ZXJuYWxfaHRtbF9zdHJpcF90YWdzID09IFwidHJ1ZVwiO1xuICAgICRodG1sLT5lbmNvZGVFbnRpdGllcyA9ICRleHRlcm5hbF9odG1sX2VuY29kZV9lbnRpdGllcyA9PSBcInRydWVcIjtcbiAgICBlY2hvICRodG1sLT5yZW5kZXIoJGV4dGVybmFsX2h0bWxfdXJsKTsgICAgICAgICAgXG4/PiJ9/!HannaCode




Based on the RSS/Atom plugin by Ryan Cramer / Teppo Koivula.

ProcessWire 3.x
Copyright 2019 by murb
Copyright 2013 by Teppo Koivula
Copyright 2011 by Ryan Cramer
Licensed under GNU/GPL v2, see LICENSE.TXT

http://www.processwire.com
http://www.ryancramer.com
https://www.murb.nl
