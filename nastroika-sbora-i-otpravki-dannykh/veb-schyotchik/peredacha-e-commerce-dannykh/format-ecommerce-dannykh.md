# Формат eCommerce-данных

В общем случае eCommerce-объект характеризуется следующими полями:

| Поле            | Тип                                                                                                                                            | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ecommerce       | object                                                                                                                                         | Обязательное поле. Контейнер полей-параметров eCommerce-объекта.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| currencyCode    | string                                                                                                                                         | Трехбуквенный [код валюты по ISO 4217](https://en.wikipedia.org/wiki/ISO\_4217#Active\_codes). Если передается иная валюта, будут отправлены нулевые значения вместо валюты и суммы. Указывается в коде в качестве параметра поля ecommerce.                                                                                                                                                                                                                                                                      |
| actionType      | string                                                                                                                                         | Идентификатор действия, произведённого с набором товаров. Указывается в коде в качестве параметра поля ecommerce. Возможные значения: click – клик по товару (ссылке на товар); detail – просмотр полного описания (карточки) товара; add – добавление товара в корзину; remove – удаление товара из корзины; checkout – переход к оформлению покупки; checkout\_option – выбор пользователя на определенном этапе оформления покупки; purchase – покупка товара; refund – возврат одного или нескольких товаров. |
| actionField     | object <[actionField](format-ecommerce-dannykh.md#struktura-obekta-s-dannymi-o-deistvii-less-than-actionfield-greater-than)>​                  | Дополнительные данные, описывающие действие, произведённое с товаром или набором товаров. Данные передаются в виде объекта [actionField](format-ecommerce-dannykh.md#struktura-obekta-s-dannymi-o-deistvii-less-than-actionfield-greater-than). Поле обрабатывается только для данных о покупках (actionType=purchase). Указывается в коде в качестве параметра поля actionType.                                                                                                                                  |
| products        | array[ \<productFieldObject>](format-ecommerce-dannykh.md#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara)       | Список описаний товаров, с которыми было произведено указанное действие. Данные обязательны для событий actionType. Описание каждого из товаров представляет собой объект вида [\<productFieldObject>](format-ecommerce-dannykh.md#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara). Указывается в коде в качестве параметра поля actionType.                                                                                                                                       |
| promoActionType | string                                                                                                                                         | Идентификатор промо-действия, произведённого с набором товаров. Возможные значения: promoView, promoClick.                                                                                                                                                                                                                                                                                                                                                                                                        |
| promotions      | array [\<promoFieldObject>​](format-ecommerce-dannykh.md#struktura-obekta-less-than-promofieldobject-greater-than-s-dannymi-o-reklamnoi-akcii) | Массив данных, описывающих связанное с рекламной акцией действие promoActionType. Данные передаются в виде объекта [\<promoFieldObject>](format-ecommerce-dannykh.md#struktura-obekta-less-than-promofieldobject-greater-than-s-dannymi-o-reklamnoi-akcii). Указывается в коде в качестве параметра поля promoActionType.                                                                                                                                                                                         |

Вложенность параметров eCommerce-объекта в общем случае следующая:

```
window.dataLayer.push({
    ecommerce: {
        currencyCode: '<код валюты по ISO 4217>',
        actionType: '<actionType значения из таблицы>'- обязательное поле
        products: [<productFieldObject>, <productFieldObject>, …],
        actionField: <actionField>,
        promoActionType: <promoActionType значения из таблицы>, 
        promotions: [<promoFieldObject>, <promoFieldObject>, …]
    }
});
```

Какие именно группы полей отправлять зависит от конкретной ситуации/события.

Так, например, при отображении страницы с каталогом товаров и рекламным объявлением следует передавать `products` c перечнем показанных товаров и `promoView` в качестве `promoActionType` с данными по рекламе:

```
window.dataLayer.push({
    ecommerce: {
        ccurrencyCode: '<код валюты по ISO 4217>',
        actionType: impressions, 
        products: [<productFieldObject>, <productFieldObject>, …],
        promoActionType: promoView,
        promotions: [<параметры конкретной рекламы в формате promoFieldObject>]
    }
});
```

При клике по конкретному товару из списка результатов поиска –`click` в качестве `actionType` c данными по товару и, например, названием блока «Результаты поиска»:

```
window.dataLayer.push({
    ecommerce: {
        currencyCode: '<код валюты по ISO 4217>',
        actionType: click,
        actionField: {
             list = 'Результаты поиска'
        },
        products: [<параметры конкретного товара в формате productFieldObject>]
    }
});
```

Рекомендации по тому, какие группы полей для каких ситуаций и событий передавать, приводятся в разделе «[Рекомендации по передаче eCommerce-данных](rekomendacii-po-peredache-ecommerce-dannykh.md)».

### Структура объекта \<productFieldObject> с описанием товара: <a href="#struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara" id="struktura-obekta-less-than-productfieldobject-greater-than-s-opisaniem-tovara"></a>

| Поле     | Тип     | Описание                                                                                                                                                                              |
| -------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id       | string  | Обязательное поле. Идентификатор товара. Пример: «SKU».                                                                                                                               |
| name     | string  | Название товара. Пример: «Футболка». Поле опциональное, но рекомендуется его передавать.                                                                                              |
| list     | string  | Название блока, куда входит/ отображается товар. Пример: «Результаты поиска», «Вы недавно смотрели», «Вам также могут понравиться».                                                   |
| brand    | string  | Бренд, торговая марка, ассоциированная с товаром. Пример: «Печки-лавочки».                                                                                                            |
| category | string  | Категория, к которой относится товар. Поддерживается иерархия категорий до 5 уровней вложенности. Разделителем уровней является символ «/». Пример: «Одежда/Мужская одежда/Футболки». |
| coupon   | string  | Промокод, ассоциированный с товаром. Пример: «PARTNER\_SITE\_15».                                                                                                                     |
| position | number  | Положение товара в списке. Пример: «2».                                                                                                                                               |
| price    | number  | Итоговая стоимость единицы товара с учетом всех скидок.                                                                                                                               |
| quantity | integer | Количество единиц товара.                                                                                                                                                             |
| variant  | string  | Разновидность товара. Пример: «Красный цвет».                                                                                                                                         |

### Структура объекта \<promoFieldObject> с данными о рекламной акции: <a href="#struktura-obekta-less-than-promofieldobject-greater-than-s-dannymi-o-reklamnoi-akcii" id="struktura-obekta-less-than-promofieldobject-greater-than-s-dannymi-o-reklamnoi-akcii"></a>

| Поле     | Тип    | Описание                                                                                                     |
| -------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| id       | string | Обязательное поле. Идентификатор рекламной акции. Пример: «PROMO12».                                         |
| name     | string | Название рекламной акции. Пример: «Сезонная распродажа». Поле опциональное, но рекомендуется его передавать. |
| creative | string | Связанное с рекламной акцией объявление. Пример: «sale\_banner1».                                            |
| position | string | Позиция объявления. Пример: «slot\_2».                                                                       |

### Структура объекта с данными о действии \<actionField>: <a href="#struktura-obekta-s-dannymi-o-deistvii-less-than-actionfield-greater-than" id="struktura-obekta-s-dannymi-o-deistvii-less-than-actionfield-greater-than"></a>

| Поле        | Тип    | Описание                                                                                                                                                                                                         |
| ----------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | string | Обязательное поле. Идентификатор покупки. Пример: «TRX#54321».                                                                                                                                                   |
| coupon      | string | Промокод, ассоциированный со всей покупкой целиком.                                                                                                                                                              |
| revenue     | number | Полученный доход. Если не указан, вычисляется автоматически как сумма цен всех товаров, ассоциированных с покупкой.                                                                                              |
| affiliation | string | Магазин или филиал, в котором произошла транзакция.                                                                                                                                                              |
| tax         | number | Сумма всех налогов для данной покупки.                                                                                                                                                                           |
| shipping    | number | Стоимость доставки данной покупки.                                                                                                                                                                               |
| list        | string | Название блока, куда входят/отображаются товары из данной покупки. Примеры: «Новинки», «Результаты поиска».                                                                                                      |
| step        | number | Число, представляющее этап последовательности покупки. Передается для действий типа checkout и checkout\_option.                                                                                                 |
| option      | string | Дополнительное поле, передаваемое для действий типа checkout и checkout\_option. Предоставляет информацию о выборе пользователя на определенном этапе оформления покупки (например, о выбранном способе оплаты). |
