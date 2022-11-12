---
id: mjho331g7uskewelt4if19u
title: CAP-theorem
desc: ''
updated: 1668258551013
created: 1668257206137
---

## CAP определение

В CAP говорится, что в распределенной системе возможно выбрать только 2 из 3-х свойств:
* C (consistency) — согласованность. Каждое чтение даст вам самую последнюю запись.
* A (availability) — доступность. Каждый узел (не упавший) всегда успешно выполняет запросы (на чтение и запись).
* P (partition tolerance) — устойчивость к распределению. Даже если между узлами нет связи, они продолжают работать независимо друг от друга.

!["CAP schema"](assets/images/data-relation-db-cap-schema.png)
___

## Недостатки теоремы

Проблемы CAP теоремы:
* Далёкие от реального мира определения
* В рамках разработки, выбор в основном лежит между CP и AP
* Множество систем — просто P
* Чистые AP и CP системы могут быть не тем, что ожидаешь

___