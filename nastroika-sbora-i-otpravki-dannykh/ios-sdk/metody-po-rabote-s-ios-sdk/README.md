# Методы по работе с iOS SDK

{% hint style="info" %}
**ВНИМАНИЕ!** Перед вызовом методов следует убедиться, что экземпляр счётчика создан и доступен. Данные не будут собираться, если счётчик ещё не создан, т.к. их не с чем связать.
{% endhint %}

<table><thead><tr><th>Метод (Swift)</th><th width="203">Метод (Objective-C)</th><th>Описание</th></tr></thead><tbody><tr><td><pre><code>TrackerTop100.trackPageView(className: "SCREEN_CLASS", url: "URL", title: "TITLE");
</code></pre></td><td><pre><code>[TrackerTop100 trackPageViewWithClassName: @"SCREEN_CLASS" url: @"URL" title: @"TITLE"];
</code></pre></td><td><a href="otpravka-sobytii-o-pokaze-ekrana.md">Отправка событий о показе экрана</a></td></tr><tr><td><pre><code>TrackerTop100.trackEvent(eventName: "EVENT_NAME", customVars: EVENT_DATA);
</code></pre></td><td><pre><code>[TrackerTop100 trackEventWithEventName: @"EVENT_NAME" eventValues: EVENT_DATA];
</code></pre></td><td><a href="otpravka-sobstvennykh-sobytii.md">Отправка собственных событий</a></td></tr><tr><td><pre><code><strong>Формат данных &#x3C;TrackerTop100ECommerce>
</strong></code></pre></td><td><pre><code>Формат данных &#x3C;TrackerTop100ECommerce>
</code></pre></td><td><a href="peredacha-dannykh-elektronnoi-kommercii.md">Передача eCommerce-данных</a></td></tr><tr><td><pre><code>Необходимо передать код в Activity
</code></pre></td><td><pre><code>Формат данных &#x3C;TrackerTop100ECommerce>
</code></pre></td><td><a href="peredacha-dannykh-v-web-view.md">Передача данных в web-view</a></td></tr><tr><td><pre><code>TrackerTop100.trackDeeplink(link: deeplink)
</code></pre></td><td><pre><code>[TrackerTop100 trackDeeplinkWithLink: deeplink]
</code></pre></td><td>Отправка событий о переходе по deeplink</td></tr></tbody></table>
