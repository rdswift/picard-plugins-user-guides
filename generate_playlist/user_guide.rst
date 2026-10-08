Generate Playlist
==================

Overview
---------

This plugin allows the user to generate a playlist from selected albums in Picard. The output is written to a ``*.m3u8`` file with UTF-8 encoded text.

This plugin is based on the Picard 2 plugin "Generate M3U playlist" by Francis Chin, Sambhav Kothari and Chris Hylen. See https://github.com/metabrainz/picard-plugins/blob/5a63f009/plugins/playlist/playlist.py for the original Picard 2 plugin code.


What it Does
-------------

This plugin provides a new context menu action for albums to write a playlist file for the selected albums.

To create a playlist, select one or more albums and right-click on the selection to bring up the context menu. Then click on the :menuselection:`Plugins --> Generate playlist` action to bring up a save dialog, allowing you to confirm the name and location of the playlist file being written. If only a single album has been selected, the proposed file name will be based on the album artist (if not Various Artists) and album name. If multiple albums are selected the proposed file name will be based on the first album in the selection list. The proposed file location will be the directory common to all of the audio files contained in the playlist. For example, if the audio files are ``/a/b/c/d/1.mp3``, ``/a/b/c/2.mp3`` and ``/a/b/e/3.mp3``, the proposed output directory will be ``/a/b``.

Relative paths are used where audio files are in the same directory as the playlist, otherwise absolute (full) paths are used in the playlist file.

Each file matched to one of the selected albums will be included in the playlist file generated. Album tracks with no attached audio file will not be included.


Option Settings
----------------

There are no option settings for this plugin.


Examples
---------

There are no examples.


Source Code
----------------

The source code for this plugin is available on `GitHub <https://github.com/rdswift/picard-plugin-generate-playlist>`_.
