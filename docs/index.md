For example, the mkdocs theme (browse source), contains the following directory structure (in part):

- css\
- fonts\
- img\
  - favicon.ico
  - grid.png
- js\
- 404.html
- base.html
- content.html
- nav-sub.html
- nav.html
- toc.html
To override any of the files contained in that theme, create a new directory next to your docs_dir:

mkdir custom_theme
And then point your mkdocs.yml configuration file at the new directory:

theme:
    name: mkdocs
    custom_dir: custom_theme/
To override the 404 error page ("file not found"), add a new template file named 404.html to the custom_theme directory. For information on what can be included in a template, review the documentation for building a custom theme.

To override the favicon, you can add a new icon file at custom_theme/img/favicon.ico.

To include a JavaScript library, copy the library to the custom_theme/js/ directory.

Your directory structure should now look like this:

- docs/
  - index.html
- custom_theme/
  - img/
    - favicon.ico
  - js/
    - somelib.js
  - 404.html
- config.yml
Note

Any files included in the parent theme (defined in name) but not included in the custom_dir will still be utilized. The custom_dir will only override/replace files in the parent theme. If you want to remove files, or build a theme from scratch, then you should review the documentation for building a custom theme.

Overriding Template Blocks
The built-in themes implement many of their parts inside template blocks which can be individually overridden in the main.html template. Simply create a main.html template file in your custom_dir and define replacement blocks within that file. Just make sure that the main.html extends base.html. For example, to alter the title of the MkDocs theme, your replacement main.html template would contain the following:


In the above example, the htmltitle block defined in your custom main.html file will be used in place of the default htmltitle block defined in the parent theme. You may re-define as many blocks as you desire, as long as those blocks are defined in the parent. For example, you could replace the Google Analytics script with one for a different service or replace the search feature with your own. You will need to consult the parent theme you are using to determine what blocks are available to override. The MkDocs and ReadTheDocs themes provide the following blocks:

site_meta: Contains meta tags in the document head.
htmltitle: Contains the page title in the document head.
styles: Contains the link tags for stylesheets.
libs: Contains the JavaScript libraries (jQuery, etc) included in the page header.
scripts: Contains JavaScript scripts which should execute after a page loads.
analytics: Contains the analytics script.
extrahead: An empty block in the <head> to insert custom tags/scripts/etc.
site_name: Contains the site name in the navigation bar.
site_nav: Contains the site navigation in the navigation bar.
search_button: Contains the search box in the navigation bar.
next_prev: Contains the next and previous buttons in the navigation bar.
repo: Contains the repository link in the navigation bar.
content: Contains the page content and table of contents for the page.
footer: Contains the page footer.
