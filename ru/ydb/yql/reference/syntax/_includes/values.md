---
sourcePath: core/yql/reference/yql-docs-core-2/syntax/_includes/values.md
sourcePath: yql/reference/yql-docs-core-2/syntax/_includes/values.md
---

# Базовый синтаксис VALUES в YQL

## VALUES как оператор верхнего уровня

Позволяет сформировать таблицу из указанных значений. Например, данное выражение формирует таблицу из k колонок и n строк: 
``` yql
VALUES (expr_11, expr_12, ..., expr_1k),
       (expr_21, expr_22, ..., expr_2k),
       ....
       (expr_n1, expr_n2, ..., expr_nk); 

```

Это выражение полностью эквивалентно следующему:

``` yql
SELECT expr_11, expr_12, ..., expr_1k UNION ALL
SELECT expr_21, expr_22, ..., expr_2k UNION ALL
....
SELECT expr_n1, expr_n2, ..., expr_nk; 

```

**Пример:**

``` yql
VALUES (1,2), (3,4);
```


## VALUES после FROM

VALUES может использоваться и в подзапросе после FROM. В частности, эти два запроса эквивалентны:
``` yql
VALUES (1,2), (3,4);
SELECT * FROM (VALUES (1,2), (3,4));
```

Во всех примерах выше имена колонок назначаются YQL и имеют вид `column0 ... columnN`. Для того, чтобы назначить произвольные имена колонок, можно воспользоваться следующей конструкцией:
``` yql
SELECT * FROM (VALUES (1,2), (3,4)) as t(x,y);
```
В данном случае колонки получат имена `x`, `y`.