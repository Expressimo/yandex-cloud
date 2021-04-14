---
editable: false
---

# Метод listRecordSets
Возвращает список наборов записей в указанном каталоге.
 

 
## HTTP-запрос {#https-request}
```
GET https://dns.api.cloud.yandex.net/dns/v1/zones/{dnsZoneId}:listRecordSets
```
 
## Path-параметры {#path_params}
 
Параметр | Описание
--- | ---
dnsZoneId | Идентификатор зоны DNS для получения списка наборов записей.   Чтобы получить идентификатор зоны DNS, выполните запрос [list](/docs/dns/api-ref/DnsZone/list).  Длина строки в символах должна быть равна 20.
 
## Query-параметры {#query_params}
 
Параметр | Описание
--- | ---
pageSize | Максимальное количество результатов на странице ответа на запрос. Если количество результатов больше чем `page_size`, сервис вернет значение [nextPageToken](/docs/dns/api-ref/DnsZone/listRecordSets#responses), которое можно использовать для получения следующей страницы.  Максимальное значение — 1000.
pageToken | Токен страницы. Установите значение `page_token` равным значению поля [nextPageToken](/docs/dns/api-ref/DnsZone/listRecordSets#responses) предыдущего запроса, чтобы получить следующую страницу результатов.  Максимальная длина строки в символах — 1000.
filter | Параметры фильтрации задач в ответе.  В параметрах фильтрации указываются:  1. Имя поля. В настоящее время вы можете использовать фильтрацию только для полей `name` и `type` .  2. Оператор. Поддерживаются операторы `=` и `!=` для одиночных значений, `IN` и `NOT IN` для списков значений. 3. Значение или списки значений. Значение длиной от 3 до 63 символов, совпадающее с регулярным выражением `^[a-z][-a-z0-9]{1,61}[a-z0-9]`. Пример фильтра: `name=my-record-set`.  Максимальная длина строки в символах — 1000.
 
## Ответ {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "recordSets": [
    {
      "name": "string",
      "type": "string",
      "ttl": "string",
      "data": [
        "string"
      ]
    }
  ],
  "nextPageToken": "string"
}
```

 
Поле | Описание
--- | ---
recordSets[] | **object**<br><p>Набор записей. Подробнее см. в разделе <a href="/docs/dns/concepts/resource-record">Ресурсные записи</a>.</p> 
recordSets[].<br>name | **string**<br><p>Доменное имя.</p> <p>Длина строки в символах должна быть от 1 до 254.</p> 
recordSets[].<br>type | **string**<br><p>Тип записи.</p> <p>Длина строки в символах должна быть от 1 до 20.</p> 
recordSets[].<br>ttl | **string** (int64)<br><p>Время жизни записи в секундах.</p> <p>Допустимые значения — от 0 до 2147483647 включительно.</p> 
recordSets[].<br>data[] | **string**<br><p>Обязательное поле. Значение набора записей.</p> <p>Количество элементов должно находиться в диапазоне от 1 до 100. Длина строки в символах для каждого значения должна быть от 1 до 255.</p> 
nextPageToken | **string**<br><p>Токен для получения следующей страницы результатов в ответе. Если количество результатов больше чем <a href="/docs/dns/api-ref/DnsZone/listRecordSets#query_params">pageSize</a>, используйте `next_page_token` в качестве значения параметра <a href="/docs/dns/api-ref/DnsZone/listRecordSets#query_params">pageToken</a> в следующем запросе списка ресурсов.</p> <p>Каждая следующая страница будет иметь свой `next_page_token` для продолжения перебора страниц результатов.</p> 