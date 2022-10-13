### Ошибка трансфера при переносе представлений (VIEW) {#view}

Текст ошибки:

```text
[ERROR] "... _view": no key columns found
```

Репликация новых данных из представлений невозможна. При трансфере {{ PG }} — {{ PG }} переносятся только те представления, которые указаны в параметре эндпоинта-источника **Фильтр таблиц** → **Список включенных таблиц**.

**Решение:** вручную исключите из трансфера все представления, записав их в [параметре эндпоинта-источника](../../../../data-transfer/operations/endpoint/source/postgresql.md#additional-settings) **Фильтр таблиц** → **Список исключённых таблиц**, после чего [активируйте](../../../../data-transfer/operations/transfer.md#activate) трансфер повторно.