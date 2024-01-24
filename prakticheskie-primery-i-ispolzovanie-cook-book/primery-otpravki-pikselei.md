# Примеры отправки пикселей

Данные о событиях в приложении можно отправлять напрямую на серверы Статистики от SberAds посредством HTTPS-запросов вида:

`https://kraken.rambler.ru/cnt/v2/?<params>`

Пример использования для сбора показов с креатива:[	](https://kraken.rambler.ru/cnt/v2/?project\_id=7727633\&event\_id=%random%\&request\_id=%random%\&counter\_type=pixel\&event\_type=base\&event\_name=page\_view)

[https://kraken.rambler.ru/cnt/v2/?project\_id='PROJECT\_ID'\&event\_id=%random%\&request\_id=%random%\&counter\_type=pixel\&event\_type=base\&event\_name=page\_view\
](https://kraken.rambler.ru/cnt/v2/?project\_id=%27PROJECT\_ID%27\&event\_id=%random%\&request\_id=%random%\&counter\_type=pixel\&event\_type=base\&event\_name=page\_view)

Пример отправки просмотра с наименьшим достаточным количеством параметров:

[https://kraken.rambler.ru/cnt/v2/?project\_id='PROJECT\_ID'\&session\_id=%random%\&event\_id=%random%\&request\_id=%random%\&counter\_type=pixel\&event\_type=base\&event\_name=page\_view ](https://kraken.rambler.ru/cnt/v2/?project\_id=%27PROJECT\_ID%27\&session\_id=%random%\&event\_id=%random%\&request\_id=%random%\&counter\_type=pixel\&event\_type=base\&event\_name=page\_view)[](https://kraken.rambler.ru/cnt/v2/?project\_id=7727633\&event\_id=%random%\&request\_id=%random%\&counter\_type=pixel\&event\_type=base\&event\_name=page\_view)
