# Обзор данных.
Изначально данные представлены в формате резервной выгрузки, разложенной по разным папкам на сервере компании. Необходимо собрать данные из разрозненных источников, проанализировать их и сделать выводы.
**В ходе работы над проектом нам встретятся следующие таблицы:**  

1) **[orders](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/orders.rar "Ссылка на файл с данными")** (данные о заказах):  
- order_id — номер заказа  
- product_id — идентификатор товара  
- quantity — количество этого товара в заказе

2) **[order_status](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/orders_status.csv "Ссылка на файл с данными")** (данные о статусах заказов и клиентах):
- order_id — номер заказа  
- client_id — идентификатор клиента  
- status — статус заказа

3) **[products](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/products.rar "Ссылка на файл с данными")** (данные о товарах):
- id — идентификатор товара  
- name — имя товара (сначала указан бренд, через запятую модель товара)  
- price — цена единицы товара, в долларах

Каждый заказ имеет статус или подтвержденного (`confirmed`), или отмененного (`canceled`). В одном заказе может быть несколько разных товаров. Если заказ был отменен, а потом создан такой же (тем же клиентом, с теми же товарами, у того же менеджера), в базе останется запись о двух заказах с разными номерами и статусами, поскольку система не позволяет создать заказ с тем же номером. 
Соберем и предобработаем три типа датасетов: `orders.csv`, `order_status.csv`, `products.csv`.

На схеме показано, как связаны таблицы между собой:
![](https://storage.yandexcloud.net/klms-public/production/learning-content/457/4167/37264/104636/497986/er_white.png)

Внутри папки `data` находятся 2 другие папки: `orders` и `products`.

В папке `orders` папки с датами, в которые сделаны записи. В этих папках — папки с именами менеджеров по продажам. Эти папки содержат файлы `orders.csv` и `order_status.csv` (в каждой папке по одной паре файлов). Пример структуры: `data` -> `orders` -> `2024-03-01` -> `Алексей Саксофонов` -> `orders.csv` и `order_status.csv`.
![image](https://github.com/user-attachments/assets/f3f0fb4e-990e-482f-89ba-44cdaedd129d)
![image](https://github.com/user-attachments/assets/d2b81499-1694-4f96-9a8b-d94eb540792f)
![image](https://github.com/user-attachments/assets/65a75023-75c2-4be2-ab99-617cb1987990)

В папке `products` папки с категориями товаров. В этих папках файлы `products.csv` (в каждой папке по одному файлу). Пример структуры: `data` -> `products` -> `AV-процессор` -> `products.csv`.
![image](https://github.com/user-attachments/assets/de073f89-5162-4c07-af52-70542a6969c7)
![image](https://github.com/user-attachments/assets/25f19340-de88-4fc7-83f9-f4d16a6c63fb)
  
Кроме того у нас есть файл **[usd_rate.txt](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/usd_rate.txt "Ссылка на файл с данными")** с курсом доллара США на каждый день анализируемого периода (данные в формате дата,курс,валюта). 

![image](https://github.com/user-attachments/assets/9b266f3b-4bda-4c37-8731-ad11e9075b0e)

**Соберем данные со всех папок в три датафрейма:**  
1. **[df_orders](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/df_orders.csv "Ссылка на файл с данными")** — на основе датасетов `orders.csv` + добавляем колонку `manager` с именами менеджеров и колонку `date` с датами.

![image](https://github.com/user-attachments/assets/a0a1b90e-0f8b-46cd-8a83-675ca8aea0c2)
 
2. **[df_order_status](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/df_order_status.csv "Ссылка на файл с данными")** — на основе датасетов `order_status.csv`.

![image](https://github.com/user-attachments/assets/23c230c8-da56-41a8-981e-7d63fd0ebcd6)

3. **[df_products](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/blob/main/Wholesale_audio_equipment/data/df_products.csv "Ссылка на файл с данными")** — на основе датасетов `products.csv` + добавляем колонку `category` с категориями товаров.  

![image](https://github.com/user-attachments/assets/1a655abe-75f8-431a-995c-6c90721e38e9)

