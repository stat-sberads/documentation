# Метод для передачи идентификатора пользователя

### Виды идентификаторов:

| Параметр передачи                                                                                                                                              | Описание                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| <p> <a href="../parametry-schyotchika-top-100.md"><code>pub_id</code></a> </p><p> <a href="../parametry-schyotchika-top-100.md"><code>pub_scope</code></a></p> | Идентификатор пользователя, который должен быть сгенерирован и установлен площадкой –собственный идентификатор площадки |
| [`user_id`](../parametry-schyotchika-top-100.md)                                                                                                               | Идентификатор **авторизованного** пользователя                                                                          |
| `rambler_id`                                                                                                                                                   | Идентификатор RamblerId                                                                                                 |
| <p><code>sber_id</code></p><p><code>sber_id_sub</code></p>                                                                                                     | Идентификаторы SberId                                                                                                   |

### Метод для передачи идентификатора авторизованного пользователя

{% hint style="info" %}
Идентификатор **авторизованного** пользователя передается через метод [`syncUserId`](./)
{% endhint %}

Метод используется для передачи идентификатора авторизованного пользователя: принимает на вход идентификатор и отправляет его в счётчик. Таким образом можно переопределить значение [user\_id](../parametry-schyotchika-top-100.md), указанное в настройках счётчика при инициализации.

**Пример:**

```
top100Counter.syncUserId("USER_ID" || null);
```

**USER\_ID** – идентификатор пользователя или null, если человек разлогинился

#### Примеры вызова в коде страницы метода:

{% code overflow="wrap" %}
```
window.top100Counter?.syncUserId(null); // выход пользователя
window.top100Counter?.syncUserId('abcde1234'); // id авторизованного пользователя
```
{% endcode %}

Для сбора статистики в разрезе пользователей необходимо присвоить пользователям уникальные идентификаторы и включать их в данные, отправляемые в счётчик Статистики. Это позволит соотносить в Статистике активности на сайте (просмотры, клики и т.п.) с заданными пользователями.

{% hint style="info" %}
**ВНИМАНИЕ!** Если планируется использование метода [`syncUserId`](./), то обязательно в коде счётчика необходимо указать параметр [`user_id`](../parametry-schyotchika-top-100.md). Если на момент инициализации счётчика пользователь неизвестен, то в качестве [`user_id`](../parametry-schyotchika-top-100.md) нужно указать `null`. Без указания параметра [`user_id`](../parametry-schyotchika-top-100.md) при вызове [`syncUserId`](./) будет напечатано предупреждение в консоли.
{% endhint %}

#### Пример:

```
<!-- Top100 (Kraken) Counter -->
    // …
    var options = {
        // …
        user_id: <USER_ID>, || null
    };
    // …
<!-- END Top100 (Kraken) Counter -->
```

#### Передача идентификатора и аргумента null в зависимости от поведения пользователя:

* Если требуется указать, что пользователь разлогинился, надо вызвать метод [`syncUserId`](./) с аргументом `null`:

**Пример:**

```
top100Counter.syncUserId(null)
```

* Если человек пришёл незалогиненный и залогинился в процессе работы с сайтом: в атрибутах счётчика при инициализации следует указать «`user_id: null`» и далее после авторизации передать нужный идентификатор пользователя через [`syncUserId`](./).
* Если человек пришёл залогиненным, затем разлогинился и перелогинился: в атрибутах счётчика при инициализации следует указать исходный идентификатор пользователя, потом через [`syncUserId`](./) передать `null` (если это необходимо) и снова через [`syncUserId`](./) передать новый идентификатор.
* Если вы устанавливаете значение `user_id` после того, как он был `null`, то надо отправлять событие base/login `null`.
* Если вы устанавливаете `null` после того, как в `user_id` было значение, то надо отправлять событие base/logout.

### Метод для передачи остальных идентификаторов

Любой другой идентификатор передается с помощью метода [`updateOptions`](./)

**Пример:**

```
top100Counter.updateOptions({ramblerId: <USER_ID>});
```

**Пример:**

```
<!-- Top100 (Kraken) Counter -->
    // …
    var options = {
        // …
        pub_id: <PUBLISHER_USER_ID>,
        pub_scope: <SITE_DOMAIN>,
    };
    // …
<!-- END Top100 (Kraken) Counter -->
```

* Если необходимо получить идентификатор пользователя и его scope можно воспользоваться методом [`getPublisherId`](./), в котором вернутся строковые значения id и scope.

**Пример:**

```
top100Counter.getPublisherId();
```
