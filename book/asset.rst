=========
Asset
=========

Asset, in our scope, is basically a stylesheet, javascript, or image file.

Nilead uses a custom flavor of assets management based on `Assetic Bundle <https://github.com/symfony/AsseticBundle>`_ and `Liip Theme Bundle <https://github.com/liip/LiipThemeBundle>`_


******************************************************
Delayed loading assets (stylesheets/Javascripts)
******************************************************

To support 3rd party modules hooking into our system and possibly requesting their own javascripts/stylesheets etc we need to delay the processing of all these requests as late as possible to:

- gather a complete list of assets
- root out all possible duplication
- combine them into a minimal number of files to reduce overhead
- try to use cdn version of the requested asset if possible
- rewrite relative paths inside css files to make them theme-aware

*****************************
Advanced Inventory Management
*****************************

For more advanced tracking purpose, Nilead also allows store owner(s) to keep track of the following information:

- location (facility, container)
- in/out date of each current available on hand lot
- inventory adjustment history
- inventory variance history (difference between physical inventory vs on-system inventory)

For all the reasons above, we introduce 2 new Twig functions to include your assets

.. code-block:: twig
   {{ add_javascripts (['javascript1.js', 'javascript2.js'], ['filter1'], ['option1']}}

   {{ add_stylesheets (['stylesheet1.css', 'stylesheet2.css'], ['filter1'], ['option1']}}