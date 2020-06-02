# var, let и const

**var**

- ограничена областью видимости функции
- ее значение будет undefined если вы попытаетесь обратиться к ней до ее объявления

**let**

- ограничена областью видимости блока
- вы получите ReferenceError если попытаетесь обратиться к ней до ее объявления

**const**

- ограничена областью видимости блока
- вы получите ReferenceError если попытаетесь обратиться к ней до ее объявления
- не может быть перезаписана

{% include a.htm url="https://habr.com/ru/post/438880/" text="Когда использовать var, let и const в Javascript" %}

## Keys

<button>var</button> <button>let</button> <button>const</button>