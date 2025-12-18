Key Wheel Converter
=======================

Overview
---------

This plugin provides the ability to convert key information between 'camelot', 'open key', 'standard' and 'traktor' formats.


What it Does
----------------

It adds four new scripting functions:

- **$key2camelot(key)** returns the key string ``key`` in camelot key format.
- **$key2openkey(key)** returns the key string ``key`` in open key format.
- **$key2standard(key[,symbols])** returns the key string ``key`` in standard key format.  If the optional argument ``symbols`` is set, then the '♭' and '#' symbols will be used, rather than spelling out '-Flat' and '-Sharp'.
- **$key2traktor(key)** returns the key string ``key`` in traktor key format.

The ``key`` argument can be entered in any of the supported formats, such as '2B' (camelot), '6d' (open key), 'A♭ Minor' (standard with symbols), 'A-Flat Minor' (standard with text) or 'C#' (traktor).  If the ``key`` argument is not recognized as one of the standard keys in the supported formats, then an empty string will be returned.


Option Settings
----------------

There are no option settings for this plugin.


Examples
---------

The following tables shows the outputs of the various functions for different key inputs:

.. code-block:: none

   Input Key       | $key2camelot | $key2openkey | $key2standard | $key2traktor
   ----------------|--------------|--------------|---------------|---------------
   2B              | 2B           | 6d           | B-Flat Minor  | A#
   6d              | 2B           | 6d           | B-Flat Minor  | A#
   B-Flat Minor    | 2B           | 6d           | B-Flat Minor  | A#
   B♭ Minor        | 2B           | 6d           | B-Flat Minor  | A#
   A#              | 2B           | 6d           | B-Flat Minor  | A#
   11A             | 11A          | 3m           | F Major       | F
   3m              | 11A          | 3m           | F Major       | F
   F Major         | 11A          | 3m           | F Major       | F
   F               | 11A          | 3m           | F Major       | F
   C#              | 1D           | 5d           | C-Sharp Major | C#
   Unknown Key     | (blank)      | (blank)      | (blank)       | (blank)


Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-key-wheel-converter>`_.
