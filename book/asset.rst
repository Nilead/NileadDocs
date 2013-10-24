=========
Asset
=========

Asset, in our scope, is basically a stylesheet, javascript, or image file.

Nilead uses a custom flavor of assets management based on `Assetic Bundle <https://github.com/symfony/AsseticBundle>`_ and `Liip Theme Bundle <https://github.com/liip/LiipThemeBundle>`_


******************************************************
Delayed loading assets (stylesheets/javascripts)
******************************************************

To support 3rd party modules hooking into our system and possibly requesting their own javascripts/stylesheets etc we need to delay the processing of all these requests as late as possible to:

- gather a complete list of assets
- root out all possible duplication
- combine them into a minimal number of files to reduce overhead
- try to use cdn version of the requested asset if possible
- rewrite relative paths inside css files to make them theme-aware

For all the reasons above, we introduce 2 new Twig functions to include your assets::
    {{ add_javascripts (['javascript1.js', 'javascript2.js'], ['filter1'], ['option1']}}
  
    {{ add_stylesheets (['stylesheet1.css', 'stylesheet2.css'], ['filter1'], ['option1']}}

Libraries
=========

There are certain libraries of assets such as jquery, jqueryui, bootstrap, etc... that are sometimes composed of a number of files and being used over and over again. To make using these libraries much easier and also avoid multiple loading of the same lib, we introduce another Twig function::
    {{ add_libs ('jquery', ['filter1'], ['option1']}}

*Note that libs will always be loaded FIRST before anything else.*

*For a list of supported libs and version, please visit our* `git repo <https://github.com/Nilead/NileadAsseticBundle/tree/master/Resources/config/libs>`_. *Fell free to fork and send pull requests.*

Note
=========

- We STRONGLY discourage the use of inline css and javascript, only use them when it is absolutely necessary.
- You can either pass a string or an array of string to the first parameter of the 3 functions above
- The **filters** and **options** paramters in the 3 functions above act exactly the same way with the **filters** and **options** parameters described in `Symfony document on asset management. <http://symfony.com/doc/current/cookbook/assetic/asset_management.html>`_
- There is another parameter that can be passed into the 3 functions above. The 4th parameter is a boolean parameter (default to false) and when set to true will ask the Assetic Manager to ignore the duplication and load the assets being requested again even if they are already requested else where. Be very careful with this option.

******************************************************
Theme-aware image
******************************************************

To provide better support for images, we introduce a new twig function::
    get_image('image_path.jpg', ['filter1'], ['option1'])
    
Note
=========

- You must pass a string or an array of string to the first parameter of the 3 functions above
- The **filters** and **options** paramters in the 3 functions above act exactly the same way with the **filters** and **options** parameters described in `Symfony document on asset management. <http://symfony.com/doc/current/cookbook/assetic/asset_management.html>`_