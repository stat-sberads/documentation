# Метод для передачи идентификатора авторизованного пользователя

Метод используется для передачи идентификатора авторизованного пользователя: принимает на вход идентификатор проекта с идентификатором пользователя и отправляет их в счётчик. Таким образом можно переопределить значение `user_id`, указанное в настройках счётчика при инициализации.

```
TrackerTop100.syncUserId(userId, projectId: projectId)
```

**userId** – идентификатор пользователя или nil, если человек разлогинился

**projectId** – идентификатор проекта

Для сбора статистики в разрезе пользователей необходимо присвоить пользователям уникальные идентификаторы и включать их в данные, отправляемые в счетчик. Это позволит соотносить в статистике активности в приложении с заданными пользователями.