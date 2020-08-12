save_as: unedtsarnd.html
summary: `*` `*` `*` `*` `*`

## [adsmek.github.io](https://adsmek.github.io/)

 + [Go to Adsmek README](https://adsmek.github.io/unedtsarnd.html)
 + [Go to Adsmek.github.io](https://github.com/Adsmek/Adsmek.github.io)

### Периодичные действия в CMD

 - В локальной папке активировать окружение Python `venv\Scripts\activate`
 - Изменить данные в страницах-файлах `*.md` папки Adsmek\`content
 - Папка со стилями `cd venv\Lib\site-packages\pelican\themes\notmyidea\static\css`
 - Обновить контент `pelican content -o Adsmek.github.io -s pelicanconf.py`


### Обновить контент:

	venv\Scripts\activate    

	pelican content
	pelican content --ignore-cache

	pelican content -o Adsmek.github.io -s pelicanconf.py
	pelican content -o Adsmek.github.io -s pelicanconf.py --ignore-cache


## Онлайн редакторы

 + [https://stackedit.io/app#](https://stackedit.io/app#) Редактор Markdown
 + [https://html-cleaner.com/](https://html-cleaner.com/) HTML-cleaner


## [GitHub Pages](https://pages.github.com/)

Клонировать новый репозиторий в папку проекта:

	git clone https://github.com/username/username.github.io


Push (нажать / толкнуть / отправить) в репозиторий

	git add --all
	git commit -m "Initial commit"
	git push -u origin master

Способ [указанный в документации](https://docs.getpelican.com/en/stable/tips.html) позволяет сохранить и отправить файлы на GitHub

	pelican content -o output -s pelicanconf.py && ghp-import output && git push origin gh-pages
___
