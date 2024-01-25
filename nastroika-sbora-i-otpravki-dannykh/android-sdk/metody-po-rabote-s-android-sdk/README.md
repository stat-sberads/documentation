# Методы по работе с Android SDK

{% hint style="info" %}
**ВНИМАНИЕ!** Перед вызовом методов следует убедиться, что экземпляр счётчика создан и доступен. Данные не будут собираться, если счётчик ещё не создан, т.к. их не с чем связать.
{% endhint %}

| Метод (Kotlin)                                                                | Метод (Java)                                                                   | Описание                                                                                                   |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| <pre><code>Kraken.enableActivityAutoTracking()
</code></pre>                  | <pre><code>Kraken.enableActivityAutoTracking();
</code></pre>                  | [Включение автоматической отправки события](vklyuchenie-otklyuchenie-avtomaticheskoi-otpravki-sobytiya.md) |
| <pre><code>Kraken.disableActivityAutoTracking()
</code></pre>                 | <pre><code>Kraken.disableActivityAutoTracking();
</code></pre>                 | [Отключение автоматической отправки данных](vklyuchenie-otklyuchenie-avtomaticheskoi-otpravki-sobytiya.md) |
| <pre><code>Kraken.trackPageView("SCREEN_CLASS", "URL", "TITLE")
</code></pre> | <pre><code>Kraken.trackPageView("SCREEN_CLASS", "URL", "TITLE");
</code></pre> | [Отправка событий об активации экрана](otpravka-sobytii-ob-aktivacii-ekrana.md) (ручная)                   |
| <pre><code>Kraken.trackEvent("EVENT_NAME", EVENT_DATA)
</code></pre>          | <pre><code>Kraken.trackEvent("EVENT_NAME", EVENT_DATA);
</code></pre>          | [Отправка собственных событий](otpravka-sobstvennykh-sobytii.md)                                           |
| <pre><code>Формат данных &#x3C;ECommerceEvent>
</code></pre>                  | <pre><code>Формат данных &#x3C;ECommerceEvent>
</code></pre>                   | [Передача eCommerce-данных](peredacha-dannykh-elektronnoi-kommercii.md)                                    |
| <pre><code>Необходимо передать код в Activity
</code></pre>                   |                                                                                | [Передача данных в web-view](peredacha-dannykh-v-web-view.md)                                              |
