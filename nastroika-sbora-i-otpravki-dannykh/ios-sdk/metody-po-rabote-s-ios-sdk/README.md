# Методы по работе с iOS SDK

{% hint style="info" %}
**ВНИМАНИЕ!** Перед вызовом методов следует убедиться, что экземпляр счётчика создан и доступен. Данные не будут собираться, если счётчик ещё не создан, т.к. их не с чем связать.
{% endhint %}

| Метод (Swift)                                                                                                | Метод (Objective-C)                                                                                               | Описание                                                                |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| <pre><code>TrackerTop100.trackPageView(className: "SCREEN_CLASS", url: "URL", title: "TITLE");
</code></pre> | <pre><code>[TrackerTop100 trackPageViewWithClassName: @"SCREEN_CLASS" url: @"URL" title: @"TITLE"];
</code></pre> | [Отправка событий о показе экрана](otpravka-sobytii-o-pokaze-ekrana.md) |
| <pre><code>TrackerTop100.trackEvent(eventName: "EVENT_NAME", customVars: EVENT_DATA);
</code></pre>          | <pre><code>[TrackerTop100 trackEventWithEventName: @"EVENT_NAME" eventValues: EVENT_DATA];
</code></pre>          | [Отправка собственных событий](otpravka-sobstvennykh-sobytii.md)        |
| <pre><code>Формат данных &#x3C;TrackerTop100ECommerce>
</code></pre>                                         | <pre><code>Формат данных &#x3C;TrackerTop100ECommerce>
</code></pre>                                              | [Передача eCommerce-данных](peredacha-dannykh-elektronnoi-kommercii.md) |
| <pre><code>Необходимо передать код в Activity
</code></pre>                                                  |                                                                                                                   | [Передача данных в web-view](peredacha-dannykh-v-web-view.md)           |
