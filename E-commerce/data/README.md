# Обзор данных.
- **olist_customers_dataset**

Таблица с уникальными идентификаторами пользователей. Состоит из 5-ти столбцов: 
  
  1) customer_id — позаказный идентификатор пользователя; 
  2) customer_unique_id — уникальный идентификатор пользователя (аналог номера паспорта);
  3) customer_zip_code_prefix — почтовый индекс пользователя;
  4) customer_city — город доставки пользователя;
  5) customer_state — штат доставки пользователя.
![image](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/assets/142053096/679aea15-cc16-43ed-b566-c1c762396e53)


- **olist_orders_dataset**

Таблица с заказами. Состоит из 8-ми столбцов:

  1) order_id — уникальный идентификатор заказа (номер чека);
  2) customer_id — позаказный идентификатор пользователя;
  3) order_status — статус заказа;
  4) order_purchase_timestamp — время создания заказа;
  5) order_approved_at — время подтверждения оплаты заказа;
  6) order_delivered_carrier_date — время передачи заказа в логистическую службу;
  7) order_delivered_customer_date — время доставки заказа;
  8) order_estimated_delivery_date — обещанная дата доставки.
   
![image](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/assets/142053096/16077f4c-af84-4bd7-8153-2301412f56b8)
![image](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/assets/142053096/ea560b59-0442-4d75-9406-fbb89063780c)

В столбце order_status находятся восемь статусов: created — создан, approved — подтверждён, invoiced — выставлен счёт, processing — в процессе сборки заказа,
shipped — отгружен со склада, delivered — доставлен пользователю, unavailable — недоступен, canceled — отменён.

- **olist_order_items_dataset**

Таблица с товарами, входящие в заказы. Состоит из 7-ми столбцов:

  1) order_id — уникальный идентификатор заказа (номер чека);
  2) order_item_id — идентификатор товара внутри одного заказа;
  3) product_id — ид товара (аналог штрихкода);
  4) seller_id — ид производителя товара;
  5) shipping_limit_date — максимальная дата доставки продавцом для передачи заказа партнеру по логистике;
  6) price — цена за единицу товара;
  7) freight_value — вес товара.

![image](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/assets/142053096/8a130351-6a8f-430a-8c85-98f60328733a)
![image](https://github.com/bdi2503/Product_Analysis_Pandas.Numpy.Seaborn/assets/142053096/81ba24bb-47a7-4f0e-a5e3-3e1f5660dd47)








