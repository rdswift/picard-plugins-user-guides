Language Name
=======================

Overview
---------

This plugin provides the ability to retrieve the full language name based on the three-character `ISO 639-3 <https://en.wikipedia.org/wiki/List_of_ISO_639-3_codes>`_ language code.


What it Does
----------------

It adds a new scripting function ``$language_name(code)`` that returns the full name for a three-character ISO 639-3 language code.

If an unknown ``code`` is entered, the function will return '**unknown**'. If there is no code entered, '**missing**' will be returned.

The function is available to both user scripts and file naming scripts.


Option Settings
----------------

There are no option settings for this plugin.


Examples
---------

The following examples have been graciously provided by **hiccup**:

You will need to use a script to tag your files with the full language names that this plugins makes available. A basic script to e.g. populate the 'language' tag with the full language name of the work could be:

.. code-block:: taggerscript

   $set(language,$language_name(%language%))

Or if you want to write the release language, you could use:

.. code-block:: taggerscript

   $set(release language,$language_name(%_releaselanguage%))

By default, when a release has no language code attached to it, the plugin will populate a tag with the text "**missing**". If for these cases you don't want a tag created at all, you could use a script like this:

.. code-block:: taggerscript

   $set(language_temp,$language_name(%language%))
   $if($in(%language_temp%,missing),,$set(language,%language_temp%))
   $delete(language_temp)

When a release has the code "**zxx**", the plugin will write "**no linguistic content**". While technically correct, you might prefer to have "**Instrumental**" in your tags instead. Integrated with the previous example script, you then could use:

.. code-block:: taggerscript

   $set(language_temp,$language_name(%language%))
   $if($in(%language_temp%,missing),,$if($in(%language_temp%,no linguistic content),$set(language,Instrumental),$set(language,%language_temp%)))
   $delete(language_temp)

If you are using a language other than English, you should change "no linguistic content" accordingly. E.g. for Dutch you should use:

.. code-block:: taggerscript

   $set(language_temp,$language_name(%language%))
   $if($in(%language_temp%,missing),,$if($in(%language_temp%,geen taalkundige inhoud),$set(language,Instrumentaal),$set(language,%language_temp%)))
   $delete(language_temp)


Supported Languages for Return Values
--------------------------------------

English is the output language used for all user interface languages not currently supported with a translation.

Supported translations of the language names from English are based on the translations entered into `Weblate <https://translations.metabrainz.org/projects/picard-plugins/#components>`_ under the "Language Name" component of the "Picard Plugins" project. Any help correcting / completing the current translations, or translation to other languages would be greatly appreciated.


Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-language-name>`_.
