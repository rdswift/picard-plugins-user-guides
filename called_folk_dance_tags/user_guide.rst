Called Folk Dance Tags
=======================

Overview
---------

This plugin adds tags for traditional called folk dances based on the IETF Internet-Draft (I-D) `draft-swhited-contra-tags-04 <https://datatracker.ietf.org/doc/draft-swhited-contra-tags/>`_ by Sam Whited. The plugin registers the tags, with descriptions, for easy lookup in the script editor. It does not populate any of the tags.

.. note::

   This plugin makes no additional calls to the MusicBrainz website api for the information.


What it Does
----------------

This plugin registers the new tags within Picard so that they are available for lookup and autocompletion in the script editor. In addition, it provides proper names for the tags in the metadata editor panel. It does not populate any of the tags.


Option Settings
----------------

The plugin has no option settings.


Tags Registered
------------------

* **dance_caller** - The name of the dance callers heard in the track.
* **dance_choreographer** - The names of the authors of the dances being called.
* **dance_choreography** - The moves of the dance as text for called folk dances.
* **dance_crooked** - Whether a traditional called folk dance tune is "crooked" (ie. not in perfect dance form).
* **dance_form** - The form of a called dance with no particular format, eg. "contra" or "square dance" or "duple minor improper contra".
* **dance_intro** - The number of intro beats before the dance or any potatoes for called folk dances.
* **dance_issong** - Whether the track is a song (has sung vocals other than the caller) or a tune (instrumental only) for traditional music forms that make this distinction.
* **dance_license** - Like the license field except relating to the choreography of the dance being called for called folk dances.
* **dance_potatoes** - The number of "potatoes" (syncronization beats played before some traditional folk dances).
* **dance_roles** - The role terms used for calls in a called folk dance, eg. "Larks/Robins" or "Leads/Follows" or "Positional".
* **dance_start** - The start time (in milliseconds) of the first time through the dance in a called folk dance.
* **dance_times** - The number of complete times through the dance excluding any intro, outro, or potatoes for a called folk dance. The exact definition will depend on the type of dance.
* **dance_title** - The name of the dances being called for called folk dances.


Examples
---------

There are no examples for this plugin.


Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-called-folk-dance-tags>`_.
