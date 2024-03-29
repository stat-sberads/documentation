# Активность пользователя

Названия событий передается в параметре **event\_name = ping**. Событие передается в отдельном параметре meta. Формат может быть разный: JSON, Array, String. Все данные должны быть приведены в строковый вид.&#x20;

ping – Активность пользователя

| Название   | Вложенность | Описание                                                             |
| ---------- | ----------- | -------------------------------------------------------------------- |
| activity   | mousemove   | Количество движений мышки (throttle 200мс) в течение интервала пинга |
|            | click       | Количество кликов мышки в течение интервала пинга                    |
|            | scroll      | Количество скролла мышки (throttle 200мс) в течение интервала пинга  |
|            | resize      | Количество ресайза окна в течение интервала пинга                    |
|            | keyboard    | Количество нажатий клавиатуры в течение интервала пинга              |
| scroll     | max         | Максимальная позиция скролла во время пинга                          |
|            | min         | Минимальная позиция скролла во время пинга                           |
|            | current     | Текущая позиция скролла во время пинга                               |
| doscroll   | max         | Максимальная позиция скролла во время пинга в %                      |
|            | min         | Минимальная позиция скролла во время пинга в %                       |
|            | current     | Текущая позиция скролла во время пинга в %                           |
| mdoscroll  | max         | Максимальная позиция скролла статьи во время пинга в %               |
|            | min         | Минимальная позиция скролла статьи во время пинга в %                |
|            | current     | Текущая позиция скролла статьи во время пинга в %                    |
| num        |             | Порядковый номер пинга                                               |
| duration   |             | Длительность пинга в сек                                             |
| mid        |             | Id медиа материала                                                   |
| url        |             | Url медиа материала                                                  |
| rereading  |             | Дочтение материала                                                   |

**Пример**: meta=

```
{
	"activity":{
		"mousemove":9
	},
	"scroll":{
		"max":551,
		"min":0,
		"current":0
	},
	"num":4,
	"duration":40
}
```
