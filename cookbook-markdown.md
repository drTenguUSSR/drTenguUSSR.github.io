# общая информация MarkDowm

## markDown ограничения

стили не работают (как тег <style></style>> так и атрибут тега типа
style="float: right;")
см. [полный список тегов запрещенных тегов](https://github.github.com/gfm/#disallowed-raw-html-extension-)

````text
<title>
<textarea>
<style>
<xmp>
<iframe>
<noembed>
<noframes>
<script>
<plaintext>
````

### preformatted text

в рамках preformated text не работают выделения (*)

### проблемы в HTML-таблицах

в рамках таблицы не работают выделения ни (\*) ни тегом (b)

## Markdown HTML Preview (subLime)

[Markdown HTML Preview https://github.com/zeyon/MarkdownHtmlPreview](https://github.com/zeyon/MarkdownHtmlPreview)

нажать ctrl+shift+m

особенности:

- некорректно отображает, что стили работают (на самом деле в GitHub нет)

- картинки, заданные локальными относительными путями локально не
отображаются (на GitHub проблемы нет)

## Sublime Text Markdownlint

[плугин https://github.com/jonlabelle/SublimeLinter-contrib-markdownlint](https://github.com/jonlabelle/SublimeLinter-contrib-markdownlint)

[консольный клиент https://github.com/igorshubovych/markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli)

````text
Usage: markdownlint [options] <files|directories|globs>

  MarkdownLint Command Line Interface

  Options:
    -V, --version                               output the version number
    -c, --config [configFile]                   configuration file (JSON, JSONC, JS, YAML, or TOML)
    -d, --dot                                   include files/folders with a dot (for example `.github`)
    -f, --fix                                   fix basic errors (does not work with STDIN)
    -i, --ignore [file|directory|glob]          file(s) to ignore/exclude (default: [])
    -j, --json                                  write issues in json format
    -o, --output [outputFile]                   write issues to file (no console)
    -p, --ignore-path [file]                    path to file with ignore pattern(s)
    -q, --quiet                                 do not write issues to STDOUT
    -r, --rules  [file|directory|glob|package]  include custom rule files (default: [])
    -s, --stdin                                 read from STDIN (does not work with files)
    --enable [rules...]                         Enable certain rules, e.g. --enable MD013 MD041 --
    --disable [rules...]                        Disable certain rules, e.g. --disable MD013 MD041 --
    -h, --help                                  display help for command
````

информация актуальна для (markdownlint -V) "0.39.0"
настройки правил - создать в рабочей папке .markdownlint.json
с содержимым

````json
{
  "MD013": {
       "code_block_line_length": 120
    } 
}
````

подробности [https://github.com/DavidAnson/markdownlint/blob/main/doc/md013.md](https://github.com/DavidAnson/markdownlint/blob/main/doc/md013.md)

особенности:

- через плагин не отображает подробностей ошибки. при запуске из консоли - все отображается

## Список языков, задаваемых для preformatted text через 4 гровера

markdownlint выдает ссылку на MD040/fenced-code-language

[список языков https://gitlab.com/gitlab-org/gitlab/-/issues/32881](https://gitlab.com/gitlab-org/gitlab/-/issues/32881)

````text
plaintext: When no language. Also used for output from shell commands. Replace text with this.
JavaScript: Replace js with this
html
ruby: Replace rb with this
shell: Replace bash and sh with this.
toml: Config files, like with Runner docs
ini: Simple config files, when not TOML (sometimes). Replace conf with this?
prometheus: Prometheus config
yaml: Replace yml with this
sql
asciidoc
dockerfile: Replace docker with this
erb
elixir
golang: Replace go with this
graphql
html
http
haml
json: Replace json-doc (broken) with this
markdown: Replace md with this
mermaid
nginx
python
php
perl
TypeScript: Replace ts with this.
xml
````

## Включение HTML (отключение проверки правила, его запрещающего)

[https://github.com/updownpress/markdown-lint/blob/master/rules/033-no-inline-html.md](https://github.com/updownpress/markdown-lint/blob/master/rules/033-no-inline-html.md)

````cmd
markdownlint --disable MD033 -- README.md
````

## markdown table

[https://copyprogramming.com/howto/set-table-column-width-via-markdown](https://copyprogramming.com/howto/set-table-column-width-via-markdown)

## Markdown Images

[https://github.com/xsleonard/sublime-MarkdownImages](https://github.com/xsleonard/sublime-MarkdownImages)

These can be activated with the command palette (cmd+shift+p):

````text
MarkdownImages: Hide Images
MarkdownImages: Show All Images
MarkdownImages: Show Local Images
MarkdownImages: Show Remote Images
````

## markdownlint. многоуровневые списки. ошибка MD007

проблема: если делать отступы 2 пробела на уровень, то
проверка проходит нормально, НО в визуализации отступов нет
а если делать 4 пробела - возникает ошибка

решение - в файле .markdownlint.json указать

````json
  "MD007": {
       "indent": 4
    } 
````

полезно: завести переменную среды с указанием правильного конфига
и все скрипты проверки ориентировать на неё

## Сделать якорь и ссылку на него

nb: есть автоматичеси формированные якоря для заголовков,
исходя из текста заголовка.

явное задание якоря

````markdown
## <a id="anchortext" />Header text
````

ссылка на якорь

````markdown
[text](filename.md#anchortext)
````
