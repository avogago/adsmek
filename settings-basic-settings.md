Title: Settings / Basic settings
authors: docs.getpelican.com
summary: Pelican is configurable thanks to a settings file


# Settings[¶](#settings "Permalink to this headline")

Pelican is configurable thanks to a settings file you can pass to the command line:

	pelican content -s path/to/your/pelicanconf.py

If you used the  `pelican-quickstart`  command, your primary settings file will be named  `pelicanconf.py`  by default.

> Note
> 
> When experimenting with different settings (especially the metadata
> ones) caching may interfere and the changes may not be visible. In
> such cases disable caching with  `LOAD_CONTENT_CACHE  =  False`  or
> use the  `--ignore-cache`  command-line switch.

Settings are configured in the form of a Python module (a file). There is an  [example settings file](https://github.com/getpelican/pelican/raw/master/samples/pelican.conf.py)  available for reference.

To see a list of current settings in your environment, including both default and any customized values, run the following command (append one or more specific setting names as arguments to see values for those settings only):

pelican --print-settings

All the setting identifiers must be set in all-caps, otherwise they will not be processed. Setting values that are numbers (5, 20, etc.), booleans (True, False, None, etc.), dictionaries, or tuples should  _not_  be enclosed in quotation marks. All other values (i.e., strings)  _must_  be enclosed in quotation marks.

Unless otherwise specified, settings that refer to paths can be either absolute or relative to the configuration file. The settings you define in the configuration file will be passed to the templates, which allows you to use your settings to add site-wide content.

Here is a list of settings for Pelican:

## Basic settings[¶](#basic-settings "Permalink to this headline")

`USE_FOLDER_AS_CATEGORY = True`

When you don’t specify a category in your post metadata, set this setting to  `True`, and organize your articles in subfolders, the subfolder will become the category of your post. If set to  `False`,  `DEFAULT_CATEGORY`  will be used as a fallback.

`DEFAULT_CATEGORY = 'misc'`

The default category to fall back on.

`DISPLAY_PAGES_ON_MENU = True`

Whether to display pages on the menu of the template. Templates may or may not honor this setting.

`DISPLAY_CATEGORIES_ON_MENU = True`

Whether to display categories on the menu of the template. Templates may or not honor this setting.

`DOCUTILS_SETTINGS = {}`

Extra configuration settings for the docutils publisher (applicable only to reStructuredText). See  [Docutils Configuration](http://docutils.sourceforge.net/docs/user/config.html)  settings for more details.

`DELETE_OUTPUT_DIRECTORY = False`

Delete the output directory, and  **all**  of its contents, before generating new files. This can be useful in preventing older, unnecessary files from persisting in your output. However,  **this is a destructive setting and should be handled with extreme care.**

`OUTPUT_RETENTION = []`

A list of filenames that should be retained and not deleted from the output directory. One use case would be the preservation of version control data.

Example:

OUTPUT_RETENTION = [".hg", ".git", ".bzr"]

`JINJA_ENVIRONMENT = {'trim_blocks': True, 'lstrip_blocks': True}`

A dictionary of custom Jinja2 environment variables you want to use. This also includes a list of extensions you may want to include. See  [Jinja Environment documentation](http://jinja.pocoo.org/docs/dev/api/#jinja2.Environment).

`JINJA_FILTERS = {}`

A dictionary of custom Jinja2 filters you want to use. The dictionary should map the filtername to the filter function.

Example:

JINJA_FILTERS = {'urlencode': urlencode_filter}

See  [Jinja custom filters documentation](http://jinja.pocoo.org/docs/api/#custom-filters).

`LOG_FILTER = []`

A list of tuples containing the logging level (up to  `warning`) and the message to be ignored.

Example:

LOG_FILTER = [(logging.WARN, 'TAG_SAVE_AS is set to False')]

`READERS = {}`

A dictionary of file extensions / Reader classes for Pelican to process or ignore.

For example, to avoid processing .html files, set:

READERS = {'html': None}

To add a custom reader for the  `foo`  extension, set:

READERS = {'foo': FooReader}

`IGNORE_FILES = ['.#*']`

A list of glob patterns. Files and directories matching any of these patterns will be ignored by the processor. For example, the default  `['.#*']`  will ignore emacs lock files, and  `['__pycache__']`  would ignore Python 3’s bytecode caches.

`MARKDOWN = {...}`

Extra configuration settings for the Markdown processor. Refer to the Python Markdown documentation’s  [Options section](https://python-markdown.github.io/reference/#markdown)  for a complete list of supported options. The  `extensions`  option will be automatically computed from the  `extension_configs`  option.

Defaults to:

	MARKDOWN = {
	    'extension_configs': {
	        'markdown.extensions.codehilite': {'css_class': 'highlight'},
	        'markdown.extensions.extra': {},
	        'markdown.extensions.meta': {},
	    },
	    'output_format': 'html5',
	}

> Note
> 
> The dictionary defined in your settings file will replace this default one.


`OUTPUT_PATH = 'output/'`

Where to output the generated files.

`PATH`[¶](#PATH "Permalink to this definition")

Path to content directory to be processed by Pelican. If undefined, and content path is not specified via an argument to the  `pelican`  command, Pelican will use the current working directory.

`PAGE_PATHS = ['pages']`

A list of directories and files to look at for pages, relative to  `PATH`.

`PAGE_EXCLUDES = []`

A list of directories to exclude when looking for pages in addition to  `ARTICLE_PATHS`.

`ARTICLE_PATHS = ['']`

A list of directories and files to look at for articles, relative to  `PATH`.

`ARTICLE_EXCLUDES = []`

A list of directories to exclude when looking for articles in addition to  `PAGE_PATHS`.

`OUTPUT_SOURCES = False`

Set to True if you want to copy the articles and pages in their original format (e.g. Markdown or reStructuredText) to the specified  `OUTPUT_PATH`.

`OUTPUT_SOURCES_EXTENSION = '.text'`

Controls the extension that will be used by the SourcesGenerator. Defaults to  `.text`. If not a valid string the default value will be used.

`PLUGINS = []`

The list of plugins to load. See  [Plugins](https://docs.getpelican.com/en/stable/plugins.html#plugins).

`PLUGIN_PATHS = []`

A list of directories where to look for plugins. See  [Plugins](https://docs.getpelican.com/en/stable/plugins.html#plugins).

`SITENAME = 'A Pelican Blog'`

Your site name

`SITEURL`[¶](#SITEURL "Permalink to this definition")

Base URL of your web site. Not defined by default, so it is best to specify your SITEURL; if you do not, feeds will not be generated with properly-formed URLs. If your site is available via HTTPS, this setting should begin with  `https://`  — otherwise use  `http://`. Then append your domain, with no trailing slash at the end. Example:  `SITEURL  =  'https://example.com'`

`STATIC_PATHS = ['images']`

A list of directories (relative to  `PATH`) in which to look for static files. Such files will be copied to the output directory without modification. Articles, pages, and other content source files will normally be skipped, so it is safe for a directory to appear both here and in  `PAGE_PATHS`  or  `ARTICLE_PATHS`. Pelican’s default settings include the “images” directory here.

`STATIC_EXCLUDES = []`

A list of directories to exclude when looking for static files.

`STATIC_EXCLUDE_SOURCES = True`

If set to False, content source files will not be skipped when copying files found in  `STATIC_PATHS`. This setting is for backward compatibility with Pelican releases before version 3.5. It has no effect unless  `STATIC_PATHS`  contains a directory that is also in  `ARTICLE_PATHS`  or  `PAGE_PATHS`. If you are trying to publish your site’s source files, consider using the  `OUTPUT_SOURCES`  setting instead.

`STATIC_CREATE_LINKS = False`

Create links instead of copying files. If the content and output directories are on the same device, then create hard links. Falls back to symbolic links if the output directory is on a different filesystem. If symlinks are created, don’t forget to add the  `-L`  or  `--copy-links`  option to rsync when uploading your site.

`STATIC_CHECK_IF_MODIFIED = False`

If set to  `True`, and  `STATIC_CREATE_LINKS`  is  `False`, compare mtimes of content and output files, and only copy content files that are newer than existing output files.

`TYPOGRIFY = False`

If set to True, several typographical improvements will be incorporated into the generated HTML via the  [Typogrify](https://pypi.python.org/pypi/typogrify)  library, which can be installed via:  `pip  install  typogrify`

`TYPOGRIFY_IGNORE_TAGS = []`

A list of tags for Typogrify to ignore. By default Typogrify will ignore  `pre`  and  `code`  tags. This requires that Typogrify version 2.0.4 or later is installed

`SUMMARY_MAX_LENGTH = 50`

When creating a short summary of an article, this will be the default length (measured in words) of the text created. This only applies if your content does not otherwise specify a summary. Setting to  `None`  will cause the summary to be a copy of the original content.

`WITH_FUTURE_DATES = True`

If disabled, content with dates in the future will get a default status of  `draft`. See  [Reading only modified content](#reading-only-modified-content)  for caveats.

`INTRASITE_LINK_REGEX = '[{|](?P<what>.*?)[|}]'`

Regular expression that is used to parse internal links. Default syntax when linking to internal files, tags, etc., is to enclose the identifier, say  `filename`, in  `{}`  or  `||`. Identifier between  `{`  and  `}`  goes into the  `what`  capturing group. For details see  [Linking to internal content](https://docs.getpelican.com/en/stable/content.html#ref-linking-to-internal-content).

`PYGMENTS_RST_OPTIONS = []`

A list of default Pygments settings for your reStructuredText code blocks. See  [Syntax highlighting](https://docs.getpelican.com/en/stable/content.html#internal-pygments-options)  for a list of supported options.

`SLUGIFY_SOURCE = 'title'`

Specifies where you want the slug to be automatically generated from. Can be set to  `title`  to use the ‘Title:’ metadata tag or  `basename`  to use the article’s file name when creating the slug.

`CACHE_CONTENT = False`

If  `True`, saves content in caches. See  [Reading only modified content](#reading-only-modified-content)  for details about caching.

`CONTENT_CACHING_LAYER = 'reader'`

If set to  `'reader'`, save only the raw content and metadata returned by readers. If set to  `'generator'`, save processed content objects.

`CACHE_PATH = 'cache'`

Directory in which to store cache files.

`GZIP_CACHE = True`

If  `True`, use gzip to (de)compress the cache files.

`CHECK_MODIFIED_METHOD = 'mtime'`

Controls how files are checked for modifications.

`LOAD_CONTENT_CACHE = False`

If  `True`, load unmodified content from caches.

`WRITE_SELECTED = []`

If this list is not empty,  **only**  output files with their paths in this list are written. Paths should be either absolute or relative to the current Pelican working directory. For possible use cases see  [Writing only selected content](#writing-only-selected-content).

`FORMATTED_FIELDS = ['summary']`

A list of metadata fields containing reST/Markdown content to be parsed and translated to HTML.

`PORT = 8000`

The TCP port to serve content from the output folder via HTTP when pelican is run with –listen

`BIND = ''`

The IP to which to bind the HTTP server.

## URL settings[¶](#url-settings "Permalink to this headline")

The first thing to understand is that there are currently two supported methods for URL formation:  _relative_  and  _absolute_. Relative URLs are useful when testing locally, and absolute URLs are reliable and most useful when publishing. One method of supporting both is to have one Pelican configuration file for local development and another for publishing. To see an example of this type of setup, use the  `pelican-quickstart`  script as described in the  [Installation](https://docs.getpelican.com/en/stable/install.html)  section, which will produce two separate configuration files for local development and publishing, respectively.

You can customize the URLs and locations where files will be saved. The  `*_URL`  and  `*_SAVE_AS`  variables use Python’s format strings. These variables allow you to place your articles in a location such as  `{slug}/index.html`  and link to them as  `{slug}`  for clean URLs (see example below). These settings give you the flexibility to place your articles and pages anywhere you want.

Note

If you specify a  `datetime`  directive, it will be substituted using the input files’ date metadata attribute. If the date is not specified for a particular file, Pelican will rely on the file’s  `mtime`  timestamp. Check the  [Python datetime documentation](https://docs.python.org/2/library/datetime.html#strftime-and-strptime-behavior)  for more information.

Also, you can use other file metadata attributes as well:

-   slug
-   date
-   lang
-   author
-   category

Example usage:

ARTICLE_URL = 'posts/{date:%Y}/{date:%b}/{date:%d}/{slug}/'
ARTICLE_SAVE_AS = 'posts/{date:%Y}/{date:%b}/{date:%d}/{slug}/index.html'
PAGE_URL = 'pages/{slug}/'
PAGE_SAVE_AS = 'pages/{slug}/index.html'

This would save your articles into something like  `/posts/2011/Aug/07/sample-post/index.html`, save your pages into  `/pages/about/index.html`, and render them available at URLs of  `/posts/2011/Aug/07/sample-post/`  and  `/pages/about/`, respectively.

`RELATIVE_URLS = False`

Defines whether Pelican should use document-relative URLs or not. Only set this to  `True`  when developing/testing and only if you fully understand the effect it can have on links/feeds.

`ARTICLE_URL = '{slug}.html'`

The URL to refer to an article.

`ARTICLE_SAVE_AS = '{slug}.html'`

The place where we will save an article.

`ARTICLE_LANG_URL = '{slug}-{lang}.html'`

The URL to refer to an article which doesn’t use the default language.

`ARTICLE_LANG_SAVE_AS = '{slug}-{lang}.html'`

The place where we will save an article which doesn’t use the default language.

`DRAFT_URL = 'drafts/{slug}.html'`

The URL to refer to an article draft.

`DRAFT_SAVE_AS = 'drafts/{slug}.html'`

The place where we will save an article draft.

`DRAFT_LANG_URL = 'drafts/{slug}-{lang}.html'`

The URL to refer to an article draft which doesn’t use the default language.

`DRAFT_LANG_SAVE_AS = 'drafts/{slug}-{lang}.html'`

The place where we will save an article draft which doesn’t use the default language.

`PAGE_URL = 'pages/{slug}.html'`

The URL we will use to link to a page.

`PAGE_SAVE_AS = 'pages/{slug}.html'`

The location we will save the page. This value has to be the same as PAGE_URL or you need to use a rewrite in your server config.

`PAGE_LANG_URL = 'pages/{slug}-{lang}.html'`

The URL we will use to link to a page which doesn’t use the default language.

`PAGE_LANG_SAVE_AS = 'pages/{slug}-{lang}.html'`

The location we will save the page which doesn’t use the default language.

`DRAFT_PAGE_URL = 'drafts/pages/{slug}.html'`

The URL used to link to a page draft.

`DRAFT_PAGE_SAVE_AS = 'drafts/pages/{slug}.html'`

The actual location a page draft is saved at.

`DRAFT_PAGE_LANG_URL = 'drafts/pages/{slug}-{lang}.html'`

The URL used to link to a page draft which doesn’t use the default language.

`DRAFT_PAGE_LANG_SAVE_AS = 'drafts/pages/{slug}-{lang}.html'`

The actual location a page draft which doesn’t use the default language is saved at.

`AUTHOR_URL = 'author/{slug}.html'`

The URL to use for an author.

`AUTHOR_SAVE_AS = 'author/{slug}.html'`

The location to save an author.

`CATEGORY_URL = 'category/{slug}.html'`

The URL to use for a category.

`CATEGORY_SAVE_AS = 'category/{slug}.html'`

The location to save a category.

`TAG_URL = 'tag/{slug}.html'`

The URL to use for a tag.

`TAG_SAVE_AS = 'tag/{slug}.html'`

The location to save the tag page.

Note

If you do not want one or more of the default pages to be created (e.g., you are the only author on your site and thus do not need an Authors page), set the corresponding  `*_SAVE_AS`  setting to  `''`  to prevent the relevant page from being generated.

Pelican can optionally create per-year, per-month, and per-day archives of your posts. These secondary archives are disabled by default but are automatically enabled if you supply format strings for their respective  `_SAVE_AS`  settings. Period archives fit intuitively with the hierarchical model of web URLs and can make it easier for readers to navigate through the posts you’ve written over time.

Example usage:

YEAR_ARCHIVE_SAVE_AS = 'posts/{date:%Y}/index.html'
MONTH_ARCHIVE_SAVE_AS = 'posts/{date:%Y}/{date:%b}/index.html'

With these settings, Pelican will create an archive of all your posts for the year at (for instance)  `posts/2011/index.html`  and an archive of all your posts for the month at  `posts/2011/Aug/index.html`.

Note

Period archives work best when the final path segment is  `index.html`. This way a reader can remove a portion of your URL and automatically arrive at an appropriate archive of posts, without having to specify a page name.

`YEAR_ARCHIVE_URL = ''`

The URL to use for per-year archives of your posts. Used only if you have the  `{url}`  placeholder in  `PAGINATION_PATTERNS`.

`YEAR_ARCHIVE_SAVE_AS = ''`

The location to save per-year archives of your posts.

`MONTH_ARCHIVE_URL = ''`

The URL to use for per-month archives of your posts. Used only if you have the  `{url}`  placeholder in  `PAGINATION_PATTERNS`.

`MONTH_ARCHIVE_SAVE_AS = ''`

The location to save per-month archives of your posts.

`DAY_ARCHIVE_URL = ''`

The URL to use for per-day archives of your posts. Used only if you have the  `{url}`  placeholder in  `PAGINATION_PATTERNS`.

`DAY_ARCHIVE_SAVE_AS = ''`

The location to save per-day archives of your posts.

`DIRECT_TEMPLATES`  work a bit differently than noted above. Only the  `_SAVE_AS`  settings are available, but it is available for any direct template.

`ARCHIVES_SAVE_AS = 'archives.html'`

The location to save the article archives page.

`AUTHORS_SAVE_AS = 'authors.html'`

The location to save the author list.

`CATEGORIES_SAVE_AS = 'categories.html'`

The location to save the category list.

`TAGS_SAVE_AS = 'tags.html'`

The location to save the tag list.

`INDEX_SAVE_AS = 'index.html'`

The location to save the list of all articles.

URLs for direct template pages are theme-dependent. Some themes use corresponding  `*_URL`  setting as string, while others hard-code them:  `'archives.html'`,  `'authors.html'`,  `'categories.html'`,  `'tags.html'`.

`SLUG_REGEX_SUBSTITUTIONS = [`

`(r'[^\w\s-]', ''), # remove non-alphabetical/whitespace/'-' chars`

`(r'(?u)\A\s*', ''), # strip leading whitespace`

`(r'(?u)\s*\Z', ''), # strip trailing whitespace`

`(r'[-\s]+', '-'), # reduce multiple whitespace or '-' to single '-'`

`]`

Regex substitutions to make when generating slugs of articles and pages. Specified as a list of pairs of  `(from,  to)`  which are applied in order, ignoring case. The default substitutions have the effect of removing non-alphanumeric characters and converting internal whitespace to dashes. Apart from these substitutions, slugs are always converted to lowercase ascii characters and leading and trailing whitespace is stripped. Useful for backward compatibility with existing URLs.

`AUTHOR_REGEX_SUBSTITUTIONS = SLUG_REGEX_SUBSTITUTIONS`

Regex substitutions for author slugs. Defaults to  `SLUG_REGEX_SUBSTITUTIONS`.

`CATEGORY_REGEX_SUBSTITUTIONS = SLUG_REGEX_SUBSTITUTIONS`

Regex substitutions for category slugs. Defaults to  `SLUG_REGEX_SUBSTITUTIONS`.

`TAG_REGEX_SUBSTITUTIONS = SLUG_REGEX_SUBSTITUTIONS`

Regex substitutions for tag slugs. Defaults to  `SLUG_REGEX_SUBSTITUTIONS`.

## Time and Date[¶](#time-and-date "Permalink to this headline")

`TIMEZONE`[¶](#TIMEZONE "Permalink to this definition")

The timezone used in the date information, to generate Atom and RSS feeds.

If no timezone is defined, UTC is assumed. This means that the generated Atom and RSS feeds will contain incorrect date information if your locale is not UTC.

Pelican issues a warning in case this setting is not defined, as it was not mandatory in previous versions.

Have a look at  [the wikipedia page](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)  to get a list of valid timezone values.

`DEFAULT_DATE = None`

The default date you want to use. If  `'fs'`, Pelican will use the file system timestamp information (mtime) if it can’t get date information from the metadata. If given any other string, it will be parsed by the same method as article metadata. If set to a tuple object, the default datetime object will instead be generated by passing the tuple to the  `datetime.datetime`  constructor.

`DEFAULT_DATE_FORMAT = '%a %d %B %Y'`

The default date format you want to use.

`DATE_FORMATS = {}`

If you manage multiple languages, you can set the date formatting here.

If no  `DATE_FORMATS`  are set, Pelican will fall back to  `DEFAULT_DATE_FORMAT`. If you need to maintain multiple languages with different date formats, you can set the  `DATE_FORMATS`  dictionary using the language name (`lang`  metadata in your post content) as the key.

In addition to the standard C89 strftime format codes that are listed in  [Python strftime documentation](https://docs.python.org/library/datetime.html#strftime-strptime-behavior), you can use the  `-`  character between  `%`  and the format character to remove any leading zeros. For example,  `%d/%m/%Y`  will output  `01/01/2014`  whereas  `%-d/%-m/%Y`  will result in  `1/1/2014`.

	DATE_FORMATS = {
	    'en': '%a, %d %b %Y',
	    'jp': '%Y-%m-%d(%a)',
	}

It is also possible to set different locale settings for each language by using a  `(locale,  format)`  tuple as a dictionary value which will override the  `LOCALE`  setting:

	# On Unix/Linux
	DATE_FORMATS = {
	    'en': ('en_US','%a, %d %b %Y'),
	    'jp': ('ja_JP','%Y-%m-%d(%a)'),
	}

	# On Windows  
	DATE_FORMATS  =  {  
	‘en’:  (‘usa’,’%a, %d %b %Y’),  
	‘jp’:  (‘jpn’,’%Y-%m-%d(%a)’),  
	}  

`LOCALE`[¶](#LOCALE "Permalink to this definition")

Change the locale  [[1]](#id2). A list of locales can be provided here or a single string representing one locale. When providing a list, all the locales will be tried until one works.

You can set locale to further control date format:

	 LOCALE = ('usa', 'jpn',      # On Windows
	           'en_US', 'ja_JP'   # On Unix/Linux
	)

For a list of available locales refer to  [locales on Windows](http://msdn.microsoft.com/en-us/library/cdax410z%28VS.71%29.aspx)  or on Unix/Linux, use the  `locale  -a`  command; see manpage  [locale(1)](https://linux.die.net/man/1/locale)  for more information.

[[1]](#id1)

Default is the system locale.

## Template pages[¶](#template-pages "Permalink to this headline")

`TEMPLATE_PAGES = None`

A mapping containing template pages that will be rendered with the blog entries. See  [Template pages](#template-pages).

If you want to generate custom pages besides your blog entries, you can point any Jinja2 template file with a path pointing to the file and the destination path for the generated file.

For instance, if you have a blog with three static pages — a list of books, your resume, and a contact page — you could have:

	TEMPLATE_PAGES = {'src/books.html': 'dest/books.html',
	                  'src/resume.html': 'dest/resume.html',
	                  'src/contact.html': 'dest/contact.html'}

`TEMPLATE_EXTENSIONS = ['.html']`

The extensions to use when looking up template files from template names.

`DIRECT_TEMPLATES = ['index', 'authors', 'categories', 'tags', 'archives']`

List of templates that are used directly to render content. Typically direct templates are used to generate index pages for collections of content (e.g., category and tag index pages). If the author, category and tag collections are not needed, set  `DIRECT_TEMPLATES  =  ['index',  'archives']`

`DIRECT_TEMPLATES`  are searched for over paths maintained in  `THEME_TEMPLATES_OVERRIDES`.

## Metadata[¶](#metadata "Permalink to this headline")

`AUTHOR`[¶](#AUTHOR "Permalink to this definition")

Default author (usually your name).

`DEFAULT_METADATA = {}`

The default metadata you want to use for all articles and pages.

`FILENAME_METADATA = r'(?P<date>d{4}-d{2}-d{2}).*'`

The regexp that will be used to extract any metadata from the filename. All named groups that are matched will be set in the metadata object. The default value will only extract the date from the filename.

For example, to extract both the date and the slug:

	FILENAME_METADATA = r'(?P<date>\d{4}-\d{2}-\d{2})_(?P<slug>.*)'

See also  `SLUGIFY_SOURCE`.

`PATH_METADATA = ''`

Like  `FILENAME_METADATA`, but parsed from a page’s full path relative to the content source directory.

`EXTRA_PATH_METADATA = {}`

Extra metadata dictionaries keyed by relative path. Relative paths require correct OS-specific directory separators (i.e. / in UNIX and \ in Windows) unlike some other Pelican file settings. Paths to a directory apply to all files under it. The most-specific path wins conflicts.

Not all metadata needs to be  [embedded in source file itself](https://docs.getpelican.com/en/stable/content.html#internal-metadata). For example, blog posts are often named following a  `YYYY-MM-DD-SLUG.rst`  pattern, or nested into  `YYYY/MM/DD-SLUG`  directories. To extract metadata from the filename or path, set  `FILENAME_METADATA`  or  `PATH_METADATA`  to regular expressions that use Python’s  [group name notation](https://docs.python.org/3/library/re.html#regular-expression-syntax)  `(?P<name>…)`. If you want to attach additional metadata but don’t want to encode it in the path, you can set  `EXTRA_PATH_METADATA`:

	EXTRA_PATH_METADATA = {
	    'relative/path/to/file-1': {
	        'key-1a': 'value-1a',
	        'key-1b': 'value-1b',
	        },
	    'relative/path/to/file-2': {
	        'key-2': 'value-2',
	        },
	    }

This can be a convenient way to shift the installed location of a particular file:

	# Take advantage of the following defaults
	# STATIC_SAVE_AS = '{path}'
	# STATIC_URL = '{path}'
	STATIC_PATHS = [
	    'static/robots.txt',
	    ]
	EXTRA_PATH_METADATA = {
	    'static/robots.txt': {'path': 'robots.txt'},
	    }

## Feed settings[¶](#feed-settings "Permalink to this headline")

By default, Pelican uses Atom feeds. However, it is also possible to use RSS feeds if you prefer.

Pelican generates category feeds as well as feeds for all your articles. It does not generate feeds for tags by default, but it is possible to do so using the  `TAG_FEED_ATOM`  and  `TAG_FEED_RSS`  settings:

`FEED_DOMAIN = None, i.e. base URL is "/"`

The domain prepended to feed URLs. Since feed URLs should always be absolute, it is highly recommended to define this (e.g., “[https://feeds.example.com](https://feeds.example.com/)”). If you have already explicitly defined SITEURL (see above) and want to use the same domain for your feeds, you can just set:  `FEED_DOMAIN  =  SITEURL`.

`FEED_ATOM = None, i.e. no Atom feed`

The location to save the Atom feed.

`FEED_ATOM_URL = None`

Relative URL of the Atom feed. If not set,  `FEED_ATOM`  is used both for save location and URL.

`FEED_RSS = None, i.e. no RSS`

The location to save the RSS feed.

`FEED_RSS_URL = None`

Relative URL of the RSS feed. If not set,  `FEED_RSS`  is used both for save location and URL.

`FEED_ALL_ATOM = 'feeds/all.atom.xml'`

The location to save the all-posts Atom feed: this feed will contain all posts regardless of their language.

`FEED_ALL_ATOM_URL = None`

Relative URL of the all-posts Atom feed. If not set,  `FEED_ALL_ATOM`  is used both for save location and URL.

`FEED_ALL_RSS = None, i.e. no all-posts RSS`

The location to save the the all-posts RSS feed: this feed will contain all posts regardless of their language.

`FEED_ALL_RSS_URL = None`

Relative URL of the all-posts RSS feed. If not set,  `FEED_ALL_RSS`  is used both for save location and URL.

`CATEGORY_FEED_ATOM = 'feeds/{slug}.atom.xml'`

The location to save the category Atom feeds.  [[2]](#id14)

`CATEGORY_FEED_ATOM_URL = None`

Relative URL of the category Atom feeds, including the  `{slug}`  placeholder.  [[2]](#id14)  If not set,  `CATEGORY_FEED_ATOM`  is used both for save location and URL.

`CATEGORY_FEED_RSS = None, i.e. no RSS`

The location to save the category RSS feeds, including the  `{slug}`  placeholder.  [[2]](#id14)

`CATEGORY_FEED_RSS_URL = None`

Relative URL of the category RSS feeds, including the  `{slug}`  placeholder.  [[2]](#id14)  If not set,  `CATEGORY_FEED_RSS`  is used both for save location and URL.

`AUTHOR_FEED_ATOM = 'feeds/{slug}.atom.xml'`

The location to save the author Atom feeds.  [[2]](#id14)

`AUTHOR_FEED_ATOM_URL = None`

Relative URL of the author Atom feeds, including the  `{slug}`  placeholder.  [[2]](#id14)  If not set,  `AUTHOR_FEED_ATOM`  is used both for save location and URL.

`AUTHOR_FEED_RSS = 'feeds/{slug}.rss.xml'`

The location to save the author RSS feeds.  [[2]](#id14)

`AUTHOR_FEED_RSS_URL = None`

Relative URL of the author RSS feeds, including the  `{slug}`  placeholder.  [[2]](#id14)  If not set,  `AUTHOR_FEED_RSS`  is used both for save location and URL.

`TAG_FEED_ATOM = None, i.e. no tag feed`

The location to save the tag Atom feed, including the  `{slug}`  placeholder.  [[2]](#id14)

`TAG_FEED_ATOM_URL = None`

Relative URL of the tag Atom feed, including the  `{slug}`  placeholder.  [[2]](#id14)

`TAG_FEED_RSS = None, i.e. no RSS tag feed`

Relative URL to output the tag RSS feed, including the  `{slug}`  placeholder. If not set,  `TAG_FEED_RSS`  is used both for save location and URL.

`FEED_MAX_ITEMS`[¶](#FEED_MAX_ITEMS "Permalink to this definition")

Maximum number of items allowed in a feed. Feed item quantity is unrestricted by default.

`RSS_FEED_SUMMARY_ONLY = True`

Only include item summaries in the  `description`  tag of RSS feeds. If set to  `False`, the full content will be included instead. This setting doesn’t affect Atom feeds, only RSS ones.

If you don’t want to generate some or any of these feeds, set the above variables to  `None`.

[2]

_([1](#id4),  [2](#id5),  [3](#id6),  [4](#id7),  [5](#id8),  [6](#id9),  [7](#id10),  [8](#id11),  [9](#id12),  [10](#id13))_  `{slug}`  is replaced by name of the category / author / tag.

## Pagination[¶](#pagination "Permalink to this headline")

The default behaviour of Pelican is to list all the article titles along with a short description on the index page. While this works well for small-to-medium sites, sites with a large quantity of articles will probably benefit from paginating this list.

You can use the following settings to configure the pagination.

`DEFAULT_ORPHANS = 0`

The minimum number of articles allowed on the last page. Use this when you don’t want the last page to only contain a handful of articles.

`DEFAULT_PAGINATION = False`

The maximum number of articles to include on a page, not including orphans. False to disable pagination.

`PAGINATED_TEMPLATES = {'index': None, 'tag': None, 'category': None, 'author': None}`

The templates to use pagination with, and the number of articles to include on a page. If this value is  `None`, it defaults to  `DEFAULT_PAGINATION`.

	`PAGINATION_PATTERNS = (`

	`(1, '{name}{extension}', '{name}{extension}'),`

	`(2, '{name}{number}{extension}', '{name}{number}{extension}'),`

	`)`

> A set of patterns that are used to determine advanced pagination output.

### Using Pagination Patterns[¶](#using-pagination-patterns "Permalink to this headline")

By default, pages subsequent to  `.../foo.html`  are created as  `.../foo2.html`, etc. The  `PAGINATION_PATTERNS`  setting can be used to change this. It takes a sequence of triples, where each triple consists of:

	(minimum_page, page_url, page_save_as,)

For  `page_url`  and  `page_save_as`, you may use a number of variables.  `{url}`  and  `{save_as}`  correspond respectively to the  `*_URL`  and  `*_SAVE_AS`  values of the corresponding page type (e.g.  `ARTICLE_SAVE_AS`). If  `{save_as}  ==  foo/bar.html`, then  `{name}  ==  foo/bar`  and  `{extension}  ==  .html`.  `{base_name}`  equals  `{name}`  except that it strips trailing  `/index`  if present.  `{number}`  equals the page number.

For example, if you want to leave the first page unchanged, but place subsequent pages at  `.../page/2/`  etc, you could set  `PAGINATION_PATTERNS`  as follows:

	PAGINATION_PATTERNS = (
	    (1, '{url}', '{save_as}',
	    (2, '{base_name}/page/{number}/', '{base_name}/page/{number}/index.html'),
	)

## Translations[¶](#translations "Permalink to this headline")

Pelican offers a way to translate articles. See the  [Content](https://docs.getpelican.com/en/stable/content.html)  section for more information.

`DEFAULT_LANG = 'en'`

The default language to use.

`ARTICLE_TRANSLATION_ID = 'slug'`

The metadata attribute(s) used to identify which articles are translations of one another. May be a string or a collection of strings. Set to  `None`  or  `False`  to disable the identification of translations.

`PAGE_TRANSLATION_ID = 'slug'`

The metadata attribute(s) used to identify which pages are translations of one another. May be a string or a collection of strings. Set to  `None`  or  `False`  to disable the identification of translations.

`TRANSLATION_FEED_ATOM = 'feeds/all-{lang}.atom.xml'`

The location to save the Atom feed for translations.  [[3]](#id18)

`TRANSLATION_FEED_ATOM_URL = None`

Relative URL of the Atom feed for translations, including the  `{lang}`  placeholder.  [[3]](#id18)  If not set,  `TRANSLATION_FEED_ATOM`  is used both for save location and URL.

`TRANSLATION_FEED_RSS = None, i.e. no RSS`

Where to put the RSS feed for translations.

`TRANSLATION_FEED_RSS_URL = None`

Relative URL of the RSS feed for translations, including the  `{lang}`  placeholder.  [[3]](#id18)  If not set,  `TRANSLATION_FEED_RSS`  is used both for save location and URL.

[3]

_([1](#id15),  [2](#id16),  [3](#id17))_  {lang} is the language code

## Ordering content[¶](#ordering-content "Permalink to this headline")

`NEWEST_FIRST_ARCHIVES = True`

Order archives by newest first by date. (False: orders by date with older articles first.)

`REVERSE_CATEGORY_ORDER = False`

Reverse the category order. (True: lists by reverse alphabetical order; default lists alphabetically.)

`ARTICLE_ORDER_BY = 'reversed-date'`

Defines how the articles (`articles_page.object_list`  in the template) are sorted. Valid options are: metadata as a string (use  `reversed-`  prefix the reverse the sort order), special option  `'basename'`  which will use the basename of the file (without path) or a custom function to extract the sorting key from articles. The default value,  `'reversed-date'`, will sort articles by date in reverse order (i.e. newest article comes first).

`PAGE_ORDER_BY = 'basename'`

Defines how the pages (`pages`  variable in the template) are sorted. Options are same as  `ARTICLE_ORDER_BY`. The default value,  `'basename'`  will sort pages by their basename.

## Themes[¶](#themes "Permalink to this headline")

Creating Pelican themes is addressed in a dedicated section (see  [Creating themes](https://docs.getpelican.com/en/stable/themes.html#theming-pelican)). However, here are the settings that are related to themes.

`THEME`[¶](#THEME "Permalink to this definition")

Theme to use to produce the output. Can be a relative or absolute path to a theme folder, or the name of a default theme or a theme installed via  `pelican-themes`  (see below).

`THEME_STATIC_DIR = 'theme'`

Destination directory in the output path where Pelican will place the files collected from  THEME_STATIC_PATHS. Default is  theme.

`THEME_STATIC_PATHS = ['static']`

Static theme paths you want to copy. Default value is  static, but if your theme has other static paths, you can put them here. If files or directories with the same names are included in the paths defined in this settings, they will be progressively overwritten.

`THEME_TEMPLATES_OVERRIDES = []`

A list of paths you want Jinja2 to search for templates before searching the theme’s  `templates/`  directory. Allows for overriding individual theme template files without having to fork an existing theme. Jinja2 searches in the following order: files in  `THEME_TEMPLATES_OVERRIDES`  first, then the theme’s  `templates/`.

You can also extend templates from the theme using the  `{%  extends  %}`  directive utilizing the  `!theme`  prefix as shown in the following example:

{% extends '!theme/article.html' %}

`CSS_FILE = 'main.css'`

Specify the CSS file you want to load.

By default, two themes are available. You can specify them using the  `THEME`  setting or by passing the  `-t`  option to the  `pelican`  command:

-   notmyidea
-   simple (a synonym for “plain text” :)

There are a number of other themes available at  [https://github.com/getpelican/pelican-themes](https://github.com/getpelican/pelican-themes). Pelican comes with  [pelican-themes](https://docs.getpelican.com/en/stable/pelican-themes.html), a small script for managing themes.

You can define your own theme, either by starting from scratch or by duplicating and modifying a pre-existing theme. Here is  [a guide on how to create your theme](https://docs.getpelican.com/en/stable/themes.html).

Following are example ways to specify your preferred theme:

	# Specify name of a built-in theme
	THEME = "notmyidea"
	# Specify name of a theme installed via the pelican-themes tool
	THEME = "chunk"
	# Specify a customized theme, via path relative to the settings file
	THEME = "themes/mycustomtheme"
	# Specify a customized theme, via absolute path
	THEME = "/home/myuser/projects/mysite/themes/mycustomtheme"

The built-in  `notmyidea`  theme can make good use of the following settings. Feel free to use them in your themes as well.

`SITESUBTITLE`[¶](#SITESUBTITLE "Permalink to this definition")

A subtitle to appear in the header.

`DISQUS_SITENAME`[¶](#DISQUS_SITENAME "Permalink to this definition")

Pelican can handle Disqus comments. Specify the Disqus sitename identifier here.

`GITHUB_URL`[¶](#GITHUB_URL "Permalink to this definition")

Your GitHub URL (if you have one). It will then use this information to create a GitHub ribbon.

`GOOGLE_ANALYTICS`[¶](#GOOGLE_ANALYTICS "Permalink to this definition")

Set to  `UA-XXXXX-Y`  Property’s tracking ID to activate Google Analytics.

`GA_COOKIE_DOMAIN`[¶](#GA_COOKIE_DOMAIN "Permalink to this definition")

Set cookie domain field of Google Analytics tracking code. Defaults to  `auto`.

`GOSQUARED_SITENAME`[¶](#GOSQUARED_SITENAME "Permalink to this definition")

Set to ‘XXX-YYYYYY-X’ to activate GoSquared.

`MENUITEMS`[¶](#MENUITEMS "Permalink to this definition")

A list of tuples (Title, URL) for additional menu items to appear at the beginning of the main menu.

`PIWIK_URL`[¶](#PIWIK_URL "Permalink to this definition")

URL to your Piwik server - without ‘[http://](http:)‘ at the beginning.

`PIWIK_SSL_URL`[¶](#PIWIK_SSL_URL "Permalink to this definition")

If the SSL-URL differs from the normal Piwik-URL you have to include this setting too. (optional)

`PIWIK_SITE_ID`[¶](#PIWIK_SITE_ID "Permalink to this definition")

ID for the monitored website. You can find the ID in the Piwik admin interface > Settings > Websites.

`LINKS`[¶](#LINKS "Permalink to this definition")

A list of tuples (Title, URL) for links to appear on the header.

`SOCIAL`[¶](#SOCIAL "Permalink to this definition")

A list of tuples (Title, URL) to appear in the “social” section.

`TWITTER_USERNAME`[¶](#TWITTER_USERNAME "Permalink to this definition")

Allows for adding a button to articles to encourage others to tweet about them. Add your Twitter username if you want this button to appear.

`LINKS_WIDGET_NAME`[¶](#LINKS_WIDGET_NAME "Permalink to this definition")

Allows override of the name of the links widget. If not specified, defaults to “links”.

`SOCIAL_WIDGET_NAME`[¶](#SOCIAL_WIDGET_NAME "Permalink to this definition")

Allows override of the name of the “social” widget. If not specified, defaults to “social”.

In addition, you can use the “wide” version of the  `notmyidea`  theme by adding the following to your configuration:

	CSS_FILE = "wide.css"

## Logging[¶](#logging "Permalink to this headline")

Sometimes, a long list of warnings may appear during site generation. Finding the  **meaningful**  error message in the middle of tons of annoying log output can be quite tricky. In order to filter out redundant log messages, Pelican comes with the  `LOG_FILTER`  setting.

`LOG_FILTER`  should be a list of tuples  `(level,  msg)`, each of them being composed of the logging level (up to  `warning`) and the message to be ignored. Simply populate the list with the log messages you want to hide, and they will be filtered out.

For example:

	import logging
	LOG_FILTER = [(logging.WARN, 'TAG_SAVE_AS is set to False')]

It is possible to filter out messages by a template. Check out source code to obtain a template.

For example:

	import logging
	LOG_FILTER = [(logging.WARN, 'Empty alt attribute for image %s in %s')]

Warning

Silencing messages by templates is a dangerous feature. It is possible to unintentionally filter out multiple message types with the same template (including messages from future Pelican versions). Proceed with caution.

Note

This option does nothing if  `--debug`  is passed.

## Reading only modified content[¶](#reading-only-modified-content "Permalink to this headline")

To speed up the build process, Pelican can optionally read only articles and pages with modified content.

When Pelican is about to read some content source file:

1.  The hash or modification time information for the file from a previous build are loaded from a cache file if  `LOAD_CONTENT_CACHE`  is  `True`. These files are stored in the  `CACHE_PATH`  directory. If the file has no record in the cache file, it is read as usual.
    
2.  The file is checked according to  `CHECK_MODIFIED_METHOD`:
    
    > -   If set to  `'mtime'`, the modification time of the file is checked.
    > -   If set to a name of a function provided by the  `hashlib`  module, e.g.  `'md5'`, the file hash is checked.
    > -   If set to anything else or the necessary information about the file cannot be found in the cache file, the content is read as usual.
    
3.  If the file is considered unchanged, the content data saved in a previous build corresponding to the file is loaded from the cache, and the file is not read.
    
4.  If the file is considered changed, the file is read and the new modification information and the content data are saved to the cache if  `CACHE_CONTENT`  is  `True`.
    

If  `CONTENT_CACHING_LAYER`  is set to  `'reader'`  (the default), the raw content and metadata returned by a reader are cached. If this setting is instead set to  `'generator'`, the processed content object is cached. Caching the processed content object may conflict with plugins (as some reading related signals may be skipped) and the  `WITH_FUTURE_DATES`  functionality (as the  `draft`  status of the cached content objects would not change automatically over time).

Checking modification times is faster than comparing file hashes, but it is not as reliable because  `mtime`  information can be lost, e.g., when copying content source files using the  `cp`  or  `rsync`  commands without the  `mtime`  preservation mode (which for  `rsync`  can be invoked by passing the  `--archive`  flag).

The cache files are Python pickles, so they may not be readable by different versions of Python as the pickle format often changes. If such an error is encountered, it is caught and the cache file is rebuilt automatically in the new format. The cache files will also be rebuilt after the  `GZIP_CACHE`  setting has been changed.

The  `--ignore-cache`  command-line option is useful when the whole cache needs to be regenerated, such as when making modifications to the settings file that will affect the cached content, or just for debugging purposes. When Pelican runs in autoreload mode, modification of the settings file will make it ignore the cache automatically if  `AUTORELOAD_IGNORE_CACHE`  is  `True`.

Note that even when using cached content, all output is always written, so the modification times of the generated  `*.html`  files will always change. Therefore,  `rsync`-based uploading may benefit from the  `--checksum`  option.

## Writing only selected content[¶](#writing-only-selected-content "Permalink to this headline")

When only working on a single article or page, or making tweaks to your theme, it is often desirable to generate and review your work as quickly as possible. In such cases, generating and writing the entire site output is often unnecessary. By specifying only the desired files as output paths in the  `WRITE_SELECTED`  list,  **only**  those files will be written. This list can be also specified on the command line using the  `--write-selected`  option, which accepts a comma-separated list of output file paths. By default this list is empty, so all output is written. See  [Site generation](https://docs.getpelican.com/en/stable/publish.html#site-generation)  for more details.

## Example settings[¶](#example-settings "Permalink to this headline")

	# -*- coding: utf-8 -*-
	from __future__ import unicode_literals

	AUTHOR  =  ‘Alexis Métaireau’  
	SITENAME  =  “Alexis’ log”  
	SITESUBTITLE  =  ‘A personal blog.’  
	SITEURL  =  ‘[http://blog.notmyidea.org](http://blog.notmyidea.org/)’  
	TIMEZONE  =  “Europe/Paris”

	# can be useful in development, but set to False when you’re ready to publish  
	RELATIVE_URLS  =  True

	GITHUB_URL  =  ‘[http://github.com/ametaireau/](http://github.com/ametaireau/)’  
	DISQUS_SITENAME  =  “blog-notmyidea”  
	REVERSE_CATEGORY_ORDER  =  True  
	LOCALE  =  “C”  
	DEFAULT_PAGINATION  =  4  
	DEFAULT_DATE  =  (2012,  3,  2,  14,  1,  1)

	FEED_ALL_RSS  =  ‘feeds/all.rss.xml’  
	CATEGORY_FEED_RSS  =  ‘feeds/{slug}.rss.xml’

	LINKS  =  ((‘Biologeek’,  ‘[http://biologeek.org](http://biologeek.org/)’),  
	(‘Filyb’,  “[http://filyb.info/](http://filyb.info/)”),  
	(‘Libert-fr’,  “[http://www.libert-fr.com](http://www.libert-fr.com/)”),  
	(‘N1k0’,  “[http://prendreuncafe.com/blog/](http://prendreuncafe.com/blog/)”),  
	(‘Tarek Ziadé’,  “[http://ziade.org/blog](http://ziade.org/blog)”),  
	(‘Zubin Mithra’,  “[http://zubin71.wordpress.com/](http://zubin71.wordpress.com/)”),)

	SOCIAL  =  ((‘twitter’,  ‘[http://twitter.com/ametaireau](http://twitter.com/ametaireau)’),  
	(‘lastfm’,  ‘[http://lastfm.com/user/akounet](http://lastfm.com/user/akounet)’),  
	(‘github’,  ‘[http://github.com/ametaireau](http://github.com/ametaireau)’),)

	# global metadata to all the contents  
	DEFAULT_METADATA  =  {‘yeah’:  ‘it is’}

	# path-specific metadata  
	EXTRA_PATH_METADATA  =  {  
	‘extra/robots.txt’:  {‘path’:  ‘robots.txt’},  
	}

	# static paths will be copied without parsing their contents  
	STATIC_PATHS  =  [  
	‘pictures’,  
	‘extra/robots.txt’,  
	]

	# custom page generated with a jinja2 template  
	TEMPLATE_PAGES  =  {‘pages/jinja2_template.html’:  ‘jinja2_template.html’}

	# code blocks with line numbers  
	PYGMENTS_RST_OPTIONS  =  {‘linenos’:  ‘table’}

	# foobar will not be used, because it’s not in caps. All configuration keys  
	# have to be in caps  
	foobar  =  “barbaz”