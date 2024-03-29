# Рекомендации по передаче eCommerce-данных

Если у вас есть карусель с блоками, то рекомендуется присылать сообщения по следующим связанным с ней событиям:

* **impressions** – событие показа каждого блока, содержащего объект с товарами на странице,
* действие **click** – при нажатии на любой товар из этих блоков (при нажатии на «Подробнее»),
* действие **add** – при инициации покупки любого товара из этих блоков (нажатии на «Купить»).

Если у вас есть страницы со списками товаров (например, каталог товаров или новинок), то рекомендуется присылать следующие события:

* **impressions** – событие показа каждого блока, содержащего объект с товарами на странице,
* действие **click** – при нажатии на любой товар из этих блоков (при нажатии на «Подробнее»),
* действие **add** – при инициации покупки любого товара из этих блоков (нажатии на «Купить»).

Для карточки товара рекомендуется присылать следующие события:

* **impressions** – событие показа каждого блока, содержащего объект с товарами на странице,
* действие **detail** с описанием товара на карточке (здесь блок указывать не нужно),
* действие **click** – при нажатии на любой товар из этих блоков (при нажатии на «Подробнее»),
* действие **add** – при инициации покупки любого товара из этих блоков (нажатии на «Купить»).

Для корзины товаров рекомендуется присылать сообщения по следующим событиям:

* действие **add/remove** – при увеличении/уменьшении числа товаров в корзине,
* действие **checkout** – при нажатии на «Оформить заказ»,
* действие **purchase** – по факту совершения покупки.

По факту быстрого просмотра товара (нажатие не на кнопку «Подробнее» под товаром, а на само изображение товара):

* действие **detail** с описанием товара на карточке,
* действие **add** – при добавлении товара в корзину.
