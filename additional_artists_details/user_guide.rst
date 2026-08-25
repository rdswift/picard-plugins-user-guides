Additional Artists Details
===========================

Overview
---------

This plugin provides specialized album and track variables with artist details such as type, gender, begin and end dates, location (begin, end and current) and country code (begin, end and current) for use in tagging and naming scripts.

.. note::

   This plugin makes additional calls to the MusicBrainz website api for the information, which will slow down retrieving album information from MusicBrainz. This will be particularly noticable when there are many different album or track artists, such as on a \[Various Artists\] release. There is an option to disable track artist processing, which can significantly increase the processing speed if you are only interested in album artist details.


What it Does
----------------

This plugin reads the album and track metadata provided to Picard, extracts the list of associated artists, retrieves the detailed information from the MusicBrainz website, and exposes the information in a number of additional variables for use in Picard scripts.

The plugin maintains a cache of artist and area information retrieved from MusicBrainz to avoid making multiple API calls for the same information. This can significantly reduce the time required to load an album by eliminating unnecessary API calls for information already retrieved.

Area and (optionally) artist information is saved to a persistent cache file so that it is retained between Picard sessions. Area information usually provides the most additional API calls, and thus is the largest contributor to delays when loading an album. For this reason, area information is always saved to the persistent cache file.

When the plugin is initialized, it will populate its working cache from the persistent cache file if it is available. When an album is retrieved from MusicBrainz, once loading is complete, the persistent cache file is updated automatically with any new items in the working cache.

Option Settings
----------------

The plugin adds a settings page under the "Plugins" section under "Options..." from Picard's main menu. This allows you to control how the plugin operates with respect to processing track artists and detail included in the artist location variables' content.

.. image:: option_settings.png
   :alt: Additional Artists Details Option Settings
   :align: center

|

Track processing
+++++++++++++++++

This option determines whether or not details are retrieved for all track artists on the release. If you are only interested in details for the album artists then this should be disabled, thus significantly reducing the number of additional calls made to the MusicBrainz API and reducing the time required to load a release. Album artists are always processed.

Details to include
+++++++++++++++++++

These options determine whether or not County, Municipality and Subdivision information is included in the artist location variables created. Regardless of these settings, this information will be included if a County, Municipality or Subdivision is the area specified for an artist.

Persistent cache
+++++++++++++++++

The working cache is periodically stored to a persistent cache file, in JSON format, to allow the information to be used in subsequent Picard sessions. The path and file name of the persistent cache file is displayed, and there is a button to open the directory in your system file browser for easy access.

Area information is always stored in the persistent cache file, because area lookups produce the largest amount of API calls that impact album loading time.

Artist information storage in the persistent cache file is optional, but recommended. Where area information is almost always static and does not change, artist information occasionally changes things like location, begin or end dates, or disambiguation. If artist information is retained in the persistent cache file, the variables created will not contain this updated information. There are two ways to address this. One way is to disable including the artists in the cache file, and the other way is to remove one or more selected artists from the cache using the cache editor. Removing specific artists will trigger refreshing only those artists the next time they are encountered on an album.

.. image:: cache_editor.png
   :alt: Additional Artists Details Cache Editor
   :align: center

|

The cache editor displays a list of the artists currently contained in the cache. It allows you to remove one or more artists from the current cache by selecting them from the list and clicking the :guilabel:`Remove` button. There is a check box to quickly select or deselect all artists, and an option to highlight and quickly move between artists using a filter.

Because the area information causes numerous additional calls to the API resulting in significant delays, and because the information rarely changes, the area information items cannot be removed from the cache with the cache editor.

The persistent cache action buttons include:

- :guilabel:`Load` - Load the items from the persistent cache file into the current working cache.
- :guilabel:`Save` - Save the items from the current working cache to the persistent cache file.
- :guilabel:`Edit` - Open the cache editor dialog.
- :guilabel:`Import` - Import items from a user-specified cache file into the current working cache.
- :guilabel:`Export` - Export the items from the current working cache to a user-specified cache file. This can be used to generate a copy of the cache for backup purposes, for transferring to a different system, or for sharing with others.

.. caution::

   When the option to include artists when saving to the cache file is disabled, the artist information will **not** be written when using the :guilabel:`Save` or :guilabel:`Export` actions.


Variables Created
------------------

* **\_artist_\{artist_id\}_begin** - The begin date (birth date) of the artist
* **\_artist_\{artist_id\}_begin_country** - The begin two-character country code of the artist
* **\_artist_\{artist_id\}_begin_location** - The begin location of the artist
* **\_artist_\{artist_id\}_country** - The two-character country code for the artist
* **\_artist_\{artist_id\}_disambiguation** - The disambiguation information for the artist
* **\_artist_\{artist_id\}_end** - The end date (death date) of the artist
* **\_artist_\{artist_id\}_end_country** - The end two-character country code of the artist
* **\_artist_\{artist_id\}_end_location** - The end location of the artist
* **\_artist_\{artist_id\}_gender** - The gender of the artist
* **\_artist_\{artist_id\}_name** - The name of the artist
* **\_artist_\{artist_id\}_sort_name** - The sort name of the artist
* **\_artist_\{artist_id\}_type** - The type of artist (person, group, etc.)

.. note::

   A variable will only be created if the information is returned from MusicBrainz. For example, if a gender has not been specified in the MusicBrainz data then the **%\_artist_\{artist_id\}_gender%** variable will not be created.


Examples
---------

If you load the release **Wrecking Ball** (release `8c759d7a-2ade-4201-abc2-a2a7c1a6ad6c <https://musicbrainz.org/release/8c759d7a-2ade-4201-abc2-a2a7c1a6ad6c>`_) by Sarah Blackwood (artist `af7e5ea9-bd58-4346-8f78-d672e9f297f7 <https://musicbrainz.org/artist/af7e5ea9-bd58-4346-8f78-d672e9f297f7>`_), Jenni Pleau (artist `07fa21a9-c253-4ed0-b711-d63f7965b723 <https://musicbrainz.org/artist/07fa21a9-c253-4ed0-b711-d63f7965b723>`_) & Emily Bones (artist `541d331c-f041-4895-b8f2-7db9e27dc5ab <https://musicbrainz.org/artist/541d331c-f041-4895-b8f2-7db9e27dc5ab>`_), the following variables will be created:

Sarah Blackwood (primary artist):

* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_begin** = "1980-10-18"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_begin_country** = "CA"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_begin_location** = "Burlington, Ontario, Canada"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_country** = "CA"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_disambiguation** = "rockabilly, + "Somebody That I Used to Know""
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_gender** = "Female"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_location** = "Canada"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_name** = "Sarah Blackwood"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_sort_name** = "Blackwood, Sarah"
* **\_artist_af7e5ea9_bd58_4346_8f78_d672e9f297f7_type** = "Person"

Jenny Pleau (additional artist)

* **\_artist_07fa21a9_c253_4ed0_b711_d63f7965b723_country** = "CA"
* **\_artist_07fa21a9_c253_4ed0_b711_d63f7965b723_gender** = "Female"
* **\_artist_07fa21a9_c253_4ed0_b711_d63f7965b723_location** = "Kitchener, Ontario, Canada"
* **\_artist_07fa21a9_c253_4ed0_b711_d63f7965b723_name** = "Jenni Pleau"
* **\_artist_07fa21a9_c253_4ed0_b711_d63f7965b723_sort_name** = "Pleau, Jenni"
* **\_artist_07fa21a9_c253_4ed0_b711_d63f7965b723_type** = "Person"

Emily Bones (additional artist)

* **\_artist_541d331c_f041_4895_b8f2_7db9e27dc5ab_gender** = "Female"
* **\_artist_541d331c_f041_4895_b8f2_7db9e27dc5ab_name** = "Emily Bones"
* **\_artist_541d331c_f041_4895_b8f2_7db9e27dc5ab_sort_name** = "Bones, Emily"
* **\_artist_541d331c_f041_4895_b8f2_7db9e27dc5ab_type** = "Person"

Note that variables will only be created for information that exists for the artist's record.

This could be used to set a **%country%** tag to the country code of the (primary) album artist with a tagging script like:

.. code-block:: taggerscript

   $set(_tmp,_artist_$getmulti(%musicbrainz_albumartistid%,0)_)
   $set(country,$if2($get(%_tmp%country),$get(%_tmp%begin_country),$get(%_tmp%end_country),xx))

Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-additional-artists-details>`_.
