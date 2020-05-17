## Специальные HTML-символы

В языке HTML существует два символа (![?](/i/q.png) только), требующих специального рассмотрения: это символы («&lt;») и («&amp;»). Левая угловая скобка используется как начало тэга; амперсанды применяются для обозначения специального символа HTML.
Для того чтобы использовать эти символы в их буквальном смысле, необходимо заменить их элементами HTML, а именно `&lt;` и `&amp;` соответственно.

При использовании Markdown подобных действий совершать не нужно. Он позволяет использовать эти символы в исходном виде. В случае если амперсанд используется как часть спецсимвола HTML, он останется неизменным. В противном случае Markdown преобразует его в `&amp;`.

{{ page.name }}

{% include f.htm f="symbols.md" %}