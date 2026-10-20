Smart Case
===========

Overview
---------

This plugin adds a new scripting function ``$smart_case(text)`` to Capitalize The First Character In Every Word Of The Text. The conversion leaves words containing embedded uppercase as-is (i.e. USA or DoA).

This is based on the Picard v2 plugin "Smart Title Case" by Sophist (based on an earlier plugin by Javier Kohen).


What it Does
-------------

This plugin adds a new scripting function ``$smart_case(text)``.

Usage: **$smart_case(text)**

This will return ``text`` converted to Capitalize The First Character In Every Word Of The Text. The conversion leaves words containing embedded uppercase as-is (i.e. USA or DoA).


Option Settings
----------------

There are no option settings for this plugin.


Examples
---------

The following statements will return the values indicated:

.. code-block:: taggerscript

   $set(foo,tHe houR is upOn uS)
   $smart_case(%foo%)          ==>  "tHe houR Is upOn uS"
   $smart_case($lower(%foo%))  ==>  "The Hour Is Upon Us"

   $set(bar,Born in the USA)
   $smart_case(%bar%)          ==>  "Born In The USA"
   $smart_case($lower(%bar%))  ==>  "Born In The Usa"

   $set(baz,AC/DC a,b;c:d.e-f you're here)
   $smart_case(%baz%)          ==>  "AC/DC A,B;C:D.E-F You're Here"
   $smart_case($lower(%baz%))  ==>  "Ac/Dc A,B;C:D.E-F You're Here"


Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-smart-case>`_.
