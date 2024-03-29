# Заголовки запроса

<table><thead><tr><th width="140.33333333333331">Данные</th><th width="115">Формат</th><th>Описание</th></tr></thead><tbody><tr><td>ip *</td><td>String</td><td><p>IP пользователя. Установить значение следует в заголовке используя X-Forwarded-For.</p><p>Если интеграция происходит server-side требуется в это поле прокидывать IP исходного пользователя.</p><p><strong>Пример:</strong> <code>curl --header "X-Forwarded-For: 192.168.0.2"</code></p></td></tr><tr><td>user-agent</td><td>String</td><td><p>User-Agent может содержать название контрагента, или отсутствовать </p><p><strong>Пример:</strong> <code>curl -A "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.127 Safari/537.36"</code></p></td></tr></tbody></table>

Пример передачи всех заголовков:

{% code overflow="wrap" %}
```
curl -A "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.127 Safari/537.36" --header "X-Forwarded-For: 192.168.0.2" \"https://kraken.rambler.ru/cnt/v2/?event_type=page_view&project_id=29811&request_id=1461774198.139-396177806&top100_id=f8eb35f2-94b0-4f19-affa-9d8b9c878270&en=UTF-8&sr=640x480&cd=24-bit&\la=ru-RU&timezone=-180&url=app%3A%2F%2Frambler_mail%2Fmain_page%2Fload&eid=6210531992879190&pt=%D0%A0%D0%B0%D0%BC%D0%B1%D0%BB%D0%B5%D1%80%2F%D0%BD%D0%BE%D0%B2"
```
{% endcode %}
