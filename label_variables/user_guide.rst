Label Variables
=================

Overview
---------

This plugin provides variables containing label information for a release for use in user or file naming scripts.


What it Does
----------------

This plugin reads the release metadata provided to Picard and exposes the information in a number of additional variables for use in Picard scripts.

This plugin makes no additional calls to the MusicBrainz website api for the information.


Variables Created
-------------------

Label Variables
++++++++++++++++

* **_label_ids_multi** - All label IDs listed, as a multi-value
* **_label_names_multi** - All label names listed, as a multi-value
* **_label_sort_names_multi** - All label names listed (sort name), as a multi-value
* **_label_disambig_multi** - All label disambiguations listed, as a multi-value
* **_label_catalog_multi** - All label catalog numbers listed, as a multi-value
* **_label_label_count** - Count of the number of labels listed
* **_label_catalog_count** - Count of all catalog numbers listed

.. note::

   Variables will not be created if the data is missing.


Option Settings
----------------

There are no option settings for this plugin.


Examples
---------

Using the album "`Pretenders (club edition) <https://musicbrainz.org/release/21c0e66c-7994-474b-af1d-5c73578aba61>`_" by `Pretenders <https://musicbrainz.org/artist/e9c832b0-384b-4ee6-aec0-111372784aac>`_, the label variables created for the album are:

* **_label_ids_multi** = ['132282be-91ba-4185-ae10-0cb570a1288c', '851b17a3-8353-47fc-9f7b-cba5392b41cd', 'c4f2cf49-b57c-4cc1-8061-f54400704ac4', 'be0fec81-5c18-4494-8bbf-0d81dec006bf']
* **_label_names_multi** = ['BMG Direct', 'Real Records', 'Rhino', 'Sire Records']
* **_label_sort_names_multi** = ['BMG Direct', 'Real Records', 'Rhino', 'Sire Records']
* **_label_disambig_multi** = ["BMG's direct marketing company/club editions", 'WEA subsidiary', 'reissue label', '']
* **_label_catalog_multi** = ['D220040', 'R2 74178', 'R2 74178', 'R2 74178']
* **_label_label_count** = 4
* **_label_catalog_count** = 4


Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-label-variables>`_.
