# Метод для обновления параметров счетчика

Метод для обновления параметром счётчика, соответствующих `projectId`. Обновляет следующие параметры: `publisherId`, `publisherScope`, `phone`, `email`.&#x20;

```
TrackerTop100.updateOptions(options)
```

&#x20;**OPTION** – объект класса `TrackerTop100Settings.Params` с обновленными параметрами

**Пример использования метода:**

```
let options = TrackerTop100Settings.Params(
    projectId: "777777",
    publisherId: "test_publisher_id",
    publisherScope: "test_publisher_scope",
    phone: "79262167879",
    email: "some@rambler.ru"
)!
TrackerTop100.updateOptions(options)
```
