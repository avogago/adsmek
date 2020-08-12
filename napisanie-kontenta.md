Title: Написание контента
authors: docs.getpelican.com
summary: Пеликан считает «статьи» хронологическим содержанием, например сообщениями в блоге, и, следовательно, связанными с датой. Идея «страниц» заключается в том, что они обычно не носят временный характер и используются для содержания, которое не меняется очень часто (например, страницы «О нас» или «Контакты»). Вы можете найти образцы контента в репозитории по адресу `samples/content/`.



## Написание контента[¶](https://docs.getpelican.com/en/stable/content.html#writing-content "Постоянная ссылка на этот заголовок")

## Статьи и страницы[¶](https://docs.getpelican.com/en/stable/content.html#articles-and-pages "Постоянная ссылка на этот заголовок")

Пеликан считает «статьи» хронологическим содержанием, например сообщениями в блоге, и, следовательно, связанными с датой.

Идея «страниц» заключается в том, что они обычно не носят временный характер и используются для содержания, которое не меняется очень часто (например, страницы «О нас» или «Контакты»).

Вы можете найти образцы контента в репозитории по адресу `samples/content/`.

## Метаданные файла[¶](https://docs.getpelican.com/en/stable/content.html#file-metadata "Постоянная ссылка на этот заголовок")

Пеликан старается быть достаточно умным, чтобы получить необходимую информацию из файловой системы (например, о категории ваших статей), но некоторую информацию вам необходимо предоставить в виде метаданных внутри ваших файлов.

Если вы пишете свой контент в формате reStructuredText, вы можете предоставить эти метаданные в текстовых файлах с помощью следующего синтаксиса (дайте вашему файлу `.rst` расширение):

    My super title
    ##############

    :date: 2010-10-03 10:20
    :modified: 2010-10-04 18:40
    :tags: thats, awesome
    :category: yeah
    :slug: my-super-post
    :authors: Alexis Metaireau, Conan Doyle
    :summary: Short version for index and feeds



    Мой  супер  заголовок 
    ##############
    
    :дата: 2010-10-03 10:20
    :изменено: 2010-10-04 18:40
    :теги:  вот ,  круто 
    :категория:  да 
    :slug:  моё-супер-сообщение 
    :авторы: Алексис Метеро, Конан Дойл
    :резюме: Краткая версия  для индекса и каналов


Вместо этого списки авторов и тегов могут разделяться точкой с запятой, что позволяет писать авторов и теги, содержащие запятые:

    :tags: pelican, publishing tool; pelican, bird
    :authors: Metaireau, Alexis; Doyle, Conan

    :tags: пеликан, издательский  инструмент; пеликан, птица 
    :авторы: Метеро, Алексис; Дойл , Конан

Пеликан реализует расширение для reStructuredText, чтобы включить поддержку `abbr` тега HTML. Чтобы использовать его, напишите в своем посте что-то вроде этого:

    This will be turned into :abbr:`HTML (HyperText Markup Language)`.
    Это будет преобразовано в :abbr:`HTML (язык разметки гипертекста)`. 


Вы также можете использовать Markdown синтаксис (с файлом , заканчивающимся в `.md`, `.markdown`, `.mkd`, или `.mdown`). Для создания Markdown требуется, чтобы вы сначала явно установили `Markdown` пакет, что можно сделать через .`pip  install  Markdown`

Pelican также поддерживает [расширения Markdown](https://python-markdown.github.io/extensions/) , которые, возможно, придется установить отдельно, если они не включены в `Markdown` пакет по умолчанию , и их можно настроить и загрузить с помощью `MARKDOWN` параметра.

Синтаксис метаданных для сообщений Markdown должен соответствовать следующему шаблону:

    Title: My super title
    Date: 2010-12-03 10:20
    Modified: 2010-12-05 19:30
    Category: Python
    Tags: pelican, publishing
    Slug: my-super-post
    Authors: Alexis Metaireau, Conan Doyle
    Summary: Short version for index and feeds

    This is the content of my super blog post.


    Название : Мой супер заголовок
    Дата: 2010-12-03 10:20
    Изменено: 2010-12-05 19:30
    Категория: Python 
    Теги: пеликан, публикация 
    Слаг: my-super-post 
    Авторы: Alexis  Metaireau ,  Conan  Doyle 
    Резюме: Short версия для индекса и каналов
        
    Здесь содержание статьи в моем супер блоге .   

   

Вы также можете иметь свои собственные ключи метаданных (при условии, что они не конфликтуют с зарезервированными ключевыми словами метаданных) для использования в ваших шаблонах. 

В следующей таблице содержится список зарезервированных ключевых слов метаданных:

Метаданные

| Metadata  |  Description |
|--|--|
title  |  Title of the article or page
date  |  Publication date (e.g., YYYY-MM-DD HH:SS)
modified  |  Modification date (e.g., YYYY-MM-DD HH:SS)
tags  |  Content tags, separated by commas
keywords  |  Content keywords, separated by commas (HTML content only)
category  |  Content category (one only — not multiple)
slug  |  Identifier used in URLs and translations
author  |  Content author, when there is only one
authors  |  Content authors, when there are multiple
summary  |  Brief description of content for index pages
lang  |  Content language ID (en, fr, etc.)
translation  |  Is content is a translation of another (true or false)
status  |  Content status: draft, hidden, or published
template  |  Name of template to use to generate content (without extension)
save_as  |  Save content to this relative file path
url  |  URL to use for this article/page


Перевод значений

| Метаданные  |  Описание |
|--|--|
`title`  |  Заголовок статьи или страницы
`date`  |  Дата публикации (например, )`YYYY-MM-DD  HH:SS`
`modified`  |  Дата модификации (например, )`YYYY-MM-DD  HH:SS`
`tags`  |  Теги содержимого, разделенные запятыми
`keywords`  |  Ключевые слова содержимого, разделенные запятыми (только содержимое HTML)
`category`  |  Категория контента (только одна, а не несколько)
`slug`  |  Идентификатор, используемый в URL-адресах и переводах
`author`  |  Автор контента, когда есть только один
`authors`  |  Авторы контента, когда есть несколько
`summary`  |  Краткое описание контента для индексных страниц
`lang`  |  Идентификатор языка контента ( `en`, `fr` и т. Д.)
`translation`  |  Является ли контент переводом другого ( `true` или `false`)
`status`  |  Содержание Статус: `draft`, `hidden` или `published`
`template`  |  Имя шаблона, который будет использоваться для создания контента (без расширения)
`save_as`  |  Сохранить содержимое по этому относительному пути к файлу
`url`  |  URL-адрес для этой статьи / страницы


Читатели для дополнительных форматов (например, [AsciiDoc](http://www.methods.co.nz/asciidoc/) ) доступны через плагины. Для этого обратитесь к репозиторию [pelican-plugins](https://github.com/getpelican/pelican-plugins) .

Пеликан также может обрабатывать файлы HTML, оканчивающиеся на `.html` и `.htm`. Пеликан очень просто интерпретирует HTML, считывая метаданные из `meta` тегов, заголовок из `title` тега и тело из `body` тега:

    <html>
        <head>
            <title>My super title</title>
            <meta name="tags" content="thats, awesome" />
            <meta name="date" content="2012-07-09 22:28" />
            <meta name="modified" content="2012-07-10 20:14" />
            <meta name="category" content="yeah" />
            <meta name="authors" content="Alexis Métaireau, Conan Doyle" />
            <meta name="summary" content="Short version for index and feeds" />
        </head>
        <body>
            This is the content of my super blog post.
        </body>
    </html>

    <html>
        <head>
            <title>Мой супер заголовок</title>
            <meta name="tags" content="thats, awesome" />
            <meta name="date" content="2012-07-09 22:28" />
            <meta name="modified" content="2012-07-10 20:14" />
            <meta name="category" content="О, да" />
            <meta name="authors" content="Алексис Métaireau, Конан Дойл" />
            <meta name="summary" content="Краткая версия для индекса и корм" />
        </head>
        <body>
            This is the content of my super blog post.
        </body>
    </html>


В HTML есть одно простое исключение из стандартных метаданных: теги могут быть указаны либо через `tags` метаданные, как это принято в Pelican, либо через `keywords` метаданные, как это принято в HTML. Их можно использовать как взаимозаменяемые.

Обратите внимание, что, помимо заголовка, никакие из этих метаданных контента не являются обязательными: если дата не указана и `DEFAULT_DATE` установлена ​​на `'fs'`, Pelican будет полагаться на временную метку файла «mtime», а категория может определяться по каталогу, в котором файл находится. Например, файл, расположенный по адресу, `python/foobar/myfoobar.rst` будет иметь категорию `foobar`. Если вы хотите организовать файлы другими способами, при которых имя подпапки не подходит для категории, вы можете установить для этого параметра `USE_FOLDER_AS_CATEGORY` значение `False`. При синтаксическом анализе дат, указанных в метаданных страницы, Pelican поддерживает предложенное W3C [подмножество ISO 8601](https://www.w3.org/TR/NOTE-datetime) .

Так что заголовок - единственные требуемые метаданные. Если вас это беспокоит, не волнуйтесь. Вместо того, чтобы каждый раз вручную указывать заголовок в метаданных, вы можете использовать имя файла исходного содержимого в качестве заголовка. Например, исходному файлу Markdown с именем `Publishing  via  Pelican.md` автоматически будет присвоено название Publishing via Pelican («Публикация через Pelican»). Если вы предпочитаете такое поведение, добавьте в файл настроек следующую строку:

    FILENAME_METADATA = '(?P<title>.*)'


> Заметка 
> 
> При экспериментировании с разными настройками (особенно с
> метаданными) кеширование может мешать, и изменения могут быть не
> видны. В таких случаях отключите кеширование или используйте
> переключатель командной строки. `LOAD_CONTENT_CACHE = False` or use
> the `--ignore-cache` command-line switch.


`modified` должно быть в последний раз, когда вы обновляли статью, и по умолчанию, `date` если не указано иное. Помимо того, что вы можете отображать `modified` в шаблонах, записи каналов в средствах чтения каналов будут обновляться автоматически, если вы установите `modified` текущую дату после того, как вы изменили свою статью.

`authors` список авторов статей, разделенных запятыми. Если есть только один автор, вы можете использовать `author` поле.

Если вы явно не указали сводные метаданные для данного сообщения, этот `SUMMARY_MAX_LENGTH` параметр можно использовать, чтобы указать, сколько слов из начала статьи используется в качестве резюме.

Вы также можете извлечь любые метаданные из имени файла с помощью регулярного выражения, которое будет установлено в `FILENAME_METADATA` настройке. Все сопоставленные именованные группы будут установлены в объекте метаданных. Значение по умолчанию для этого `FILENAME_METADATA` параметра будет извлекать только дату из имени файла. Например, если вы хотите извлечь и дату, и заголовок, вы можете установить что-то вроде:`'(?P<date>\d{4}-\d{2}-\d{2})_(?P<slug>.*)'`

Обратите внимание, что метаданные, доступные в ваших файлах, имеют приоритет над метаданными, извлеченными из имени файла.


## страницы[¶](https://docs.getpelican.com/en/stable/content.html#pages "Постоянная ссылка на этот заголовок")

Если вы создаете папку с именем `pages` внутри папки содержимого, все файлы в ней будут использоваться для создания статических страниц, таких как « **О нас»** или « **Контакты»** . (См. Пример макета файловой системы ниже.)

Вы можете использовать эту `DISPLAY_PAGES_ON_MENU` настройку, чтобы контролировать, все ли эти страницы отображаются в основном меню навигации. (По умолчанию `True`.)

Если вы хотите исключить ссылки на какие-либо страницы или их перечисление в меню, добавьте атрибут к его метаданным. Это полезно для таких вещей, как создание страниц ошибок, соответствующих сгенерированной теме вашего сайта. `status:  hidden`

## Статический контент[¶](https://docs.getpelican.com/en/stable/content.html#static-content "Постоянная ссылка на этот заголовок")

Статические файлы - это файлы, отличные от статей и страниц, которые копируются в выходную папку как есть, без обработки. Вы можете контролировать, какие статические файлы копируются, с помощью `STATIC_PATHS` настройки `pelicanconf.py` файла проекта . Конфигурация по умолчанию Pelican включает `images` каталог для этого, но другие должны быть добавлены вручную. Кроме того, включены статические файлы, на которые есть явные ссылки (см. Ниже).

### Смешанный контент в одном каталоге[¶](https://docs.getpelican.com/en/stable/content.html#mixed-content-in-the-same-directory "Постоянная ссылка на этот заголовок")

Начиная с Pelican 3.5, статические файлы могут безопасно делиться исходным каталогом с исходными файлами страниц, не раскрывая источники страниц на сгенерированном сайте. Любой такой каталог должен быть добавлен в оба `STATIC_PATHS` и `PAGE_PATHS` (или `STATIC_PATHS` и `ARTICLE_PATHS`). Пеликан будет идентифицировать и обрабатывать исходные файлы страниц в обычном режиме, а остальные файлы копировать, как если бы они находились в отдельном каталоге, зарезервированном для статических файлов.

Примечание. Размещение статических файлов и файлов источника контента вместе в одном исходном каталоге не гарантирует, что они окажутся в одном месте на созданном сайте. Самый простой способ сделать это - использовать `{attach}` синтаксис ссылки (описанный ниже). Кроме того `STATIC_SAVE_AS`, можно настроить параметры `PAGE_SAVE_AS`, и `ARTICLE_SAVE_AS`(и соответствующие `*_URL` параметры) для размещения файлов разных типов вместе, как это было в более ранних версиях Pelican.

## Ссылка на внутренний контент[¶](https://docs.getpelican.com/en/stable/content.html#linking-to-internal-content "Постоянная ссылка на этот заголовок")

Начиная с Pelican 3.1, теперь можно указывать внутрисайтовые ссылки на файлы в иерархии _исходного контента_ вместо файлов в _сгенерированной_ иерархии. Это упрощает ссылку из текущего сообщения на другой контент, который может находиться рядом с этим сообщением (вместо того, чтобы определять, где будет размещен другой контент после создания сайта).

Чтобы создать ссылку на внутреннее содержимое (файлы в `content` каталоге), используйте следующий синтаксис для цели ссылки: `{filename}path/to/file` Примечание: косые черты,, `/` являются обязательным разделителем пути в `{filename}` директиве во всех операционных системах, включая Windows.

Например, проект Пеликана может иметь такую ​​структуру:

    website/
    ├── content
    │   ├── category/
    │   │   └── article1.rst
    │   ├── article2.md
    │   └── pages
    │       └── about.md
    └── pelican.conf.py

    интернет сайт/ 
    ├── содержание 
    │    ├── категория / 
    │    │      └── article1.rst
    │    ├── article2.md 
    │    └── страницы 
    │           └── about.md 
    └── pelican.conf.py

В этом примере это `article1.rst` может выглядеть так:

    The first article
    #################

    :date: 2012-12-01 10:02
    
    See below intra-site link examples in reStructuredText format.

    `a link relative to the current file <{filename}../article2.md>`
    `a link relative to the content root <{filename}/article2.md>`



    Первая статья 
    ################ 

    : date: 2012-12-01 10:02 

    См. Ниже примеры внутрисайтовых ссылок в формате reStructuredText. 

    `ссылка относительно текущего файла <{filename}../ article2.md>`
    `ссылка относительно корня содержимого <{filename}/article2.md>`

и `article2.md`:

    Title: The second article
    Date: 2012-12-01 10:02

    See below intra-site link examples in Markdown format.

    [a link relative to the current file]({filename}category/article1.rst)
    [a link relative to the content root]({filename}/category/article1.rst)



    Title: Вторая статья
    Date: 2012-12-01 10:02

    См. Ниже примеры внутрисайтовых ссылок в формате Markdown.

    [ссылка относительно текущего файла]({filename}category/article1.rst)
    [ссылка относительно корня содержимого]({filename}/category/article1.rst)    
      

### Связывание со статическими файлами[¶](https://docs.getpelican.com/en/stable/content.html#linking-to-static-files "Постоянная ссылка на этот заголовок")

Вы можете ссылаться на статический контент, используя `{static}path/to/file`. Файлы, связанные с этим синтаксисом, будут автоматически скопированы в выходной каталог, даже если исходные каталоги, содержащие их, не включены в `STATIC_PATHS`  настройку `pelicanconf.py` файла проекта.

Например, каталог содержимого проекта может иметь такую ​​структуру:

    содержание 
    ├── изображения 
    │   └── han.jpg 
    ├── PDF-файлы 
    │   └── menu.pdf 
    └── страницы 
        └── test.md


    content
    ├── images
    │   └── han.jpg
    ├── pdfs
    │   └── menu.pdf
    └── pages
        └── test.md


`test.md` будет включать:

    ![Альтернативный текст]({static} /images/han.jpg) 
    [Наше меню]({static}/pdfs/menu.pdf)

Поколение сайта будет затем скопировать `han.jpg` на `output/images/han.jpg`, `menu.pdf` чтобы `output/pdfs/menu.pdf` и написать соответствующие ссылки `test.md`.

Если вы используете `{static}` ссылку на статью или страницу, она будет преобразована в ссылку на ее исходный код.


### Прикрепление статических файлов[¶](https://docs.getpelican.com/en/stable/content.html#attaching-static-files "Постоянная ссылка на этот заголовок")

Начиная с Pelican 3.5, статические файлы могут быть «прикреплены» к странице или статье, используя следующий синтаксис для цели ссылки: `{attach}path/to/file`. Это работает как `{static}` синтаксис, но также перемещает статический файл в выходной каталог связывающего документа. Если статический файл происходит из подкаталога ниже источника связывающего документа, эта связь будет сохранена на выходе. В противном случае он станет родственником связывающего документа.

Это работает только для ссылки на статические файлы.

Например, каталог содержимого проекта может иметь такую ​​структуру:

    содержание 
    ├── блог 
    │   ├── иконки 
    │   │   └── icon.png 
    │   ├── photo.jpg 
    │   └── testpost.md 
    └── загрузки 
        └── archive.zip


    content
    ├── blog
    │   ├── icons
    │   │   └── icon.png
    │   ├── photo.jpg
    │   └── testpost.md
    └── downloads
        └── archive.zip


`pelicanconf.py` будет включать:

    ДОРОЖКА  =  'content' 
    ARTICLE_PATHS  =  [ 'blog' ] 
    ARTICLE_SAVE_AS  =  '{date:% Y} / {slug} .html' 
    ARTICLE_URL  =  '{date:% Y} / {slug} .html'


    PATH = 'content'
    ARTICLE_PATHS = ['blog']
    ARTICLE_SAVE_AS = '{date:%Y}/{slug}.html'
    ARTICLE_URL = '{date:%Y}/{slug}.html'


`testpost.md` будет включать:

    Title: Test Post
    Category: test
    Date: 2014-10-31

    ![Icon]({attach}icons/icon.png)
    ![Photo]({attach}photo.jpg)
    [Downloadable File]({attach}/downloads/archive.zip)


    Название: Тестовая статья
    Category: тест 
    Date: 2014-10-31

    ![Icon]({attach}icons/icon.png) 
    ![Фото]({attach}photo.jpg)
    [Загружаемый файл]({attach}/downloads/archive.zip)


При создании сайта будет создан выходной каталог со следующей структурой:

    вывод 
    └── 2014 
        ├── archive.zip 
        ├── иконки 
        │   └── icon.png 
        ├── photo.jpg 
        └── test-post.html


    output
    └── 2014
        ├── archive.zip
        ├── icons
        │   └── icon.png
        ├── photo.jpg
        └── test-post.html


Обратите внимание, что все файлы, связанные с помощью, `{attach}` оказались в каталоге вывода статьи или ниже него.

Если статический файл связан несколько раз, функция перемещения `{attach}` будет работать только в первой из этих ссылок, которые будут обрабатываться. После первой ссылки Пеликан отнесется к `{attach}` лайку `{static}`. Это позволяет избежать разрыва уже обработанных ссылок.

**Будьте осторожны при связывании с файлом из нескольких документов:** поскольку первая ссылка на файл завершает его местоположение, а Pelican не определяет порядок, в котором обрабатываются документы, использование `{attach}` файла, связанного несколькими документами, может привести к изменению его местоположения с одного. сайт строить до следующего. (Произойдет ли это на практике, будет зависеть от операционной системы, файловой системы, версии Pelican и документов, добавляемых, изменяемых или удаляемых из проекта.) Любые внешние сайты, ссылающиеся на старое местоположение файла, могут в этом случае найти свои ссылки неработающими. **Поэтому рекомендуется использовать {attach} только в том случае, если вы используете его во всех ссылках на файл, и только если связывающие документы совместно используют один каталог.**В этих условиях выходное расположение файла не изменится в будущих сборках. В случаях, когда эти меры предосторожности невозможны, рассмотрите возможность использования `{static}` ссылок вместо `{attach}` и определения местоположения файла в соответствии с настройками проекта `STATIC_SAVE_AS` и `STATIC_URL`. (Для каждого файла `save_as` и `url` переопределения все еще можно установить `EXTRA_PATH_METADATA`.)


### Ссылки на авторов, категории, индекс и теги[¶](https://docs.getpelican.com/en/stable/content.html#linking-to-authors-categories-index-and-tags "Постоянная ссылка на этот заголовок")

Вы можете связаться с авторами, категории, индексы и теги , используя `{author}name`, `{category}foobar`, `{index}` и `{tag}tagname` синтаксис.

### Устаревший синтаксис внутренней ссылки[¶](https://docs.getpelican.com/en/stable/content.html#deprecated-internal-link-syntax "Постоянная ссылка на этот заголовок")

Чтобы оставаться совместимым с более ранними версиями, Pelican по-прежнему поддерживает вертикальные полосы ( `||` ) в дополнение к фигурным скобкам ( `{}` ) для внутренних ссылок. Например: `|filename|an_article.rst`, `|tag|tagname`, `|category|foobar`. Синтаксис был изменен с `||` на, `{}` чтобы избежать конфликтов с расширениями Markdown или директивами reST. Точно так же Pelican также поддерживает ссылки на статический контент с помощью `{filename}`. Синтаксис был изменен на, `{static}` чтобы разрешить ссылки как на сгенерированные статьи и страницы, так и на их статические источники.

Со временем поддержка старого синтаксиса может быть удалена.

### Включая другие файлы[¶](https://docs.getpelican.com/en/stable/content.html#including-other-files "Постоянная ссылка на этот заголовок")

Синтаксисы Markdown и reStructuredText предоставляют механизмы для этого.

Ниже приведены несколько примеров для **reStructuredText** с использованием [директивы include](http://docutils.sourceforge.net/docs/ref/rst/directives.html#include) :

    .. include:: main.cpp

Включите фрагмент файла, разделенный двумя идентификаторами, выделенный как C ++ (также возможна нарезка по номерам строк):

    .. include:: main.cpp
        :code: c++
        :start-after: // begin
        :end-before: // end

Включите необработанный файл HTML (или встроенный SVG) и поместите его прямо в вывод без какой-либо обработки:

    .. raw:: html
        :file: table.html

Для **Markdown** нужно полагаться на расширение. Например, используя [плагин mdx_include](https://github.com/neurobin/mdx_include) :


    ```html
    {! template.html !}
    ```

## Импорт существующего сайта[¶](https://docs.getpelican.com/en/stable/content.html#importing-an-existing-site "Постоянная ссылка на этот заголовок")

Можно импортировать свой сайт из каналов WordPress, Tumblr, Dotclear и RSS с помощью простого скрипта. См. [Импорт существующего сайта](https://docs.getpelican.com/en/stable/content.html#importer.html#import) .

## Переводы[¶](https://docs.getpelican.com/en/stable/content.html#translations "Постоянная ссылка на этот заголовок")

Есть возможность переводить статьи. Для этого вам нужно добавить `lang` метаатрибут к вашим статьям / страницам и установить `DEFAULT_LANG` настройку (по умолчанию английский [en]). С этими настройками будут перечислены только статьи с языком по умолчанию, и каждая статья будет сопровождаться списком доступных переводов для этой статьи.

> Заметка
> 
> Эта основная функция Pelican не создает дочерние сайты (например
> `example.com/de`) с переведенными шаблонами для каждого языка. Для
> такой расширенной функциональности можно использовать [плагин
> i18n_subsites](https://github.com/getpelican/pelican-plugins/tree/master/i18n_subsites).
> 

По умолчанию Pelican использует «slug» URL статьи, чтобы определить, являются ли две или более статей переводами друг друга. (Это можно изменить `ARTICLE_TRANSLATION_ID` настройкой.) Заголовок можно установить вручную в метаданных файла; если не установлен явно, Пеликан автоматически сгенерирует заголовок статьи.

Вот пример двух статей, одна на английском, а другая на французском.

Статья на английском:

    Foobar is not dead
    ##################

    :slug: foobar-is-not-dead
    :lang: en

    That's true, foobar is still alive!
    Это правда, foobar все еще жив!

Русская:

    Foobar не мертв
    ##################

    :slug: foobar-is-not-dead
    :lang: ru

    Это правда, foobar все еще жив!

И французская версия:

    Foobar n'est pas mort !
    #######################

    :slug: foobar-is-not-dead
    :lang: fr

    Oui oui, foobar est toujours vivant !


Несмотря на качество контента публикации, вы можете видеть, что единственным общим элементом этих двух статей является слаг, который здесь выступает в качестве идентификатора. Если вы не хотите явно определять заголовок таким образом, вы должны вместо этого убедиться, что переведенные заголовки статей идентичны, поскольку заголовок будет автоматически сгенерирован из заголовка статьи.

Если вы не хотите, чтобы исходная версия одной конкретной статьи определялась `DEFAULT_LANG` настройкой, используйте `translation` метаданные, чтобы указать, какие сообщения являются переводами:

    Foobar is not dead
    ##################

    :slug: foobar-is-not-dead
    :lang: en
    :translation: true

    That's true, foobar is still alive!


## Подсветка синтаксиса[¶](https://docs.getpelican.com/en/stable/content.html#syntax-highlighting "Постоянная ссылка на этот заголовок")

Pelican может предоставить цветную подсветку синтаксиса для ваших блоков кода. Для этого вы должны использовать следующие соглашения в файлах содержимого.

Для reStructuredText используйте `code-block` директиву, чтобы указать тип выделяемого кода (в этих примерах мы будем использовать `python`):

    .. code-block:: python

       print("Pelican is a static site generator.")
       print("«Пеликан - генератор статических сайтов.»")


Для Markdown, который использует [расширение CodeHilite](https://python-markdown.github.io/extensions/code_hilite/#syntax) для выделения синтаксиса, [включите](https://python-markdown.github.io/extensions/code_hilite/#syntax) идентификатор языка чуть выше блока кода, сделав отступ как для идентификатора, так и для кода:

Там являются два способа, чтобы указать на идентификатор :

        ::: python 
        print ( "Синтаксис с тройным двоеточием *не* отображает номера строк." )


Для  отображения строки цифр , использовать в пути - меньше хижину вместо из двоеточия :

        #! python 
        print ( "Синтаксис shebang без указания путей *будет* отображать номера строк." )


There are two ways to specify the identifier:

        :::python
        print("The triple-colon syntax will *not* show line numbers.")


To display line numbers, use a path-less shebang instead of colons:

        #!python
        print("The path-less shebang syntax *will* show line numbers.")


Указанный идентификатор (например `python`, `ruby`) должен быть тем, который появляется в [списке доступных лексеров](http://pygments.org/docs/lexers/).

При использовании reStructuredText в директиве code-block доступны следующие параметры:

<div class="wy-table-responsive"><table border="1" class="docutils">
<colgroup>
<col width="20%">
<col width="18%">
<col width="62%">
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head">Option</th>
<th class="head">Valid values</th>
<th class="head">Description</th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td>anchorlinenos</td>
<td>N/A</td>
<td>If present wrap line numbers in &lt;a&gt; tags.</td>
</tr>
<tr class="row-odd"><td>classprefix</td>
<td>string</td>
<td>String to prepend to token class names</td>
</tr>
<tr class="row-even"><td>hl_lines</td>
<td>numbers</td>
<td>List of lines to be highlighted, where
line numbers to highlight are separated
by a space. This is similar to
<code class="docutils literal"><span class="pre">emphasize-lines</span></code> in Sphinx, but it
does not support a range of line numbers
separated by a hyphen, or comma-separated
line numbers.</td>
</tr>
<tr class="row-odd"><td>lineanchors</td>
<td>string</td>
<td>Wrap each line in an anchor using this
string and -linenumber.</td>
</tr>
<tr class="row-even"><td>linenos</td>
<td>string</td>
<td>If present or set to “table” output line
numbers in a table, if set to
“inline” output them inline. “none” means
do not output the line numbers for this
table.</td>
</tr>
<tr class="row-odd"><td>linenospecial</td>
<td>number</td>
<td>If set every nth line will be given the
‘special’ css class.</td>
</tr>
<tr class="row-even"><td>linenostart</td>
<td>number</td>
<td>Line number for the first line.</td>
</tr>
<tr class="row-odd"><td>linenostep</td>
<td>number</td>
<td>Print every nth line number.</td>
</tr>
<tr class="row-even"><td>lineseparator</td>
<td>string</td>
<td>String to print between lines of code,
‘n’ by default.</td>
</tr>
<tr class="row-odd"><td>linespans</td>
<td>string</td>
<td>Wrap each line in a span using this and
-linenumber.</td>
</tr>
<tr class="row-even"><td>nobackground</td>
<td>N/A</td>
<td>If set do not output background color for
the wrapping element</td>
</tr>
<tr class="row-odd"><td>nowrap</td>
<td>N/A</td>
<td>If set do not wrap the tokens at all.</td>
</tr>
<tr class="row-even"><td>tagsfile</td>
<td>string</td>
<td>ctags file to use for name definitions.</td>
</tr>
<tr class="row-odd"><td>tagurlformat</td>
<td>string</td>
<td>format for the ctag links.</td>
</tr>
</tbody>
</table></div>


способ записи таблицы в Markdown

    | вариант/параметр/опция    | Допустимые значения   | Описание  |
    | - | - | - |

Как в примере выше, шаблонизатор вывел таблицу:

| вариант/параметр/опция   | Допустимые значения  | Описание  |
| - | - | - |
| `anchorlinenos`     | N / A     | Если присутствует, переносить номера строк в теги `<a>`.  |
| `classprefix`   | строка    | Строка для добавления к именам классов токенов    |
| `hl_lines` | чисел | Список выделяемых строк, где номера строк, которые необходимо выделить, разделены пробелом. Это похоже на `emphasize-lines` в Sphinx'-e, но не поддерживает диапазон номеров строк, разделенных дефисом, или номеров строк, разделенных запятыми.|
| `lineanchors` | строка | Оберните каждую строку якорем, используя эту строку и -linenumber. |
| `linenos` | строка | Если он присутствует или установлен как «таблица», выводит номера строк в таблице, если установлен как «встроенный», выводит их как строчные. «None» означает, что номера строк для этой таблицы не выводятся. |
| `linenospecial` | число | Если установлено, каждой n-й строке будет присвоен «специальный» класс css. |
| `linenostart` | число | Номер строки для первой строки. |
| `linenostep` | число | Выведите номер каждой n-й строки. |
| `lineseparator` | строка | Строка для печати между строками кода, по умолчанию «n». |
| `linespans` | строка | Оберните каждую строку отрезком, используя это и -linenumber. |
| `nobackground` | N / A | Если установлено, не выводить цвет фона для элемента упаковки |
| `Nowrap` | N / A | Если установлено, не обертывать токены. |
| `tagsfile` | строка | ctags, который будет использоваться для определений имен. |
| `tagurlformat` | строка | формат для ссылок ctag. |


## Adsmek

Обратите внимание, что в зависимости от версии в вашем модуле Pygments могут быть недоступны все эти параметры. Обратитесь к _HtmlFormatter_ части [документации Pygments](http://pygments.org/docs/formatters/) для получения более подробной информации по каждому из вариантов.

Например, следующий блок кода включает номера строк, начиная с 153, и добавляет к классам CSS Pygments префиксы _pgcss,_ чтобы сделать имена более уникальными и избежать возможных конфликтов CSS:

    .. code-block:: identifier
        :classprefix: pgcss
        :linenos: table
        :linenostart: 153

       <indented code block goes here>


    ..  код - блок ::  идентификатор 
        : префикс класса :  pgcss 
        : бельеos :  таблица 
        : белье начало :  153
        
       < здесь идет блок кода с отступом  >   


Также можно указать `PYGMENTS_RST_OPTIONS` переменную в файле настроек Pelican, чтобы включить параметры, которые будут автоматически применяться к каждому блоку кода.

Например, если вы хотите, чтобы номера строк отображались для каждого блока кода и префикса CSS, вы должны установить для этой переменной значение:

    PYGMENTS_RST_OPTIONS = {'classprefix': 'pgcss', 'linenos': 'table'}
    PYGMENTS_RST_OPTIONS  =  {'префикс класса':  'pgcss', 'белье': 'таблица'}


Если указано, настройки для отдельных блоков кода переопределят значения по умолчанию в вашем файле настроек.

## Публикация черновиков[¶](https://docs.getpelican.com/en/stable/content.html#publishing-drafts "Постоянная ссылка на этот заголовок")

Если вы хотите опубликовать статью или страницу в виде черновика (например, для просмотра друзьями перед публикацией), вы можете добавить атрибут к ее метаданным. Затем эта статья будет выведена в папку и не будет указана ни на странице индекса, ни на странице категорий или тегов.`Status:  draft` `drafts`

Если ваши статьи должны автоматически публиковаться как черновики (чтобы случайно не опубликовать статью до ее завершения), укажите статус в `DEFAULT_METADATA`:

    DEFAULT_METADATA = {
        'status': 'draft',
    }


    DEFAULT_METADATA  =  { 
        'статус': 'черновик', 
    }


Чтобы опубликовать сообщение со статусом по умолчанию `draft`, обновите метаданные сообщения, включив их .`Status:  published`
